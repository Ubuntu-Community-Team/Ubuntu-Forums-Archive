---
title: "Virtualbox: Fatal: No bootable medium found! System halted."
date: 2012-04-16
forum: Virtualisation
---

### Post by chelmite2 on 2012-04-16
I'm running Ubuntu 11.10 on an x86_64 machine. The guest is Windows 7.
I've been running Virtualbox 4.1.12 daily since April 3. (and earlier versions before that) I ran it 2 days ago without problems.
When I ran it tonight, I got the message:
Fatal: No bootable medium found! System halted.

I haven't changed any of the virtualbox settings.
 Any idea of what's wrong?
Could one of the latest updates to Ubuntu have broken virtualbox?

VB is configured as:
IDE Controller
    IDE Secondary Master (CD/DVD): Empty
 SATA Controller
    SATA Port 0: Win7-disk1.vdi (Normal, 58.59 GB)

---

### Post by anejo on 2012-04-18
From the info that you given...
I'm guessing that you have your first boot device as the IDE device and your SATA as the second
Because the CD/DVD is empty it'll give that error
If that is the problem then change the boot order!

---

### Post by dzponce11 on 2012-04-19
> **chelmite2 said:**
> I'm running Ubuntu 11.10 on an x86_64 machine. The guest is Windows 7.
I've been running Virtualbox 4.1.12 daily since April 3. (and earlier versions before that) I ran it 2 days ago without problems.
When I ran it tonight, I got the message:
Fatal: No bootable medium found! System halted.

I haven't changed any of the virtualbox settings.
 Any idea of what's wrong?
Could one of the latest updates to Ubuntu have broken virtualbox?

VB is configured as:
IDE Controller
    IDE Secondary Master (CD/DVD): Empty
 SATA Controller
    SATA Port 0: Win7-disk1.vdi (Normal, 58.59 GB)
That's the problem. IDE Secondary master is empty. You need to load an ubuntu 11.10 (Oneiric) .iso file.
That, my friend, can be found at this URL:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

~~~~dzponce11

---

