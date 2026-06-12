---
title: "Wireless/selecting other network interfaces"
date: 2008-05-02
forum: Server Platforms
---

### Post by Alien Collective on 2008-05-02
Okay, I've run a web server on Ubuntu for a year or so now, but it amazes me that I haven't bungled anything up yet. I subscribe to the "mess around until it works" school of learning, which isn't always incredibly rewarding when working from the command line.

Anyway, I'm now in the process of setting up a Ubuntu server (8.04) with an old computer I happened to have sitting around, just as a testing server for my web stuff. Everything is working fine now, but it's connected via ethernet, and my router isn't in the most convenient spot, so I'd like to get it using the wireless card instead. During installation I was given the option of which interface to use, but since I knew the ethernet would work I picked that in the interim.


So now my question is twofold (and potentially threefold):

How do I know if it has the necessary drivers? If it doesn't, how can I install them? I've searched the forum, but most of the stuff that came up was gibberish to me. I came across (and ran) this command, which does list my wireless card:

```

mikkel@montesquieu:~$ lspci | grep -i "network\|ethernet"
00:07.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:0a.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

```

Searching for the model number, I came up with _[a driver](http://linuxwireless.org/en/users/Drivers/b43)_, but I don't know if I need it or how to install it if I do. The installation instructions on the site seem to be taking some knowledge for granted.

Once the card is set up, how do I configure it as the default network interface and to connect to my (naturally passworded) wireless network?


I'm sorry, this is rather a lot to ask. I can answer most problems with Google, and I definitely came up with some things that looked helpful this time, but most of it went over my head. If anyone has any help to offer or could point me in the right direction, I'd be much obliged. :)

---

### Post by andguent on 2008-05-03
Wireless is known to be the last frontier (at least as far as I'm concerned :)). I've seen significant improvements in getting Broadcom wireless to work in recent releases, as my laptop has a broadcom 4318.

There are many wireless howto's for broadcom on these forums. Admittedly though, most are for the desktop/gui install. 

I would say the quickest ways to get this setup are like this:
* Install GUI, and walk through the GUI install howtos. The restricted driver manager will get half of the fwcutter junk working for you. I hate saying this because I love keeping my server headless. It may actually be quicker though based on past experiences.
* Buy a Linksys WRT54GL (needs the L on the end), download dd-wrt, upload to Linksys via "Firmware update" page, wait 5 minutes, restart Linksys, log in, set as wireless client/bridge, plug server into lan side of router, done.

---

### Post by Alien Collective on 2008-05-03
It's embarrassing that I didn't come across these before, but I've got the driver installed from [these instructions](http://ubuntuforums.org/showthread.php?t=766560) and configured using [this](http://ubuntuforums.org/showthread.php?t=684495). The configuration didn't go as planned, but I'm suspecting it might be a hardware problem (the card's antenna is missing). I'm done for the time being after having to lie on my stomach reconfiguring the server so it'd accept my SSH connection over ethernet again, but if I come back to it I'll start a new thread over on the networking board where this should've been to start with (sorry, didn't notice that one).

Thanks for the suggestions.

---

