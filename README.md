# Wifi pipe

Scan for available networks and present them (along with strength and 
security info) directly in your openbox menu. Click to connect.

### Method

This script is called once when the menu is initiated (`sudo wifi-pipe 
<interface>`); it parses the output of `iwlist <interface> scan` and 
formats the xml structure required to display the lines in your menu.

Each menu entry gets assigned a command which will recall this script 
(`sudo wifi-pipe <interface> connect <essid>`); when clicked, that 
command will do the required profile setup and network connection via 
netcfg.

You can test these commands individually in a terminal if you find 
something's not working.

### Requirements

* netcfg

For doing the actual connecting.

* zenity

For entering passwords when required.

* A `NOPASSWD` entry for this script

Since the script requires root but is called directly from the window 
manager's environment using sudo, you'll have no chance to enter a 
password.

    username ALL=(ALL) NOPASSWD: /path/to/wifi-pipe

* An entry for it in your menu.xml

An example menu.xml is included in this repo.

### Notes

I no longer use this; it may or may not work. If you actively use it and 
need something fixed or changed, please open an issue here. I'll try to 
get to it when I can -- be prepared to help me test fixes.

Also, if anyone could send me some screenshots of this in action, I'd 
love to include them in this README. I'm not motivated enough to start 
up an openbox instance to get my own :).
