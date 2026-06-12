---
title: "Cobalt Raq 550 + Ubuntu Server"
date: 2010-02-16
forum: Server Platforms
---

### Post by donk64 on 2010-02-16
It looks like the last threads on this topic were from 2006, and all of them now have dead external links.  I have a working Cobalt 550 (Pentium 3 1GHz, 1GB Ram, Dual 80GB RAID) basically sitting under my bed that I hate to see go to waste.  I would love to get it up and running with Ubuntu.

The problem with the Cobalt Raqs was they don't use a standard BIOS, but rather, a special firmware that relies on a special build of the Linux 2.2 kernel.

I am aware of the Strongbolt product, I've actually upgraded with that in the past, but overall it seems really out of date and not well maintained.

So, I guess my question is, has anyone had any luck getting modern i686 Ubuntu/Debian booting and working on the Raq 550?  It'd be great if there was a way hack the bootloader to just switch over to grub on the internal hard disk, but I don't know of anyone who has successfully done this.

If not, any ideas on what I can use it for in its current state?  I hate to waste good hardware. :-k

---

### Post by GreenDance on 2010-03-28
> **donk64 said:**
> It looks like the last threads on this topic were from 2006, and all of them now have dead external links.  I have a working Cobalt 550 (Pentium 3 1GHz, 1GB Ram, Dual 80GB RAID) basically sitting under my bed that I hate to see go to waste.  I would love to get it up and running with Ubuntu.

The problem with the Cobalt Raqs was they don't use a standard BIOS, but rather, a special firmware that relies on a special build of the Linux 2.2 kernel.

I am aware of the Strongbolt product, I've actually upgraded with that in the past, but overall it seems really out of date and not well maintained.

So, I guess my question is, has anyone had any luck getting modern i686 Ubuntu/Debian booting and working on the Raq 550?  It'd be great if there was a way hack the bootloader to just switch over to grub on the internal hard disk, but I don't know of anyone who has successfully done this.

If not, any ideas on what I can use it for in its current state?  I hate to waste good hardware. :-k

Hi, I've been working on it, but it's a royal pain, tried for 2 month to do it and bricked both my other RAQ550's because of a failed kernel upgrade.

I tried strongbolt on my other RAQ550, the kernel upgrade failed and to bricked that unit, strongbolt support are no help, they've left loads of people in the lurch, they'll take your money for their custom (out of date now) iso, but when problems arise their no where to be found.

I've since bought a P4 M/B from ebay with CPU n Ram, loaded Ubuntu onto a spare HDD nice cheap server.

I recommend keeping the original OS on your RAQ, as least it will "still work".

---

### Post by donk64 on 2010-04-01
Yeah, I wish I could easily revert to the original firmware and OS image.

Did you put the new P4 MB inside of the cobalt case?  It'd be nice to find something that would fit inside of the existing case and line up with ports/power supply/hds and maybe even LEDs

---

### Post by GreenDance on 2010-04-03
> **donk64 said:**
> Yeah, I wish I could easily revert to the original firmware and OS image.

Did you put the new P4 MB inside of the cobalt case?  It'd be nice to find something that would fit inside of the existing case and line up with ports/power supply/hds and maybe even LEDs

It would of been nice, but the cobalt case is custom built to their custom built motherboard, so it's impossible to use the case for modern day motherboards

---

### Post by trevor67 on 2010-11-20
I'm using strongbolt on my Raq4 no problem, I am also able to clean install original os software.  I have also tried Centos 4xx no problems there either.  Better results can be had with MIPS based Cobalt Raq3 servers with people using Debian.  I am aware or an Ubuntu how to for Raq4 server, have not tried that one though.

---

### Post by trevor67 on 2011-02-03
Maybe this how to could be an option, [http://www.mr-webcam.com/viewtopic.php?f=19&t=23](http://www.mr-webcam.com/viewtopic.php?f=19&t=23)

---

### Post by snoozer70 on 2011-02-20
hi,

just as an fyi, i have debian lenny and now also debian squeeze on 2 RaQ550 installed. the actual installation is ages ago for lenny and i just recently upgraded to squeeze. i remember i had installed debian on a physical harddisk which i moved from the installation system to the actual RaQ550. there is another way via NFS similar to the installation procedure on a RaQ 1 (mips). here a link i found very helpful:

[http://wiki.defcon.no/guides/raq/raq4-lenny](http://wiki.defcon.no/guides/raq/raq4-lenny)

there is a link to the ROM update for 2.4 kernel and ext3 etc....

at the bottom of that page is a link to kernel patches up to 2.6.32, unfortunately that seems to be the latest kernel i can use. the configuration of the kernel was rather tricky. i am stil not sure exactly which options are needed to make it work but attached a config that worked for me on a RaQ550. with the patched 2.6.32 kernel, the attached config and the debian package 'cobalt-panel-utils' i got it all to work. 

For the LCD to make it work you have to issue:
```
mknod /dev/lcd c 10 156
```after that 'lcd-write' etc. should work.

i just imagine it may be not so different with ubuntu if you can build a working kernel.

the only thing is did not get to work yet is the 'Web' LED and the 'Maintenance' LED. if anyone can point me in the right direction for that i would be very happy !!

Have Fun!
Jan

---

