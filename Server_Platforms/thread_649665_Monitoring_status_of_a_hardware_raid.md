---
title: "Monitoring status of a hardware raid"
date: 2007-12-25
forum: Server Platforms
---

### Post by fiendishlyclever on 2007-12-25
I have picked up a Dell Poweredge SC440 server on a special promo deal.  They upgraded my processor free of charge so I got them to put in a raid card thinking it would be good for data security to run a mirror.

That is where my problems started.  I'm not a linux expert but I have several linux systems and have always got them to do my bidding before.

Hardware raid is set up in the bios and I've managed to install ubuntu server (64bit) onto the mirrored raid.  The problem is that I have no way of monitoring the health of my raid.

I've searched these forums and google at length - and tried various suggestions including dell openmanage and MegaCLI - none of which I've got to detect my hardware to see the status.

I'm at a dead end now and I don't know where to go next - nothing seems to work and I'm considering wiping and putting Windows on because I know drivers are straightforward for that.

The raid controller in question is a Dell SAS 5/iR - which Linux reports: scsi0 : ioc0: LSISAS1068, FwRev=000a3300h, Ports=1, MaxQ=286, IRQ=16

Any pointers welcomed.

---

### Post by fiendishlyclever on 2007-12-25
Seems that after trying every thing I could think of I stumbled across a partial solution.

I found out [ here ](http://loftninjas.org/blog/2007/12/dell-omsa-for-sas-raid-on-debian-etch.html) that 

> /etc/init.d/dataeng stop ; modprobe mptctl ; /etc/init.d/dataeng start' got the storage portion of omreport working for me

When I had done this I got mpt-status working properly and reporting on the health of my raid.  

What I need now is: 

a way to make this happen automatically
a script to check/warn of failures

Any suggestions?

---

### Post by rsw686 on 2007-12-25
You could just use the controller without the RAID features and go with software RAID. That Dell RAID controller only sells for $100 so it most likely is a software/hardware solution meaning it uses the CPU. You could do some performance tests with the controller vs software RAID regarding speed and CPU utilization. I think you will find it comes out around the same.

---

