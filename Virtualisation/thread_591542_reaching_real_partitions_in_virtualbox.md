---
title: "reaching real partitions in virtualbox?"
date: 2007-10-25
forum: Virtualisation
---

### Post by realitybites on 2007-10-25
is there a way to mount real drives to a windows xp installed on virtualbox or do i have to use only virtual disks? 
or can i create virtual disks on other partitions except linux partition?

or is there any virtual environment i can do those? i want to reach all my partitions

i'm using gutsy, with win xp pro installed on vbox

---

### Post by bodhi.zazen on 2007-10-25
You can share partitions if you like, install the virtualBox addons.

IMO, my advice is to use network share protocols such as samba or NFS or sshfs etc. for shared directories, no need to share your entire hard drive ;)

---

### Post by realitybites on 2007-10-25
but i want to install applications on those disks, i don't think sharing them on network will solve the problem. or am i wrong? :)

---

### Post by bodhi.zazen on 2007-10-25
You should install applications on the virtual disk that you create for virtualbox. I would think that some applications *may* do OK with this idea (firefox for example), and those apps would run just fine over samba, nfs, or sshfs, but most applications, and certainly almost all windows applications will not like your idea.

I am not sure what you are trying to do, boot a physical partition ? I think of virtual machines the same as physical machines. They have their own hard drive, videocard, ethernet card. The virtual ones are software emulated is all.

---

### Post by rukshankb on 2009-03-16
Most of drivers are installed in original OS. so you don't need to install it again.

---

### Post by namaku0 on 2009-03-17
There is a way to make real disk/partition as virtual disk
for VirtualBox 2.x. Open the VirtualBox user guide/manual
(Help > Contents... F1) and find it there (chapter 9.10).

But I agree with everyones, try with folder sharing +
VB Guest Addition first. You can map a folder share to
a drive (again, read the manual chapter 4.6).

---

