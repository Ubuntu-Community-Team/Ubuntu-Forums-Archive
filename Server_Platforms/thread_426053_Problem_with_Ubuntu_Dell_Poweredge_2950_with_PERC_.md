---
title: "Problem with Ubuntu Dell Poweredge 2950 with PERC 5/i RAID"
date: 2007-04-28
forum: Server Platforms
---

### Post by mehratul on 2007-04-28
I am trying to Install Ubuntu on  Dell Poweredge 2950 with PERC 5/i RAID 

Harware Specs are as follows:

DELL PowerEdge  2950
**Two Processors**
Dual Core Intel® Pro Xeon® 5120,4MB Cache, 1.86GHz, 1066MHz FSB
Dual Core Intel® Pro Xeon® 5120,4MB Cache, 1.86GHz, 1066MHz FSB

**Memory:**
4GB (4x1024) DDR 667MHz ECC fully buffered

**Hard Drive Configuration:**
146GB 3.5- inch 10K RPM **SAS/SCSI** Hard dirive x 5 nos.
PERC 5/i, Integrated Controller Card

**Using image:**

Ubuntu 6.06 LTS server image at
[http://ftp.esat.net/mirrors/releases.ubuntu.com/releases/dapper/ubuntu-6.06.1-server-amd64.iso](http://ftp.esat.net/mirrors/releases.ubuntu.com/releases/dapper/ubuntu-6.06.1-server-amd64.iso)

Using this image it gives lot of errors while installing through LVM & Software RAID option
Keeping my first two hard dives as RAID 0, When installation completed, system got hanged 
& keyboard is also not accessible, so I restarted  the system I found out, [B]it failed to install bootloader saying 
there is no bootloader and unable to find valid boot device.[/B]

Then I tried installing without RAID, it took me in grub console ( grub>) .i can’t do anything after this.
  
Then I tried with Alternate CD, in this I tried with general LVM partition,
“**Alternate CD install**
[http://ftp.esat.net/mirrors/releases.ubuntu.com/releases/dapper/ubuntu-6.06.1-alternate-amd64.iso](http://ftp.esat.net/mirrors/releases.ubuntu.com/releases/dapper/ubuntu-6.06.1-alternate-amd64.iso) “
I have choose only two Hard drives (/dev/sda & /dev/sdb) I have created two Volume groups then
Logical volumes as shown below:

Volume group  	          LVs      Mount Point
Vg0
  		          boot     /boot
                          root      /
     	                  swap    swap
Vg1
                     	 var       /var
      	                 www    /var/www

While installing it asked where to write MBR through LILO installer, it give three options I chose first one as /dev/sda
It gives error saying failed to write MBR on this HDD you can continue. I have tried with other option too,

Every time after completing installation system gets hanged, when I rebooted it gives me [B] busybox shell  
"Target filesystem doesn't have /sbin/init" some unable map /target/ file system[/B]

Please help me in Installing Ubuntu Server at my PowerEdge 2590 machine with  SCSI hard drives

---

### Post by WesRatcliff on 2007-04-28
[http://ubuntuforums.org/showthread.php?t=226114](http://ubuntuforums.org/showthread.php?t=226114)

---

### Post by rsermilik on 2007-04-28
Don't install software RAID!!!!!!

You have a true RAID controller in your computer!!!
Have you configured the RAID controller? How did you set up your containers?

---

