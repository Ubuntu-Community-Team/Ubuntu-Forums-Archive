---
title: "Multiple Hard Drives"
date: 2010-10-09
forum: Server Platforms
---

### Post by Vaxon on 2010-10-09
I have a second hard drive that I plan on placing in a computer
I wish to use this computer as a server
so my question is how could I use  these 2 hard drives as one
lets say one is 80Gb
and the other is 40GB
how could they be shown as 120GB
instead of being seperate
The installation of server planned on being used is 10.04

---

### Post by sikander3786 on 2010-10-09
You need a RAID configuration.

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

For some useful Ubuntu specific information,

[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Cosma on 2010-10-09
> **sikander3786 said:**
> 
You need a RAID configuration.

wrong. you need to use lvm to "combine" the two hdd's to one larger volume.

---

### Post by sikander3786 on 2010-10-09
> wrong. you need to use lvm to "combine" the two hdd's to one larger volume.

LVM is actually software Raid?

[http://www.i-justblog.com/2009/06/linux-raid-and-lvm-management.html](http://www.i-justblog.com/2009/06/linux-raid-and-lvm-management.html)

---

### Post by Cosma on 2010-10-09
> **sikander3786 said:**
> LVM is actually software Raid?

[http://www.i-justblog.com/2009/06/linux-raid-and-lvm-management.html](http://www.i-justblog.com/2009/06/linux-raid-and-lvm-management.html)

lvm can act as software raid too but thats not how it should be used. the question of Vaxon was how he can combine the space of two hdd's into a single bigger one and for this he will need to use lvm.
this has nothing to do with raid.

with hardware/fake/software raid you need two hdd's or in the case of software raid two partitions of the same size to create a raid volume but that means that you can't create a bigger volume like Vaxon wanted.

---

### Post by Vaxon on 2010-10-09
How would I go about doing the LVM method?

---

### Post by Cosma on 2010-10-09
> **Vaxon said:**
> How would I go about doing the LVM method?

you should find the needed info here:
[https://help.ubuntu.com/community/Installation#LVM%20Installation%20Guides](https://help.ubuntu.com/community/Installation#LVM%20Installation%20Guides)

---

### Post by Vaxon on 2010-10-18
sorry to trouble you but I am completely clueless as to how this would work
I tried to experiment in a virtual box using 2 virtual hard drives tho nothing was accomplished :(
I plan on doing this for a server installation 10.04 if that is of any help
is their a guide somewhere I could follow?

---

