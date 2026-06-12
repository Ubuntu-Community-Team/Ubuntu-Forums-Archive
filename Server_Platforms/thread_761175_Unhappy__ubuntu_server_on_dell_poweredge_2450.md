---
title: "Unhappy  ubuntu server on dell poweredge 2450"
date: 2008-04-20
forum: Server Platforms
---

### Post by liathus on 2008-04-20
I was told to repost this here, i posted it under installation first


Hello, I am trying to install Ubuntu Server 8 RC on a dell poweredge 2450. Everything went fine during the install, ubuntu detected and let me install on my hardware raid volume. However, after the installation completed, and upon reboot, i am faced with some nasty errors. Im not sure why the server install cd could detect and mount the volume properly but it doesnt work after reboot. I have listed errors below.

Please note, that i was intending to move our production servers (also using dell raid) to ubuntu from gentoo, but that isnt gonna happen if i cant get this fixed, plese help so I dont have to waste years of my life waiting for source to compile anymore


e.g.

aacraid: Host adapter abort requesr. SCSI hang?

and after a bunch of those i get

check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/(inser my uuid here) does not exist. Dropping to a shell!

---

### Post by ikonia on 2008-04-21
I think you've got an unusual and tricky situation here.

the aacraid is famously bad. It's VERY fussy against firmware on version changes.

eg: 2.6.10 may work with firmware 1.0.0 but 2.6.12 will require 1.0.2 firmware

the first thing I'd do is boot from cd - check the firmware on the card and if possible take it to the latest revision, that is the most common cause of issues I've had with this card.

Second check the adaptec website for release notes on the driver versions, some of the older versions of THEIR driver needed specific boot options in specific cases, it's certainly worth checking what options are availble to you 

Third, check the modules/versions/boot lines of the livecd, booting and seeing an unconfigured disk is different from actually using one at boot time.

What point do you get this error, is it beyond using initrd ? as thats the last thing I'd have a poke at.


---- edit ------

just as an interesting point, boot the livecd and see if a blkid on the raid device shows up, the error you posted is also complaining about the device id not being available, check it out on the livecd and see if it does have a blkid generated for it.

---

### Post by liathus on 2008-04-21
As an update, i tried installing ubuntu server 6.06, and it has worked flawlessly.  So its just ubuntu 7, and 8 that do not work.  Both version 7 and version 8 see the drives, but fail after the reboot stage of the install.

I will check into the firmware and such on the backplane, however i do find it rather odd it works on 6 but not 7 or 8.  I thought about what you said with the kernel version and firmware, however even after doing a kernel update on server 6 it still worked.

---

### Post by ikonia on 2008-04-22
you updated the kernel on 6.06 to be the same as say 7.10 or 8.04 ?

---

### Post by liathus on 2008-04-22
im not sure exactly what kernel, but it is the latest kernel 6.06 server installed using apt-get.  Im out of town for the day, when i get back tonight I will check the exact kernel version its running now.

---

