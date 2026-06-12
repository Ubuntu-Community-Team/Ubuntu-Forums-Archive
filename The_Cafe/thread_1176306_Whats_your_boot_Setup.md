---
title: "Whats your boot Setup?"
date: 2009-06-02
forum: The Cafe
---

### Post by Ravernomina on 2009-06-02
Well My boot setup Is a Tri-boot ;)

**_My Operating Systems_**

-Mac OS X x86 10.5.7 kalyway

-Ubuntu 9.04

-Dell recovery utility :P
[B][U]
Boot Loader:[/U][/B]
GRUB

Please share your setups ;)

---

### Post by MichaelSammels on 2009-06-02
Well, mine is simple:

**_My Operating Systems:**_

-Ubuntu 9.04 "Jaunty Jackalope"

**_Boot Loader:**_
GRUB

---

### Post by Screwdriver0815 on 2009-06-02
on Desktop: Kubuntu 9.04 "Jaunty Jackalope"

Bootmanager: Grub

on Laptop: Mandriva 2009.1 "Spring"

Bootmanager (you won't believe it!): Grub

:D

---

### Post by billgoldberg on 2009-06-02
9.04 and Win7, bootloader Lilo. 

Lol, no it's Grub.

---

### Post by kk0sse54 on 2009-06-02
**_Operating Systems_**
FreeBSD
Arch Linux
NetBSD
OpenSolaris
Windows XP

**_Bootloader_**
Heavily chainloaded grub

---

### Post by ssam on 2009-06-02
about 5 linux distros.

the mbr grub reads a menu.list on one partition that looks like this

```

default saved
timeout 5
#sda1 is grub

title	sda2 Ubuntu
root	(hd0,1)
chainloader +1
savedefault

title   sda3 Ubuntu test
root    (hd0,2)
chainloader +1
savedefault

#sda4 is extended
#sda5 is swap

title   sda10 - Fedora
root    (hd0,9)
chainloader +1
savedefault

...

```

then when even i install a distro i tell the installed to install to the partition. that way it can keep its own grub up to date.

---

### Post by EnGorDiaz on 2009-06-02
freebsd 7.1
debian 5.0

---

### Post by binbash on 2009-06-02
Only Ubuntu Karmic

But soon Ubuntu Karmic + Win7 since i want to play some games

---

### Post by The Real Dave on 2009-06-02
**_Operating Systems_**
Ubuntu 9.04 Jaunty
Ubuntu 8.04 Hardy
Windows XP Home SP3
Puppy Linux 4.2

**_Bootloader_**
Grub 

Gotta say, I love GRUB :D Its been able to boot any OS I've used. Also got me out of a sticky situation when I wiped Vista's bootloader by installing XP on a friends laptop :S With no Vista disc close to hand I might add. Luckily, I had an Ubuntu Hardy Live USB :D

---

### Post by Ravernomina on 2009-06-03
Yea grub is amazing :) on a old computer one type me and a friend multi-booted over 30 diffrent Linux distros and OS's. Grub did it all With no problem God Grub is ulmighty

---

