---
title: "Need opinion on installing an &quot;encrypted and RAID 1&quot; system"
date: 2009-03-07
forum: Server Platforms
---

### Post by ruipedroca on 2009-03-07
Hi,

Probably a sily question, but I wanted to know your opinion on this:

Is it possible to install an "encrypted and RAID 1" system?
If so, what are the pros and cons?

I'm familiar with installing RAID 1 ubuntu systems and also encrypted ones, but not at the same time.

---

### Post by mrsteveman1 on 2009-03-07
Depends on what you are using to raid the drives together, softraid like md-raid? Or an on-board fakeraid chipset?

If you are using a real hardware raid card you can do whatever you want of course, since Linux thinks it is just one drive. The others will be more complicated but i do believe you can do a luks encrypted md-raid system, though i doubt the installer CD will help you do it. It might need to be manually setup, EG setup the raid device, partition it with a boot and root partition then copy the right files over from an existing system. You might have to do some manual handholding with a livecd to get it to boot correctly, like mount it all and chroot into the new system to get the right packages installed.

Needless to say i have never done it before, but if no one else chimes in to help i will look into it and see what needs to be done.

---

### Post by hyper_ch on 2009-03-08
maybe my little guide helps here:  [http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system](http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system)

---

### Post by ruipedroca on 2009-03-08
> **hyper_ch said:**
> maybe my little guide helps here:  [http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system](http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system)

Litle guide? You're joking, it's a great guide! :D 
Thanks a lot!!


Best Regards

---

