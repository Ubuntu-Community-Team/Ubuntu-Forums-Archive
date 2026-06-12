---
title: "SSH login failure: connection refused"
date: 2010-12-15
forum: Server Platforms
---

### Post by rufinus on 2010-12-15
**OS:** Ubuntu Server 10.10 x64 standard install over network
**Main application:** NAS, sharing over Samba 2x 1TB HDD configured as RAID 1; 
**Extra packages installed:** Webmin,Samba, ProFTPD, MC, OpenSSH (running headless)
**Hardware:** MSI Wind Nettop 3325VHP - Atom 330

    * Prozessor: 1 x Intel Atom 330 ( Dual-Core )
    * RAM: 2 GB (installed) DDR2 SDRAM - 533 MHz
    * 1x500 GB-SATA-300**-->replaced by Seagate 1TB HDD**
    * DVD±RW (±R DL)/DVD-RAM**-->replaced by Seagate 1TB HDD**
    * Card reader: 4-in-1
    * Intel GMA 950 Dynamic Video Memory Technology 3.0
    * Network - Gigabit Ethernet, Realteck

-------------------------------------------------------------
**First  try:** installed 10.04 LTS on SD card, formatted as EXT4 with swap (default install).  Functioned ok on the beginning, failed after about two weeks with filesystem errors.  After repair on the next boot again threw some errors , went read-only..  Lessons learned about max write cycles. Also hdparm configuration had a bug.  Was easier  to install new then to restore.

**Second try:** installed 10.10 x64 over network to usb flash drive, formatted as EXT3, but with noatime option; swap partition present, but swappiness is set to 0.

**Current issues:** systems runs ok for about two days, sharing over router to one PC and one MAC. Then suddenly share disappears, trying to SSH from PC or MAC gives “Connection refused” error. Webmin reports: “Error, file not found!” However, it is still possible to ping the server! After reboot, server hangs somewhere along boot process. After second reboot, everything functions fine again!
Somehow getting disappointed in server-oriented-reliable-linux..
Don’t know even where to start to look for a problem. Any ideas?

---

### Post by CharlesA on 2010-12-15
Try logging it to the console and see what's going on.

Are you using using a static IP, or getting one from DHCP?

---

### Post by rufinus on 2010-12-15
I use DHCP, but with reservation list for MAC addresses. So that all home 3 PCs always get same IP address and for any guest PC IP is assigned by DHCP randomly in the range.

What do you mean with logging it to the console? I currently run headless, with administration over PuTTY (SSH) or Webmin.

---

### Post by CharlesA on 2010-12-15
If you can't get in via SSH, you'd have to hook a monitor and keyboard up to see what is going on.

Might want to check dmesg for errors.

Since the machine is hanging after a reboot, and needs a second reboot to get it working, that's probably a good place to start.

---

### Post by rufinus on 2010-12-15
> **CharlesA said:**
> If you can't get in via SSH, you'd have to hook a monitor and keyboard up to see what is going on.

Might want to check dmesg for errors.

Since the machine is hanging after a reboot, and needs a second reboot to get it working, that's probably a good place to start.

Well, and that is the problem a little, carrying keyboard and monitor around all the time.. As i have only one set, which is connected to other PC. But anyway, will have to do it on next failure.

I spent an evening yesterday "grepping" /var/log/* for usefull linfo, regarding SSH and SSHD, but found nothing strange.
It must be some global login problem, if all connections are refused (samba, webmin, ssh). Biggest problem is that currently i dont know where tto start now, for what to look (keyword) in logs..

---

### Post by CharlesA on 2010-12-15
Start with dmesg.

It kinda sounds like networking stops working, but you can ping the box, so I don't know what's going on with it.

---

### Post by rufinus on 2010-12-15
Ok, thanks so far, will report when more info available.

---

### Post by rufinus on 2011-01-14
After 4  weeks time "run" time here is the update.

Crashes continue to happen, but on the radom basis. Can be a day, can be a week. 
After connecting once the monitor, following was displayed:

Unable to enumerate USB device...

And then a messages about filesystem errors (unable to write).

dmesg only shows filesystem scans and errors from consequental reboots (as the filesystem was not unmounted properly). 
It does look like usb drive is getting disconnected due to some reason, and then the system is unable to wtite to it anymore. Therefore nothing regarding this issue or error trigger in the logs.
Connecting USB keyboard does not help as well, it's just not detected (no standart port for keyboard available).

This all points to USB support problem, i think. 
What should be my next steps?

---

### Post by chrislynch8 on 2011-01-14
What is the usbdrive for?

---

### Post by CharlesA on 2011-01-14
Given that you installed to a thumb drive, and dmesg mentions problems with USB, I'd suggest putting a small hard drive in there and seeing if the problems reoccur.

That would rule out the USB drive.

---

### Post by chrislynch8 on 2011-01-14
Misread the first post. So you have Ubuntu installed on the USB Drive. How big is the USB Drive?

---

### Post by rufinus on 2011-01-14
> **chrislynch8 said:**
> What is the usbdrive for?

System is installed to USB drive. There are internal 2 SATA interfaces, 2 HDD's in software RAID are connected to those. For more detail see my 1-st post.

---

### Post by rufinus on 2011-01-14
---

---

### Post by rufinus on 2011-01-14
----

---

### Post by rufinus on 2011-01-14
USB drive is 4GB, brand new SanDisk. Befo it was installed to SD card, but it failed and i blamed the card first, thats why i went to USB drive. 

Both new card and flash drive just cant be defective. There is something with USB support.

---

### Post by airtonix on 2011-01-15
no usb flash drives are just too unreliable as a filesystem for something that does lots of writes.

My 32gb hdd from my old 5g ipod is ticking along nicely as both a sub device or via a sata/zif adaptor

---

### Post by rufinus on 2011-01-15
> **airtonix said:**
> no usb flash drives are just too unreliable as a filesystem for something that does lots of writes.

My 32gb hdd from my old 5g ipod is ticking along nicely as both a sub device or via a sata/zif adaptor

Well, i wouldn't like to go now into a discussion abot flash drives reiability, there is planty info in internet and it is clearly states, that they should run for some years, not days! If properly confgured, of course. In my case it runs with noatime option and small swap with swappiness set to zero, so what exccessive writes are you talking about? 

Problem here is the UBS interface getting kicked out, not with the driv itself! Looks like it's a kernel problem..

---

### Post by CharlesA on 2011-01-15
If it was a kernel problem, more people would be having problems with it.

You could try filing a bug over on launchpad, but I doubt it'll get much attention.

---

### Post by rufinus on 2011-01-15
> **CharlesA said:**
> If it was a kernel problem, more people would be having problems with it.

You could try filing a bug over on launchpad, but I doubt it'll get much attention.

Indeed: [http://ubuntuforums.org/showthread.php?t=1214003&highlight=unable+enumerate](http://ubuntuforums.org/showthread.php?t=1214003&highlight=unable+enumerate)

Post number 2 in particular.

---

