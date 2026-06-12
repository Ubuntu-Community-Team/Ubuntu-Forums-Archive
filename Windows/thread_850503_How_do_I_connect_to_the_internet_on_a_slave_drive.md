---
title: "How do I connect to the internet on a slave drive?"
date: 2008-07-05
forum: Windows
---

### Post by stumped on 2008-07-05
I have ubuntu installed on the primary drive and windows xp on a slave drive.
In windows (slave drive), I can not get on the internet.(no connection).
Everything works great in ubuntu.
If I go through the connection manager thing, the only choices is for dial up. I don't have dial up, so I can't connect.
How do I fix this so that I can browse the web on both drives?

---

### Post by theshadowwithanmp5n on 2008-07-05
if you have wireless, then its a problem with you windows network manager aka my network places (i think). ubuntu cannot affect windows in any way, except maybe in terms of the files. otherwise, the problem's with windows.

good luck with their customer support.

---

### Post by stumped on 2008-07-05
I do not have wireless internet.
The only reason I want windows is to play a couple games that wont work in wine. Ubuntu has been my only os for about a year now. 
I know what you mean about windows customer support.

---

### Post by mkrahmeh on 2008-07-05
windows services in general are supposed to work fine, there might be a problem with the NW adapter, try to check whether its disabled or not (in device manager), u can check the driver there too..
good luck

---

### Post by bodhi.zazen on 2008-07-05
> **stumped said:**
> I have ubuntu installed on the primary drive and windows xp on a slave drive.
In windows (slave drive), I can not get on the internet.(no connection).
Everything works great in ubuntu.
If I go through the connection manager thing, the only choices is for dial up. I don't have dial up, so I can't connect.
How do I fix this so that I can browse the web on both drives?

I do not think this issue has to do with which driver windows is installed on. I think this is a windows issue -> moved to windows forum.

---

### Post by coffeecat on 2008-07-05
Are you trying to connect to the internet through your ethernet card? If so, have you installed the Windows driver for your ethernet card yet? And what did you use to install Windows, a proper Windows install CD or one of those OEM manufacturer's image discs?

If you used a standard Windows XP install disc, you almost certainly won't have the ethernet driver installed. You have to install the driver that came on the disc with the motherboard. Failing that you'll have to use Ubuntu to find out what ethernet chipset your motherboard has, and then use Ubuntu to search the internet for a suitable Windows driver. Go Ubuntu!

---

### Post by stumped on 2008-07-05
I did install windows with a proper Windows install CD.
Yes, I am trying to connect through the ethernet card.

> **coffeecat said:**
> You have to install the driver that came on the disc with the motherboard.What exactly do you mean? I don't have any other disk. Any other time I have reinstalled windows, everything just kind of automatically worked.

I guess now I need to start searching for a driver.

---

### Post by coffeecat on 2008-07-06
> **stumped said:**
> What exactly do you mean?

Er - let me try and clarify, just to make sure we're singing from the same hymn sheet.

When I say a 'proper' Windows CD, I mean the one with the offical Microsoft logo and artwork on it. It'll also come with a product key which you type in sometime during the installation. There are two versions, retail and OEM. Retail is very expensive, but the licence allows you to install it on another machine so long as you remove it from the first one. The OEM is for system builders and is to all intents and purposes identical, but the licence allows installation on one machine only. If the machine goes down the tubes, so does the licence.

A manufacturer's image disc (or set of discs) is what comes with most big-name computers. It allows you to restore the OS to the factory setting with all the bundled software, etc that came with the machine. It will only work with the machine it is intended for. It will, of course, include all the drivers specific to that set of hardware. The fact that you've installed Windows to the slave drive suggests to me that this is not what you've got, but one of the real Windows install discs, hence your driver problem.

Now - if you built your own machine or have a machine assembled by a system builder, the motherboard *should* have come with a disc containing all the drivers you need. I recently bought a new motherboard for a new build and I installed Windows XP on it. The soundcard didn't work, ethernet didn't work, a couple of other things I can't remember now didn't work, and the display defaulted to a low-resolution vesa display. But installing all the drivers that came on the motherboard CD fixed that. So...

> **stumped said:**
> Any other time I have reinstalled windows, everything just kind of automatically worked.

would usually only happen with a manufacturer's restore image disc.

**Edit:** Actually, I believe the official CD comes with a limited set of drivers. A couple of years ago I installed XP on a machine with an Intel chipset, and iirc everything more or less just worked - as you say. The recent motherboard had a nvidia chipset, so perhaps that was why I had to install all the drivers. Whatever - I believe you need to search for the ethernet driver. If you open a terminal in Ubuntu and do 'sudo lspci' that should give you the information you need.

Good luck.

---

### Post by coffeecat on 2008-07-06
Just wanted to add...

> **coffeecat said:**
> I recently bought a new motherboard for a new build and I installed Windows XP on it. The soundcard didn't work, ethernet didn't work, a couple of other things I can't remember now didn't work, and the display defaulted to a low-resolution vesa display.

Needless to say, it 'just worked' out of the box with Ubuntu. :)

---

### Post by stumped on 2008-07-06
I found the driver I needed on the net. 
Everything works great now.
> **coffeecat said:**
> Just wanted to add...
Needless to say, it 'just worked' out of the box with Ubuntu. :)
I agree, Ubuntu works out of the box and works excellent.
Now if only all the games would work on it, I wouldn't even consider windows.

Thank you all for your help.

---

