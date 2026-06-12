---
title: "Compatability"
date: 2005-07-10
forum: The Cafe
---

### Post by harryfear on 2005-07-10
Surely one of the disadvantages of a user moving from Windows to Linux is that lots of their hardware won't be compatible?

I'm new to Linux and would love to know how people overcome this problem - if they do/can?

Thanks  :)

---

### Post by Knome_fan on 2005-07-10
Don't worry too much, most of your hardware should work out of the box. Of course there might be problems, but if you run into troubles just ask here and with a bit of luck you'll be able to solve them.

P.S.: A very good way to test compatability is to download and try the LiveCD.

---

### Post by darkmatter on 2005-07-10
Compatability is on par with Windows in most cases, better in some.
Example: My hardware has some issues with Windows, and requires additional drivers for the chipset, etc. It's also a pain in the backside to an extent, as Windows stubbornly attempts to use it's own drivers (resulting in having to force the issue). In Linux (most cases), the hardware is supported out of box, only rarely have I had to modprobe to get something working.

As mentioned in the post before mine, get some live CD's (Knoppix, Slax, Ubuntu, etc.), and see which flavor works best on your box.

---

### Post by RastaMahata on 2005-07-10
windows doesnt autodetect my nforce2 chipset (ethernet, audio). Ubuntu does, but the audio has to be fixed (just copy pasting a file, nothing else).

---

### Post by poofyhairguy on 2005-07-10
[QUOTE=harryfear]Surely one of the disadvantages of a user moving from Windows to Linux is that lots of their hardware won't be compatible?[/QUOTE]

True. The worst offenders in my experiance are:

1. Newer Wireless cards (you can nerdily force it to work though)

2. Good 3D drivers (only Nvidia)

3. Some DSL modems and Winmodems

4. Webcams (kiss um goodby)

5. Some TV Cards

6. Laptop ACPI suspend for many (not mine)

7. Some serial ATA cards.

8. Some PDAs are a biotch to sync with

There might be others I have missed. But in every example there is some hardware that does work.

> I'm new to Linux and would love to know how people overcome this problem - if they do/can?

My favorite way:

Sell the uncompatible crap on ebay and use the money to support companies that make Linux drivers. I've traded a wireless card and video card that way. You lose a little- I call that the price of Linux.

---

### Post by AgenT on 2005-07-10
And usually if something does not work it can easily be replaced for not much money instead of having the hasstle of trying to get it to work. Best example are sound cards. Most work but there are a few that were made by horrible companies who used specifications that made Linux compatibility impossible. But that is not a big deal because one can buy a pretty descent sound card that works perfectly in Linux for around $15-20US.

Two types of hardware that are most prone of not working and being expensive to replace are printers and scanners. Most work, but there are a lot that don't.

For printers, check [www.linuxprinting.org]("http://www.linuxprinting.org") and look up your printer to see what it says. If not listed, check this forum because it may be new and not yet listed on the website.

For scanners, check out [http://www.sane-project.org]("http://www.sane-project.org/").

Just realize that a lot of companies are really nasty in letting anyone have any specifications which makes Linux compatibility difficult on programmers. It is actually amazing at the work that has been accomplished by Linux users in making a lot of hardware compatible without any help from the companies that make the hardware.

---

### Post by aysiu on 2005-07-10
Just wanted to chime in that it's not a given that hardware won't be compatible. On my eMachines computer, Ubuntu recognized everything but my monitor's best screen resolution. That was an easy fix--add two lines to /etc/X11/xorg.conf.

---

### Post by somuchfortheafter on 2005-07-10
everything works on my toshiba notebook but the sd card reader slot.....

---

### Post by zeroK on 2005-07-10
The only hardware I completely haven't got working so far are cheaper Minolta printers since they offer no postscript support and only GDI. 

Another story is my TV card which basically work but I simply haven't found the right options yet ;)

---

