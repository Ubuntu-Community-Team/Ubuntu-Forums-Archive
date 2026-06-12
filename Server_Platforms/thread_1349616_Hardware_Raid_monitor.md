---
title: "Hardware Raid monitor"
date: 2009-12-08
forum: Server Platforms
---

### Post by Heeter on 2009-12-08
Hello all,

I would like to know if there is a RAID monitor for my Ubuntu setup. Need something to tell me the status of the RAID and the status of the HD's. The server has been running properly, with no issues for a couple of years now. But I think that one of my HD's is on the fritz. The only way of monitoring right now is on bootup and going into the RAID controller BIOS, but it doesn't tell me enough, and the server has to be down during the process.

My Specs:

AMD 9750 Quad Core, 8 GIG RAM, Promise FastTrak 4310 RAID Controller, 4 x 1Tera Seagate HD in a Mirrored RAID setup, VMWare Server 2 & Ebox sitting on top of Ubuntu 8.10 64bit host.

Promise says that they don't support linux on this controller, but I do have it working just fine.

Thanks

Heeter

---

### Post by munky99999 on 2009-12-08
Since it's a raid controller. I'm personally not sure if these work... but something like.

cat /proc/mdstat

That should give you a sort of like.

Like HD 0/2 HD 1/2 HD 2/2

Then if you had a drive crap out. One will be missing in the chain. If you're having resync problems. Then it'll out and say there's a sync thing going on.

[http://raidmonitor.sourceforge.net/](http://raidmonitor.sourceforge.net/)

That one is a gui version of that basically.

---

### Post by jrgp on 2009-12-08
> **munky99999 said:**
> Since it's a raid controller. I'm personally not sure if these work... but something like.

cat /proc/mdstat

That should give you a sort of like.

Like HD 0/2 HD 1/2 HD 2/2


It should be mentioned that this will only work with software raid arrays created with [mdadm]("http://en.wikipedia.org/wiki/Mdadm"), not actual hardware arrays.

See if the manufacturer of your raid card provides a Linux utility.

---

### Post by Heeter on 2009-12-08
Thanks for replies, Guys,

I have contacted the tech support, but they don't support Linux.

But they do support Window Servers :sad:

Go Figure.

Heeter

---

### Post by whoop on 2009-12-08
Isn't WebPAM (Web-based Promise Array Management) supposed to be supported under linux? Never used that tool, but it's supposed to monitor drives...

---

### Post by Heeter on 2009-12-08
I cannot get webpam to install on my Ubuntu Server. Looks like it was made for Suse/RedHat.

Heeter

---

### Post by trundlenut on 2009-12-09
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=1019045") thread and see if there is a package for your card.

---

### Post by Heeter on 2009-12-09
Thanks, trundlenut

That is an awesome thread. Great find.


Heeter

---

