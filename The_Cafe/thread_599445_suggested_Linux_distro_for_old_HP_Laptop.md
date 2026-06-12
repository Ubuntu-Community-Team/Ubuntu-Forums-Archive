---
title: "suggested Linux distro for old HP Laptop"
date: 2007-11-01
forum: The Cafe
---

### Post by MemoryDump on 2007-11-01
I have a very old HP laptop which I'm trying to setup for my sister. It's an old clunker and has I think 32MB of ram and currently is running Win98SE.
I'd LOVE to be able to put Ubuntu on there but I'm sure it's not even worth the effort. My sister bought a compatible (supposively) wireless card for it and would love to use it for when she's on the road for basic things.

Are there any other Linux distros somebody could recommend which would support an older laptop like this and support the wireless card?
This laptop only has a floppy drive and another ethernet wired card for it. (no usb or cdrom)

thanks :D

-MD

---

### Post by -grubby on 2007-11-01
no CD-ROM drive?!? What happened to it? No USB even!! I don't know any Linux distros that are non-specific that would boot from anything except a flash drive or CDROM drive

---

### Post by jouka on 2007-11-01
So then you should do a network installation. I suggest xubuntu, even though I haven't tried it by myself yet.
I installed ubuntu into one computer which had 49 ram. :P It worked a bit sluggish way but never the less was doing it's job: play music, browse net, run skype and irc.

---

### Post by popch on 2007-11-01
There are some distros which also boot from a floppy (diskette) drive and install themselves over the network from an ISO residing on an NFS, FTP or conceivably even an SMB server. 

Installing without a CD or USB would be no problem as long as there is a driver for the NIC.

The only distro which I know to support such an installation, however, is SuSe which I think would be worse than useless on a machine with those specifications. I have no doubt that there are others, but I do not know them.

---

### Post by MemoryDump on 2007-11-01
> **nathangrubb said:**
> no CD-ROM drive?!? What happened to it? No USB even!! I don't know any Linux distros that are non-specific that would boot from anything except a flash drive or CDROM drive

when I was given this laptop many years ago the cdrom wasn't included :(   It does support one.. just not worth the cost to get a replacement.. probably cheaper to buy a new laptop now! :lolflag:

---

### Post by MemoryDump on 2007-11-01
> **popch said:**
> There are some distros which also boot from a floppy (diskette) drive and install themselves over the network from an ISO residing on an NFS, FTP or conceivably even an SMB server. 

Installing without a CD or USB would be no problem as long as there is a driver for the NIC.

The only distro which I know to support such an installation, however, is SuSe which I think would be worse than useless on a machine with those specifications. I have no doubt that there are others, but I do not know them.

yeah.. I need a good simple/stable distro which would enable me to start the installation process off a floppy then continue using the NIC card it has. I believe old RedHat distros used to work in that fashion many years ago.

---

### Post by zach12 on 2007-11-01
Have a look at damn small Linux it will work on your computer and is based on Debian like Ubuntu

ther is a net boot floppy for dsl and debian just google it

---

### Post by igknighted on 2007-11-01
I would recommend Debian for that system.  Or a net install of Fluxbuntu.  But stay really light, even Xfce is probably too much for that.  Openbox, Fluxbox or my fav, IceWM, are likely your best bets.

---

### Post by n3tfury on 2007-11-01
hold on a second.  you're setting this up for your sister?  fluxbuntu she might get along with, but forget the suggestions of dsl and similar, unless she's fairly saavy.

---

### Post by lisc998 on 2007-11-01
> **zach12 said:**
> Have a look at damn small Linux it will work on your computer and is based on Debian like Ubuntu

ther is a net boot floppy for dsl and debian just google it

dsl-n is more usable.
[http://www.damnsmalllinux.org/dsl-n/](http://www.damnsmalllinux.org/dsl-n/)
Also look at Puppy
[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by mysticrider92 on 2007-11-01
> **popch said:**
> There are some distros which also boot from a floppy (diskette) drive and install themselves over the network from an ISO residing on an NFS, FTP or conceivably even an SMB server. 

Installing without a CD or USB would be no problem as long as there is a driver for the NIC.

The only distro which I know to support such an installation, however, is SuSe which I think would be worse than useless on a machine with those specifications. I have no doubt that there are others, but I do not know them.

Debian can be installed this way, which I would recommend for this computer. There is plenty of documentation, and a section of these forums you can go to if you need help. 

Just do a very minimal install, then install Xorg and whatever wm you want (IceWM, Fluxbox, Openbox, or E17 are probably best for a computer like this).

---

### Post by Christmas on 2007-11-01
I wouldn't go with either Ubuntu/Xubuntu on 32 MB RAM. Try a network installation from a Debian 3.1 CD, it worked for me on Pentium 166MHz with 64 RAM. Better yet, Damn Small Linux will surely work. I don't know if it can be installed through a network though.

---

### Post by logos34 on 2007-11-01
If all else fails try DeLi Linux...it's got the lowest sys reqs i've ever seen for a gui desktop:
[http://www.delilinux.org/wiki/doku.php?id=devel:installdisks](http://www.delilinux.org/wiki/doku.php?id=devel:installdisks)
(-->boot floppies to start network install)

[http://www.delilinux.org/](http://www.delilinux.org/)
[http://www.delilinux.org/wiki/doku.php?id=software:deli-32](http://www.delilinux.org/wiki/doku.php?id=software:deli-32)

---

### Post by MemoryDump on 2007-11-01
I'm currently making the floppy boot disks for Debian and I'll see how well it installs over the network. Thanks all for the great suggestions. I will post here once I hopefully get something going on this old clunker :P

I also downloaded to boot img for delilinux.. it looks pretty sharp too :D

---

### Post by 900donuts on 2007-11-01
whats the name of the laptop model because chances are I'm trying to do the exact same thing (creepy)

mines an omnibook 800ct with 166mhz pentium, 32mb of ram, no cd no internal floppy, no usb, ect...

p.s. i was lucky enough to find a dock for $3 in the surplus store's "as is" bin

---

