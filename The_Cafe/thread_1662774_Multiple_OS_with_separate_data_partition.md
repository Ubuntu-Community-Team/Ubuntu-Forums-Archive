---
title: "Multiple OS with separate data partition"
date: 2011-01-08
forum: The Cafe
---

### Post by donniezazen on 2011-01-08
Hi All,

Sorry to ask all this over again. I already dual boot Ubuntu and Windows and i am planning to try Natty and/or Kubuntu. Since sharing the same /home partition with multiple os would make it a mess. How about i make a separate btrfs data partition and install Maverick, Natty and Kubuntu individually in 10 GB partitions? I don't need to access data partition from windows so i will go with linux friendly data partition. Will this hold up? Do i need separate home partition for each OS? Do i need swap partition? Will the partition manager let me make so many partition? The outline will be following.

20 GB Windows
10 GB Maverick
10 GB Natty
10 GB Kubuntu
5 GB Swap
rest data partition

How can i seemlessly link softwares to use data partition? So, do i use gparted to make all those partitions and then install each os individually?

---

### Post by Paqman on 2011-01-08
> **soham_1207 said:**
> sharing the same /home partition with multiple os would make it a mess.

No it'd be fine, i've got my machine set up like that. Just use a different user name on each system. Probably easier to keep your data somewhere else, too.

Otherwise, your partitioning scheme looks fine. 5GB is quite a lot for swap though, you're unlikely to need that much unless you have 5GB of RAM and need to use hibernation.

---

### Post by Old_Grey_Wolf on 2011-01-08
If your computer has enough RAM and a decent processor, you may want to give VirtualBox a try, [http://www.virtualbox.org/](http://www.virtualbox.org/). I have virtual machines for several Linux distros, BSD distros, and Microsoft Windows.

---

### Post by MadCow108 on 2011-01-08
you might want to look into lvm for more flexible volume managment.

Also the swap partition is almost certainly too large (I for one don't have one at all,I never exceed my 4gb real ram).
Unless you have less than 1GB ram or special needs (like hibernation under full ram load) you don't need much
And if you do discover you do later you can always add a swap file at any time.

---

