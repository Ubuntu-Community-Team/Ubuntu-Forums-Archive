---
title: "Anyone have 7.10 running on a Power Edge 2600? Need help!"
date: 2008-02-22
forum: Server Platforms
---

### Post by supacool on 2008-02-22
So I downloaded Ubuntu on my laptop as a replacement for windows vista :o and absolutely fell in love with it :-D I have successfully left windows and have migrated to Ubuntu.

So that got me thinking, I run 4 dell poweredge 2600's out of my home office, lets see what I can do with a linux server. So I took my least powerful "test" server. It's got dual "dual core" 2.2 Ghz Xeon processors, 3 36 Gig scsi drives in a raid 5 and 2 18 gig scsi drives in a raid 0. Also has 4gb ram.

I installed Ubuntu server on it, and the install appeared to go smoothly. However on boot, I get the following messages, which I am guessing are not normal. 

Starting up...
Loading, please wait...
[  123.972791] i2o: iop0: Get status timeout.
[  153.921492] i20: iop0: IOP reset timeout
[  153.921548] i2o: iop0: could not activate controller
[  183.870199] i2o: iop0: IOP reset timeout
               Check root= bootarg cat /proc/cmdline
               or missing modules, devices: cat /proc/modules Ls /dev
ALERT! /dev/disk/by-uuid/7b4b3587-fa5f-4013-a68c-43b001826ec8 does not exist. Dropping to a shell!

Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter "help" for a list of built-in commands.

(initramfs) _

Now, I decipher that to mean that I does not have a raid controller and cannot mount the disks, but I am new to linux. I am an MCSE in windows, but that does not help me here. Is there a manual way to install a driver, or am I up a creek?

Thanks in advance for your help, you guys are an awesome community!

---

### Post by syale on 2008-02-22
I have a Dell PowerEdge 2300/500 and did a firmware upgrade on the raid controller. The upgrade changed my disk emulation mode to I2O and I had a similar error message. This is how I corrected it:

At boot select Ctrl M when prompted to enter raid configuration
From Management menu select Objects
From Objects menu select Adapter
From Adapter menu change the Emulation from I2O to Mass Storage.

This fixed it for me

HTH
Stephen

---

### Post by supacool on 2008-02-22
Your awesome! That appears to have worked like a charm.

Thanks for your help!

---

### Post by syale on 2008-02-22
:-) Thanks for the thanks...

This is how I found out. It is a little confusing as it should work either way:

[http://support.dell.com/support/edocs/storage/RAID/66JVW/BIOS_Utl.htm#Objects_Menu]("http://support.dell.com/support/edocs/storage/RAID/66JVW/BIOS_Utl.htm#Objects_Menu")

Menu Options
The Objects/Adapter menu options are:

Table 4. Objects\Adapter Menu Items

Emulation

You can operate in the I2O mode or mass storage mode. If you operate in mass storage mode, you need the Dell drivers. If you operate in the I2O mode, you can use either the Dell drivers or the drivers for your operating system, such as Windows NT, Novell, or UNIX. 

I run the 2300 at home also with the same raid config.

Stephen

---

### Post by vyekkirala on 2008-05-07
> **supacool said:**
> So that got me thinking, I run 4 dell poweredge 2600's out of my home office, lets see what I can do with a linux server. So I took my least powerful "test" server. It's got dual "dual core" 2.2 Ghz Xeon processors, 3 36 Gig scsi drives in a raid 5 and 2 18 gig scsi drives in a raid 0. Also has 4gb ram.


Just curious, did PowerEdge 2600's ever ship with "dual-core" processors? I thought they supported just dual single-core CPUs. Thanks.

---

### Post by 330T on 2008-06-13
I've never seen a dual core powerEdge 2600, it runs the Intel E7501 chipset.

---

