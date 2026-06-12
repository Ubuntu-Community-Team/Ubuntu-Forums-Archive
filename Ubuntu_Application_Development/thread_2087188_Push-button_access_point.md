---
title: "Push-button access point"
date: 2012-11-23
forum: Ubuntu Application Development
---

### Post by afeder on 2012-11-23
Hi. The Ubuntu repositories contain a wonderful piece of software called [FONT="Courier New"][[COLOR="Blue"]hostapd[/COLOR]]("http://packages.ubuntu.com/search?keywords=hostapd")[/FONT]. With this package, I've been able to set up a 802.11 access point (infrastructure mode) on my laptop, enabling me to share my internet connection to handheld devices like my phone.

The problem is that running hostapd as such requires a bit of command-line dirty work and, furthermore, I currently need to start it manually in a terminal every time I log in for it to work.

I would like to make, instead, a service which loads up at boot time with minimal user input required.

The procedure for setting up hostapd in this mode I found here: _[http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/](http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/)_

The dependencies for this procedure are:
[LIST]
[*][FONT="Courier New"][COLOR="Blue"]hostapd[/COLOR][/FONT]
[*][FONT="Courier New"][COLOR="Blue"]dhcp3-server[/COLOR][/FONT]
[/LIST]
I need to create two different scripts or programs:
[LIST=1]
[*]A 'setup' or 'installation' script which creates the appropriate hostapd and dhcpd .conf files, and
[*]A 'boot' or 'service' script which starts dhcpd and hostapd at boot time.
[/LIST]
I intend to make both of these scripts in a high-level language like Python. Will that work :?:

Also, where should I place the 'boot' script for it to be executed at load time :?:

And finally, how do I make a package which lists [FONT="Courier New"][COLOR="Blue"]hostapd[/COLOR][/FONT] and [FONT="Courier New"][COLOR="Blue"]dhcp3-server[/COLOR][/FONT] as its dependencies *and* runs the 'setup' script when it is installed :?:

Thanks [IMG]http://i266.photobucket.com/albums/ii269/theogrit/1sm084thumbsup.gif[/IMG]

---

