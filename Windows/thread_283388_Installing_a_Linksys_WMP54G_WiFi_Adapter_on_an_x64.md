---
title: "Installing a Linksys WMP54G WiFi Adapter on an x64 Pro system"
date: 2006-10-24
forum: Windows
---

### Post by Sonic Reducer on 2006-10-24
before any instalation you need to find the cards version number. i have v4.0 with the RaLink Tech. RT2500 chip on it, this is the one that i will cover on this guide (its also the current version AFAIK)

this is a pic of the card:
[IMG]http://tinyurl.com/y2tomz[/IMG]

the first thing to do is go to [RaLink Tech's Support Website]("http://tinyurl.com/y8tv69") and download the [RT61 + RT2500 PCI / MiniPCI / CardBus Driver]("http://tinyurl.com/t2seb") (<-- click for the correct download)

save it to the desktop to make it simple

run the program (you have to install RaLink's program to get to the driver, but you have the option of using Microsoft Zero Config tool later on, which i prefer). follow the step-by-steps and reboot afterwards.

after your computer has rebooted right click on my computer and go hardware/device manager/network adapters. it will be apparent which one is the WMP because it will hav a different icon next to it (this is because the computer doesn't know WTF it is)

double click the icon and go driver /update driver

choose "not this time" for the prompt to connect to Windows Update

choose "install from a list or specific location (advanced)"

"dont search,I'll choose the driver to install"

when it askes for what category of drivers you want displayed select "show all drivers" (it should be the top option, i'm not sure thats what it says exactly though)

on the left side there are now manufacturers and on the left are their products. click in the left table and hit "r" on your keyboard, this will scroll down to the R section, RaLink should be first (don't worry if its not though, that just means another mfg. has a higher place alphabetically)

on the left select (if memory serves) "RaLink Wireless B/G Adapter" and hit ok.

that *should* do it, but if i told you the wrong driver windows will tell you, then you just repeat that sequence until you work down to the correct one; regardless, it will be the RT2500.sys or RT2500.dll driver used.

let me know if i was mistaken on any of this, or you can clarify something better than i can. i know how to do all this so i might gloss over a difficult part simply because it's not important to me to be clear to myself when i type.

hope this helps!
- ryan

---

### Post by bklebel on 2006-10-24
im confused...you don't have to do anything in linux???? my card works in windows :confused:

---

### Post by Sonic Reducer on 2006-10-24
windows x64 does not have a driver pre-installed and linksys does not have one they'll tell you about, they just say it's incompatible.

i don't know about linux though, i hope ubuntu likes it, i don't have any linux exp.

---

### Post by BorisYeltsinFBS on 2006-10-30
Perfect... Write the man in my will.

Working perfect with Windows X64!

The Driver that worked for me was the 802.11g MiniPCI Turbo Wireless Adapter.

Thanks Again!

-Mark
a.k.a. Boris Yeltsin FBS

---

### Post by Sonic Reducer on 2007-01-05
hey everybody i just updated the links a few seconds ago. both the URL's changed but AFAIK the steps are still the same, let me know if theres a problem.

---

### Post by pokemoen on 2008-09-09
My PC crashes badly when I try those drivers.
Need to start from windows install cd, go to recovery console, do fixmbr, then fixboot, then reboot to safe mode, remove the network device(s) that were added and reboot into normal mode.. 
There were a couple more reboots for me where windows just hang while loading..

Could it be that I don't have the v4 card?

Regards,
Alex

---

### Post by Erdaron on 2008-09-10
> **pokemoen said:**
> My PC crashes badly when I try those drivers.
Need to start from windows install cd, go to recovery console, do fixmbr, then fixboot, then reboot to safe mode, remove the network device(s) that were added and reboot into normal mode.. 
There were a couple more reboots for me where windows just hang while loading..

Could it be that I don't have the v4 card?

Regards,
Alex

I'm pretty sure the drivers for 4.0 and 4.1 are the same, at least the installation file. I have v4.1, and I had to use RaLink's driver on XP Pro x64.

In any case, version number is printed on the card.

If the driver is for the wrong device, it either should have complained while installing, or simply not worked, it seems.

---

