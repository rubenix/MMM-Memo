# MMM-Memo
Memo Module for MagicMirror<sup>2</sup>

This an extension for the [MagicMirror²](https://magicmirror.builders/).
This Module is used to add many memo notes on your Magic Mirror.
<br>Content is manageable through HTTP get requests.

## What does it look like
![alt tag](https://github.com/schnibel/MMM-Memo/blob/master/MMM-Memo.png)

## Dependencies
  * An installation of [MagicMirror<sup>2</sup>](https://github.com/MichMich/MagicMirror)

## Installation

In your terminal, go to your MagicMirror's Module folder:
````
cd ~/MagicMirror/modules
````

Clone this repository:
````
git clone https://github.com/schnibel/MMM-Memo.git
````

## Using the module

To use this module, add it to the modules array in the `config/config.js` file:
````javascript
modules: [
    {
        module: 'MMM-Memo',
        position: 'top_left',
        classes: 'default everyone',        // if using MMM-ProfileSwitcher module
        config: {
            // See 'Configuration options' for more information.
            ...
        }
    }
]
````
If you declare several modules in the `config/config.js` file, you will get several memo notes on your MagicMirror<sup>2</sup> profile.

## Configuration options

The following properties can be configured:

| Option                     | Description
| -------------------------- | -----------
| `memoTitle`                | [MANDATORY]<br>Title of the memo note.<br>This title is also used to retreive memos from the persistence file.<br><br> **This is NOT case sensitive**
| `memoMaxItems`             | [OPTIONAL]<br>Integer used to define the maximum number of memo to display per note.<br>If the number of memos is greater than the one specified here, a message (e.g. `+ 2 more memos`) will be displayed at the bottom of the note.<br><br> **Default value:** `5`
| `memoMaxMsgSize`           | [OPTIONAL]<br>Integer used to define the maximum number of characters to be displayed per memo.<br><br> **Default value:** `false` (It will show all characters)
| `memoDisplayDuration`      | [OPTIONAL]<br>Used to show since when memos have been created.<br><br> **Possible values:** `true` or `false`<br> **Default value:** `false`
| `memoDisplayIfEmpty`       | [OPTIONAL]<br>Used to display (or not) an empty note if there is no memo inside.<br><br> **Possible values:** `true` or `false`<br> **Default value:** `false`
| `memoDisplayId`            | [OPTIONAL]<br>Used to display (or not) a number before each memo. This number is necessary to remove a memo.<br><br>** Note that this unicode character is limited to 20 **<br><br> **Possible values:** `true` or `false`<br> **Default value:** `true`
| `memoDisplayHeader`        | [OPTIONAL]<br>Used to display (or not) the memoTitle at the top of the note.<br><br> **Possible values:** `true` or `false`<br> **Default value:** `true`
| `memoColorBackground`      | [OPTIONAL]<br>Used to define the color of the note.<br><br> **Possible values:** See [Colors](#colors) for more information.<br> **Default value:** `Yellow`
| `memoColorHeader`          | [OPTIONAL]<br>Used to define the color of the header (if displayed).<br><br> **Possible values:** See [Colors](#colors) for more information.<br> **Default value:** `Black`
| `memoColorFont`            | [OPTIONAL]<br>Used to define the color of the memo font.<br><br> **Possible values:** See [Colors](#colors) for more information.<br> **Default value:** `Black`
| `memoColorWarning`         | [OPTIONAL]<br>Used to define the color of a WARNING note.<br><br> **Possible values:** See [Colors](#colors) for more information.<br> **Default value:** `Red`
| `memoRotation`             | [OPTIONAL]<br>Used to rotate the note.<br><br> **Possible values:** `-10` or `-8` or `-6` or `-4` or `-2` or `0` or `2` or `4` or `6` or `8` or `10`<br> **Default value:** `0`
| `memoWidth`                | [OPTIONAL]<br>Value to specify the width of the note.<br><br> **Default value:** `100px`
| `memoHeight`               | [OPTIONAL]<br>Value to specify the height of the note.<br><br> **Default value:** `100px`
| `memoPadding`              | [OPTIONAL]<br>Value to specify the padding of the note.<br><br> **Default value:** `20px`
| `format`                   | [OPTIONAL]<br>Displays relative date format, for absolute date format provide a string like `'DD:MM HH:mm'` [All Options](http://momentjs.com/docs/#/displaying/format/)



## How to Use

I'm using this module with my Jarvis installation from [DomotiqueFacile](http://domotiquefacile.fr/jarvis/).
<br>When I speak to Jarvis, I say for example : "add FRUITS to the SHOPPING memo list", and Jarvis automatically sends a HTTP get request to the MMM-Memo module.
<br><br>The available HTTP get requests are the following at the moment:

### To add `Fruits` to the `Shopping` memo note:
````
http://MIRROR_IP:MIRROR_PORT/AddMemo?memoTitle=SHOPPING&item=Fruits&level=INFO
````

### To add `Daddy: +33123456789` to the `Phone Numbers` memo note with a WARNING level:
````
http://MIRROR_IP:MIRROR_PORT/AddMemo?memoTitle=phone%20numbers&item=Daddy%3A%20%2B33123456789&level=WARNING
````

### To remove the second displayed memo of the `Phone Numbers` memo note:
````
http://MIRROR_IP:MIRROR_PORT/RemoveMemo?memoTitle=phone%20numbers&item=2
````

### To remove ALL memos of the `Phone Numbers` memo note:
````
http://MIRROR_IP:MIRROR_PORT/RemoveMemo?memoTitle=phone%20numbers&item=ALL
````

### To temporary display the second memo of the `Shopping` memo note. It will be useful for cut memos:
This HTTP request is <b>NOT YET IMPLEMENTED</b>
````
http://MIRROR_IP:MIRROR_PORT/DisplayMemo?memoTitle=SHOPPING&item=2
````

### To temporary display ALL memos of the `Shopping` memo note. It will be useful when a note does not display all memos:
This HTTP request is <b>NOT YET IMPLEMENTED</b>
````
http://MIRROR_IP:MIRROR_PORT/DisplayMemo?memoTitle=SHOPPING&item=ALL
````


## Colors
Here are the available colors.
<table width="100%">
	<thead>
		<tr>
			<th>Color Name</th>
			<th width="100%">Color</th>
		</tr>
	<thead>
	<tbody>
        <tr><td>Snow</td><td style="background: #fffafa;"></td></tr>
        <tr><td>Snow2</td><td style="background: #eee9e9;"></td></tr>
        <tr><td>Snow3</td><td style="background: #cdc9c9;"></td></tr>
        <tr><td>Snow4</td><td style="background: #8b8989;"></td></tr>
        <tr><td>GhostWhite</td><td style="background: #f8f8ff;"></td></tr>
        <tr><td>WhiteSmoke</td><td style="background: #f5f5f5;"></td></tr>
        <tr><td>Gainsboro</td><td style="background: #dccdc;"></td></tr>
        <tr><td>FloralWhite</td><td style="background: #fffaf0;"></td></tr>
        <tr><td>OldLace</td><td style="background: #fdf5e6;"></td></tr>
        <tr><td>Linen</td><td style="background: #faf0e6;"></td></tr>
        <tr><td>AntiqueWhite</td><td style="background: #faebd7;"></td></tr>
        <tr><td>AntiqueWhite2</td><td style="background: #eedfcc;"></td></tr>
        <tr><td>AntiqueWhite3</td><td style="background: #cdc0b0;"></td></tr>
        <tr><td>AntiqueWhite4</td><td style="background: #8b8378;"></td></tr>
        <tr><td>PapayaWhip</td><td style="background: #ffefd5;"></td></tr>
        <tr><td>BlanchedAlmond</td><td style="background: #ffebcd;"></td></tr>
        <tr><td>Bisque</td><td style="background: #ffe4c4;"></td></tr>
        <tr><td>Bisque2</td><td style="background: #eed5b7;"></td></tr>
        <tr><td>Bisque3</td><td style="background: #cdb79e;"></td></tr>
        <tr><td>Bisque4</td><td style="background: #8b7d6b;"></td></tr>
        <tr><td>PeachPuff</td><td style="background: #ffdab9;"></td></tr>
        <tr><td>PeachPuff2</td><td style="background: #eecbad;"></td></tr>
        <tr><td>PeachPuff3</td><td style="background: #cdaf95;"></td></tr>
        <tr><td>PeachPuff4</td><td style="background: #8b7765;"></td></tr>
        <tr><td>NavajoWhite</td><td style="background: #ffdead;"></td></tr>
        <tr><td>Moccasin</td><td style="background: #ffe4b5;"></td></tr>
        <tr><td>Cornsilk</td><td style="background: #fff8dc;"></td></tr>
        <tr><td>Cornsilk2</td><td style="background: #eee8dc;"></td></tr>
        <tr><td>Cornsilk3</td><td style="background: #cdc8b1;"></td></tr>
        <tr><td>Cornsilk4</td><td style="background: #8b8878;"></td></tr>
        <tr><td>Ivory</td><td style="background: #fffff0;"></td></tr>
        <tr><td>Ivory2</td><td style="background: #eeeee0;"></td></tr>
        <tr><td>Ivory3</td><td style="background: #cdcdc1;"></td></tr>
        <tr><td>Ivory4</td><td style="background: #8b8b83;"></td></tr>
        <tr><td>LemonChiffon</td><td style="background: #fffacd;"></td></tr>
        <tr><td>Seashell</td><td style="background: #fff5ee;"></td></tr>
        <tr><td>Seashell2</td><td style="background: #eee5de;"></td></tr>
        <tr><td>Seashell3</td><td style="background: #cdc5bf;"></td></tr>
        <tr><td>Seashell4</td><td style="background: #8b8682;"></td></tr>
        <tr><td>Honeydew</td><td style="background: #f0fff0;"></td></tr>
        <tr><td>Honeydew2</td><td style="background: #e0eee0;"></td></tr>
        <tr><td>Honeydew3</td><td style="background: #c1cdc1;"></td></tr>
        <tr><td>Honeydew4</td><td style="background: #838b83;"></td></tr>
        <tr><td>MintCream</td><td style="background: #f5fffa;"></td></tr>
        <tr><td>Azure</td><td style="background: #f0ffff;"></td></tr>
        <tr><td>AliceBlue</td><td style="background: #f0f8ff;"></td></tr>
        <tr><td>Lavender</td><td style="background: #e6e6fa;"></td></tr>
        <tr><td>LavenderBlush</td><td style="background: #fff0f5;"></td></tr>
        <tr><td>MistyRose</td><td style="background: #ffe4e1;"></td></tr>
        <tr><td>White</td><td style="background: #ffffff;"></td></tr>


        <tr><td>Snow</td><td style="background: #fffafa;"></td><td></td>
<td>Snow2</td><td style="background: #eee9e9;"></td><td></td>
<td>Snow3</td><td style="background: #cdc9c9;"></td><td></td>
<td>Snow4</td><td style="background: #8b8989;"></td><td></td></tr>
        <tr><td>GhostWhite</td><td style="background: #f8f8ff;"></td><td></td>
<td>WhiteSmoke</td><td style="background: #f5f5f5;"></td><td></td>
<td>Gainsboro</td><td style="background: #dccdc;"></td><td></td>
<td>FloralWhite</td><td style="background: #fffaf0;"></td><td></td></tr>
        <tr><td>OldLace</td><td style="background: #fdf5e6;"></td><td></td>
<td>Linen</td><td style="background: #faf0e6;"></td><td></td>
<td>AntiqueWhite</td><td style="background: #faebd7;"></td><td></td>
<td>AntiqueWhite2</td><td style="background: #eedfcc;"></td><td></td></tr>
        <tr><td>AntiqueWhite3</td><td style="background: #cdc0b0;"></td><td></td>
<td>AntiqueWhite4</td><td style="background: #8b8378;"></td><td></td>
<td>PapayaWhip</td><td style="background: #ffefd5;"></td><td></td>
<td>BlanchedAlmond</td><td style="background: #ffebcd;"></td><td></td></tr>
        <tr><td>Bisque</td><td style="background: #ffe4c4;"></td><td></td>
<td>Bisque2</td><td style="background: #eed5b7;"></td><td></td>
<td>Bisque3</td><td style="background: #cdb79e;"></td><td></td>
<td>Bisque4</td><td style="background: #8b7d6b;"></td><td></td></tr>
        <tr><td>PeachPuff</td><td style="background: #ffdab9;"></td><td></td>
<td>PeachPuff2</td><td style="background: #eecbad;"></td><td></td>
<td>PeachPuff3</td><td style="background: #cdaf95;"></td><td></td>
<td>PeachPuff4</td><td style="background: #8b7765;"></td><td></td></tr>
        <tr><td>NavajoWhite</td><td style="background: #ffdead;"></td><td></td>
<td>Moccasin</td><td style="background: #ffe4b5;"></td><td></td>
<td>Cornsilk</td><td style="background: #fff8dc;"></td><td></td>
<td>Cornsilk2</td><td style="background: #eee8dc;"></td><td></td></tr>
        <tr><td>Cornsilk3</td><td style="background: #cdc8b1;"></td><td></td>
<td>Cornsilk4</td><td style="background: #8b8878;"></td><td></td>
<td>Ivory</td><td style="background: #fffff0;"></td><td></td>
<td>Ivory2</td><td style="background: #eeeee0;"></td><td></td></tr>
        <tr><td>Ivory3</td><td style="background: #cdcdc1;"></td><td></td>
<td>Ivory4</td><td style="background: #8b8b83;"></td><td></td>
<td>LemonChiffon</td><td style="background: #fffacd;"></td><td></td>
<td>Seashell</td><td style="background: #fff5ee;"></td><td></td></tr>
        <tr><td>Seashell2</td><td style="background: #eee5de;"></td><td></td>
<td>Seashell3</td><td style="background: #cdc5bf;"></td><td></td>
<td>Seashell4</td><td style="background: #8b8682;"></td><td></td>
<td>Honeydew</td><td style="background: #f0fff0;"></td><td></td></tr>
        <tr><td>Honeydew2</td><td style="background: #e0eee0;"></td><td></td>
<td>Honeydew3</td><td style="background: #c1cdc1;"></td><td></td>
<td>Honeydew4</td><td style="background: #838b83;"></td><td></td>
<td>MintCream</td><td style="background: #f5fffa;"></td><td></td></tr>
        <tr><td>Azure</td><td style="background: #f0ffff;"></td><td></td>
<td>AliceBlue</td><td style="background: #f0f8ff;"></td><td></td>
<td>Lavender</td><td style="background: #e6e6fa;"></td><td></td>
<td>LavenderBlush</td><td style="background: #fff0f5;"></td><td></td></tr>
        <tr><td>MistyRose</td><td style="background: #ffe4e1;"></td><td></td>
<td>White</td><td style="background: #ffffff;"></td><td></td>
<td></td><td></td><td></td>
<td></td><td></td><td></td></tr>





    </tbody>
</table>



## Special thanks
I implemented colors from [Taylored Marketing](http://www.tayloredmktg.com/rgb/#PI) for color definitions, so I thank the author of this web page.
<br>I got the memo note CSS from [Creative Punch](http://creative-punch.net/2014/02/create-css3-post-it-note/), so I also wanted to thank Creative Punch.
<br><br>Enjoy... and do not hesitate to make comments or propose new functionalities.