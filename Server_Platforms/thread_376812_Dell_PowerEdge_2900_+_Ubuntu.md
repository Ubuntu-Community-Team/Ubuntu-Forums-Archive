---
title: "Dell PowerEdge 2900 + Ubuntu"
date: 2007-03-05
forum: Server Platforms
---

### Post by dudinatrix on 2007-03-05
Our company is about to purchase a Dell PowerEdge 2900 with plans to install Ubuntu on it, and I want to make sure we're not going to run into compatibility issues first... because I've seen some posts elsewhere discussing issues with Ubuntu on Dell servers.

Specifically I'm wondering about the RAID 1 configuration, having never set it up before.

Plan to install with [ubuntu-6.10-server-i386.iso]("http://mirrors.gigenet.com/ubuntu/edgy/ubuntu-6.10-server-i386.iso") (64bit?)

The main specs are:

**Two Processors**
Dual Core Intel® Xeon® 5050, 2x2MB Cache, 3.00GHz, 667MHz FSB
Dual Core Intel® Xeon® 5050, 2x2MB Cache, 3.00GHz, 667MHz FSB

**Memory**:
1GB 667MHz (2x512MB), Single Ranked DIMMs
[B]
Hard Drive Configuration[/B]:
PERC 5/i, Integrated Controller Card
Integrated SAS/SATA RAID 1, PERC 5/i Integrated

**Primary Hard Drive**:
80GB, SATA, 3.5-inch, 7.2K RPM Hard Drive

**2nd Hard Drive**:
80GB, SATA, 3.5-inch, 7.2K RPM Hard Drive

---

### Post by hlynur on 2007-03-06
I maintain some DELL 1950 and 2950 servers. I run them on dapper but I had to upgrade the kernel to a 2.6.17 to deal with the SAS PERC 5/i controller. I have a SAS/SCSI controller so im not sure you have this issue with the SAS/SATA controller. 



I install them via FAI where I use a 2.6.17 installation kernel and I was not able to install them from a regular 2.6.15 dapper CD. At least it was not possible when I got the first DELL X950 server almost a year ago. 

cheers / Thor

---

### Post by uengberg on 2007-04-26
I just installed Feisty Server on a PowerEdge 840 with the PERC 5/i raid controller. It worked out of the box without problems. We use it for RAID 5, but that clearly shouldn't make a difference.

  Urban

---

### Post by mehratul on 2007-04-28
> **hlynur said:**
> I maintain some DELL 1950 and 2950 servers. I run them on dapper but I had to upgrade the kernel to a 2.6.17 to deal with the SAS PERC 5/i controller. I have a SAS/SCSI controller so im not sure you have this issue with the SAS/SATA controller. 



I install them via FAI where I use a 2.6.17 installation kernel and I was not able to install them from a regular 2.6.15 dapper CD. At least it was not possible when I got the first DELL X950 server almost a year ago. 

cheers / Thor

I am trying to Install Ubuntu on Dell Poweredge 2950 with PERC 5/i RAID

Harware Specs are as follows:

DELL PowerEdge 2950
Two Processors
Dual Core Intel® Pro Xeon® 5120,4MB Cache, 1.86GHz, 1066MHz FSB
Dual Core Intel® Pro Xeon® 5120,4MB Cache, 1.86GHz, 1066MHz FSB

Memory:
4GB (4x1024) DDR 667MHz ECC fully buffered

Hard Drive Configuration:
146GB 3.5- inch 10K RPM SAS/SCSI Hard dirive x 5 nos.
PERC 5/i, Integrated Controller Card

Using image:

Ubuntu 6.06 LTS server image at
[http://ftp.esat.net/mirrors/releases...rver-amd64.iso](http://ftp.esat.net/mirrors/releases...rver-amd64.iso)

Using this image it gives lot of errors while installing through LVM & Software RAID option
Keeping my first two hard dives as RAID 0, When installation completed, system got hanged
& keyboard is also not accessible, so I restarted the system I found out, it failed to install bootloader saying
there is no bootloader and unable to find valid boot device.

Then I tried installing without RAID, it took me in grub console ( grub>) .i can’t do anything after this.

Then I tried with Alternate CD, in this I tried with general LVM partition,
“Alternate CD install
[http://ftp.esat.net/mirrors/releases...nate-amd64.iso](http://ftp.esat.net/mirrors/releases...nate-amd64.iso) “
I have choose only two Hard drives (/dev/sda & /dev/sdb) I have created two Volume groups then
Logical volumes as shown below:

Volume group LVs Mount Point
Vg0
boot /boot
root /
swap swap
Vg1
var /var
www /var/www

While installing it asked where to write MBR through LILO installer, it give three options I chose first one as /dev/sda
It gives error saying failed to write MBR on this HDD you can continue. I have tried with other option too,

Every time after completing installation system gets hanged, when I rebooted it gives me busybox shell
"Target filesystem doesn't have /sbin/init" some unable map /target/ file system

Please help me in Installing Ubuntu Server at my PowerEdge 2590 machine with SCSI hard drives

---

