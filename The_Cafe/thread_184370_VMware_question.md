---
title: "VMware question"
date: 2006-05-29
forum: The Cafe
---

### Post by briancurtin on 2006-05-29
first off, if another thread can answer this, shoot me the link and we can close this one. the reason i say that first, is because i know VMware is talked about a lot and i couldnt find anything on my question, since its more simple and not support-based. i did search, but didnt find much on my query.

right now i have a bunch of partitions, and i use them all and would prefer to not resize/recreate *any if possible*. if i want to check out distros in VMware -- do i need to have a partition specifically for distros that i want to run in it?

can someone go over the very basics of VMware, as to if or how i can use it with a currently "full" disk? im just wondering if i can take my current computer and toy with things in VMware

---

### Post by GreyFox503 on 2006-05-29
If I understand your question correctly, the answer is no, you do not need another partition for VMWare.

I did the same thing awhile ago, because I wanted to try several distributions easily without repartitioning.

What VMWare (and QEMU) does is create a virtual disk as a file (or a set of files) on an existing partition.  It is similar to CD images (like Ubuntu images), you download a file which represents a physical disc.  VMWare just creates a set of files on an existing partition and uses them as a virtual hard disk.  You can set the program to just expand the amount of space as needed, and I would recommend doing this to save space.

If all that is confusing, don't worry about.  As long as you have a few spare gigs free on the partition you create the virtual machines on, you'll be fine.  That's one of the best things about VMWare - no partitioning!

---

### Post by Sammi on 2006-05-29
I'm a relative noob to Linux and I've just tried to setup a virtual XP with vmware. I can confirm all that GreyFox503 says and add this to clarify my experience: It works painlessly without any need for partitioning!

---

### Post by briancurtin on 2006-05-29
alright cool, thanks guys. i have a bunch of partitions as it stands right now, and didnt want to have to resize and make room for another. ill check out VMware now that i know it will work for what i have going on and what i want out of it.

thanks again

---

### Post by mstlyevil on 2006-05-29
[QUOTE=briancurtin]alright cool, thanks guys. i have a bunch of partitions as it stands right now, and didnt want to have to resize and make room for another. ill check out VMware now that i know it will work for what i have going on and what i want out of it.

thanks again[/QUOTE]

Just make sure you have enough space on your partition to run the number of vmware distros you plan to run. 8GB is default but can be made smaller if you like.

---

