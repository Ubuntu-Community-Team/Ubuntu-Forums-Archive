---
title: "Wireless adapter suggestion"
date: 2005-12-08
forum: The Cafe
---

### Post by NeoChaosX on 2005-12-08
Okay, I need a recommendation from you guys.

I'm looking for a new wireless adapter to replace my D-Link DWL-G122 USB adapter. Though it worked fine, it's rather shoddily made (the plastic casing kept falling apart quite a number of times), and it stopped working last week. I own a Dell Inspiron 5100, and all of Dell's offerings for my laptop are Broadcom-based, which means no native Linux drivers. So I'm looking for an adapter that has a chipset with native Linux drivers, and is rather study in design. Is there anything like that out there?

---

### Post by majikstreet on 2005-12-08
USB? I dunno about laptops...  I can tell you a good PCI card, but that wouldn't help with a laptop.. If you are comfortable with ndiswrapper, have a look at this bigass list of cards known to work/not work with ndiswrapper: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

-m

edit: I haven't had good experience with USB cards working on my desktops in linux... I have a dell truemobile 1180 or 1184 (one is the router and one is the card, and I get them mixed up), but that is now being used on my tivo and since we had two, the other one is on my grandparents' tivo. I also have a Netgear MA111 which doesn't work with linux either.
So stay away from dell truemobile products and netgear ma111's....

---

### Post by ssam on 2005-12-08
have a look at [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

if you want to do some research look up if the chipset manufacturer has supported the open source driver effort (like ralink rt2x00 drivers [http://rt2x00.serialmonkey.com/wiki/index.php/History](http://rt2x00.serialmonkey.com/wiki/index.php/History) )

---

