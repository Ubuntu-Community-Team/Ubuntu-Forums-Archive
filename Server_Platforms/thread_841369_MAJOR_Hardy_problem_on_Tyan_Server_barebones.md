---
title: "MAJOR Hardy problem on Tyan Server barebones"
date: 2008-06-26
forum: Server Platforms
---

### Post by Robstarusa on 2008-06-26
[Barebones]("http://www.tyan.com/product_barebones_detail.aspx?pid=37")

[Motherboard in barebones]("http://www.tyan.com/product_board_detail.aspx?pid=85")

Hi guys,

I have been running Ubuntu 7.10 x86_64 server without a problem, except for vmware time problems.  I was eager to update to 8.04 in order to get the tickless 64 bit kernel (which seems to work better as a vmwhare host) however I have a huge problem.  First doing the distribution upgrade screwed up lilo and I ran into this bug: [https://bugs.launchpad.net/ubuntu/hardy/+source/lilo/+bug/221664](https://bugs.launchpad.net/ubuntu/hardy/+source/lilo/+bug/221664).

I added 2 new (well, used, but empty) disks in, popped out my gutsy disks, and did a fresh install.

This works great except upon first reboot after install my md1/2 (depending how I partition) with LVM is stuck resyncing.  As soon as it hits 93-100% during the MD rebuild, the box reboots.  I can't see what is on the console because it's 15 miles away.

Anyone run into this? 

Chipset: nforce4 of some sort
Processor: amd athlon x2-4800 (lm sensors reports 37-48c operating temp)
Disks: 2* WD RE2 500GB
raid software: mdadm....
Partition setup:

1) /boot md0 device with 512M-1G
and 

2) / md1 device with 20G and then md2+lvm2 400G partition
or
2) / md1+lvm2 device with 20G for slash as a logical volume.

In either case, the result is the same.

I am ripping out my hair.  Anyone ever seen sata_nv/mdadm/hardy cause the box to reboot while synching, roughly at the same point ?

Edit; This is the x86_64 version, I haven't tried i386.  Also: I MUST run x86_64 as I want to run vmware with both 32 & 64-bit guests & I don't have VT hardware extensions.

---

### Post by Robstarusa on 2008-06-28
Updates:

I picked up a SIL3114 controller & instead of randomly rebooting I get tons of errors as the raid array gets around 96/97% checked such as:

ata8.00: status: { DRDY ERR }
ata8.00: error: { UNC }
ata8.00: exception Emask 0x0 ... (other stuff here)
ata8.00: BMDMA2 stat 0x7c0009 ... (other stuff here)
ata8.00: cmd 25/00:00:d5:f3:93

Anyone have ideas to resolve this ?

---

### Post by windependence on 2008-06-28
Doesn't that Tyan board have built in SATAII RAID?

-Tim

---

### Post by promodus on 2008-06-29
Are your drives OK?

I sometimes will test to see if my drive have any errors by running
```
dd if=/dev/sda of=/dev/null
```

If there is a problem with the drive itself, you'll get an IO Error.
No IO Errors, it's likely not the drive.

If you have any valuable data on your drive, be careful running that command, a simple switch of the input file (if) and the output file (of) has it's irreversible consequence.

---

### Post by windependence on 2008-06-29
Hehe, that's why we call dd "disk destroyer". :)

-Tim

---

### Post by promodus on 2008-06-29
> **windependence said:**
> Hehe, that's why we call dd "disk destroyer". :)

-Tim

Yeah I've heard a few of the cautionary acronyms.
To be honest I thought it meant either disk dump or data dump.
Turns out the definition means "dataset definition" So it says in ESR's jargon [page]("http://www.catb.org/jargon/html/D/dd.html").

---

### Post by Robstarusa on 2008-06-30
Guys,

It turned out to be the drives...I bought 2 new (overpriced) 500G drives @ $79 ea. locally, and it works fine with the onboard controller OR the sil 3114 that I bought.

However, isn't it a bug (maybe NV onboard controller bug) that the box REBOOTS without anything on the console as an error message?  I actually sat infront of it while it did this!

---

### Post by windependence on 2008-06-30
Look on the Tyan support site, I think I remember reading about this. You will need to know your MB model. I think there is also a solution posted there for this problem.

-Tim

---

### Post by promodus on 2008-06-30
It depends. Do you have restart on system failure turned on?

Where you able to use dd, on the error did the system hard reset?
(No different than hitting the reset button.)

or did you get an error and then a soft reset?

Often with RAID if there is no fail over you will get a halt to prevent corruption.

Does the Server have a BMC? Is there a log?

---

