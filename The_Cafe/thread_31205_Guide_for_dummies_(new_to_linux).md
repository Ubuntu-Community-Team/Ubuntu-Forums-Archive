---
title: "Guide for dummies (new to linux)"
date: 2005-05-02
forum: The Cafe
---

### Post by ampiee on 2005-05-02
I got hold of Ubuntu and looked at the live cd on windows and liked what i saw.
I invested in a new P4 with 512MB and tried to install UBUNTU. when it starts up it gives a message that x Windows can not start due to graphics driver and then goes to command prompt. I do not know ho to install driver from Gigabyte main board CD. Somebody told me to use root but it tells me root is disabled. Can i enable root??   :-|

---

### Post by Juergen on 2005-05-02
A detailed hardware-description would help - and copy/paste of the output of X11 trying to start

After login try
```
sudo /usr/bin/X11/xorgconfig
```(in Warty that would be xf86config AFAIR. You don't like to give much info it seems...)

If you can't find your graphics-card, try '0-generic Vesa compatible'

> 
I do not know ho to install driver from Gigabyte main board CDWindows drivers won't help you anything.

> Can i enable root?You don't need to.
If someone tells you 'change to (or login as) root, and type "blah"'
you just type 'sudo blah', it will then ask for your user-password again (and remembers it some minutes, so it will only ask sometimes) and execute blah.

---

### Post by WildTangent on 2005-05-02
if its integrated graphics than you might need to buy a cheap AGP or PCI-E card. check Gigabytes website to see if they have any information on linux compatibility

-Wild

---

### Post by poofyhairguy on 2005-05-02
[QUOTE=ampiee]I got hold of Ubuntu and looked at the live cd on windows and liked what i saw.
I invested in a new P4 with 512MB and tried to install UBUNTU. when it starts up it gives a message that x Windows can not start due to graphics driver and then goes to command prompt. I do not know ho to install driver from Gigabyte main board CD. Somebody told me to use root but it tells me root is disabled. Can i enable root??   :-|[/QUOTE]


Two things: First of all make sure you burn the Ubuntu ISO at low speeds. I've had a few install CDs f**k up on my like that because I  burned them at high speeds. Couldn't boot into X on those either.

Second of all, make sure the BIOS on your motherboard is up to date. One day I spent a LONG time trying to make a laptop work only to find out that the BIOS needed an upgrade (then it worked fine).

---

### Post by ampiee on 2005-05-03
Juergen thanks for your information. I tried sudo /usr/bin/xf86confic and chose 0 -generic Vesa, I also tried ATI radeon but still get message "I cannot start your X server (your graphical interface) It is likely that it is not set up correctly"

here is a detailed Hardware description. 
Gigabyte Socket 478 Integrated Main Board (GA-8TRS350MT)
with integrated ATI Radeon 350 VGA (ATI 9100 IGP PRO)
Intel P4 2.8 GHZ with 512MB DDR400
40Gb Seagate 7200 HDD etc.

I have an original UBUNTU CD Distributed By Canonical (Intel x86 Edition)

---

### Post by kleeman on 2005-05-03
I assume that your live-cd was fine for X windows. If so boot into the live-cd and print the file /etc/X11/*.conf (* is xorg for hoary and XFree86 something for warty). Then compare this working version with the one installed and modify appropriately.

---

### Post by ampiee on 2005-05-03
Live CD used on my old Win98 PC! Trying to install on NEW PC with SPECS as mentioned previously - Thanks

---

