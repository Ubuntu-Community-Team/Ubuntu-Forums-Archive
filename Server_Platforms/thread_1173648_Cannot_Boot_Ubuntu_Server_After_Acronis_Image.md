---
title: "Cannot Boot Ubuntu Server After Acronis Image"
date: 2009-05-30
forum: Server Platforms
---

### Post by VitalSpark on 2009-05-30
I imaged my server using Acronis 2009 today. I have a mdadm software raid configuration that is currently only running on one drive. First, I needed to setup GRUB after i created the image on the main drive, no problems. Booted, made my changes, broke something and I need to go back to the image I created.  Running Ubuntu 6.06, Kernel 2.6.15-26-server, Intel 945 board.  I setup grub using gparted as my live CD by running...  ```
# grub # root (hd0,0) # setup (hd0,0)
```  (Same thing I needed to do to get the main drive to boot)  Now when I boot, it loads GRUB rather than a flashing cursor, then I get...  ```
ata1: disabling port
```  It does not boot past that. If I switch SATA channels I get the same message but with ata2.  Here is the output of my menu.lst file.  ```
title           Ubuntu, kernel 2.6.15-26-server root            (hd0,0) kernel          /vmlinuz-2.6.15-26-server root=/dev/md1 ro quiet splash initrd          /initrd.img-2.6.15-26-server savedefault boot  title           Ubuntu, kernel 2.6.15-26-server (recovery mode) root            (hd0,0) kernel          /vmlinuz-2.6.15-26-server root=/dev/md1 ro single initrd          /initrd.img-2.6.15-26-server boot 
```  Recovery mode will boot to an extent, after enabling USB devices (which I have since unplugged), it will give me the error.  I noticed when I booted the second drive in the array that I got the error message, but it continued booting. I would have used this drive... but... it has been unplugged since I got it... so VERY old data...   When I imaged, Acronis detected the partitions as RAID partitions. Is it possible that where I imaged to a single drive as oppose to a volume and where it's booting off of an md device, that changing /dev/md1 to /dev/sda1 would have any positive effect?  I'm trying to get the output of df -h but server's too slow processing spam with a terrible config; but I THINK that my configuration is...   sda1=/boot sda2=/ sda3=/var sda4=swap  Does anybody have any suggestions?

---

### Post by VitalSpark on 2009-05-30
Just an update, by changing the md to sda2, I'm able to boot, but because it is in a RAID configuration, it tries to open all hard drives as md devices. Is there a way to trick the system and link the md devices that it is looking for to the sd devices?

Or is there a way to make the device an md device, but not lose all the data?

---

