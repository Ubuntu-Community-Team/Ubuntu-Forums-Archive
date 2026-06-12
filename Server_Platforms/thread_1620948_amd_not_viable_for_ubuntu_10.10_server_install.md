---
title: "amd not viable for ubuntu 10.10 server install?"
date: 2010-11-13
forum: Server Platforms
---

### Post by miga on 2010-11-13
Hi

been trying to get a spare computer up and running with 10.10 server 64bit

no dice so far, after hours of memchecks, disk checksums, re-burns and whatnot..

install stops at 73% and does f. all.. tail log shows that it stops at updating sources, alt+f2 and ps aux shows apt-get update process running.

if I kill this process, I can continue with the installation, but for this I need to repeat same process - killing all the apt instances that show up - so that it can complete the install.  
Unacceptable imho.

computer is a AMD cpu based, athlon 2 435 on an ASUS M4A89TD PRO mainboard. ddr3 4gb crucial ram sticks.

drives are functional S-ATA.  No external GPU, so using IGP.

Tried installing without eth-cable plugged in, with it plugged in, with a usb install (that sorry excuse for an install was even worse, "please insert cd" midway ......)

Soo.. I know I can get the install going with desktop version.. But why would I want an xserver running on a headless computer.

Kind of pissed atm, spent so many hours at this, figuring it just might be a faulty HW item.  It isn't.

using 10.10 desktop on my laptop and production pc - and been using 8.04 as main server, until now...

Edit:  another one of them optiarc sony nec **** for brains dvd/cd-rom/writer it seems..   Please add a check for this in future releases, with big bold letters "YOU ARE SCREWED, BUY NEW HARDWARE" printed as soon as the cd loads in these drives.. I've got better things to spend my time on than staring at a screen trying to figure out why it won't load properly

time for a new distro, perhaps..

---

### Post by gdahlm on 2010-11-13
If you have an issue with the particular DVD drive you may want to try installing via a USB flash drive if the system supports boot from USB.

---

### Post by miga on 2010-11-15
> **gdahlm said:**
> If you have an issue with the particular DVD drive you may want to try installing via a USB flash drive if the system supports boot from USB.

"
Tried installing without eth-cable plugged in, with it plugged in, **with a usb install **(that sorry excuse for an install was even worse, "please insert cd" midway ......)
"

Anyhoot, gave up trying. Giving debian a go instead, via net-install

---

