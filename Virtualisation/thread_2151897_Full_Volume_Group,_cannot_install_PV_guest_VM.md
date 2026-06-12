---
title: "Full Volume Group, cannot install PV guest VM"
date: 2013-06-06
forum: Virtualisation
---

### Post by laars80 on 2013-06-06
Hi all,
I have just registered and this is my first post.
I have tried to search for similar problems, but I cannot see anything that solves this particular one.
Probably because I am not 100% what I should look for......so I hope someone might help me out.
After days of try and fail, having formatted the hard-disk by mistake and so forth, I managed to reach my goal:
Installing Ubuntu as Dom0 with Xen as hypervisor. (Notice: first time using Xen, and have only a superficial knowledge of Ubuntu)
In order to manage this I followed the guide at [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen), but found out that only the latest Ubuntu
has the following option at installation time: [COLOR=#333333][FONT=Ubuntu]"Guided - use the entire disk and setup LVM". Unfortunately I was never prompted to enter [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]"Amount of volume group to use for guided partitioning:"[/FONT][/COLOR][FONT=Ubuntu][SIZE=2][COLOR=#333333] and so all the disk was used.[/COLOR][/SIZE][/FONT]
[FONT=Ubuntu][SIZE=2][COLOR=#333333]Now I would like to install Ubuntu also as a guest OS, but when I try to create a new LV in my only Volume Group (ubuntu), I can't because there are only 45 MB free. Now, I know nothing about LVM, but why is there so little free space on a 500 GB hard-disk with only Ubuntu and Xen on?[/COLOR][/SIZE][/FONT]
[FONT=Ubuntu][SIZE=2][COLOR=#333333]Is there any way to resize this VG to get enough space to create a new VG and install guest OSes or to free enough space to create a LV? Or do I have to reinstall everything from [/COLOR][/SIZE][/FONT][FONT=Ubuntu][COLOR=#333333]scratch[/COLOR][/FONT][FONT=Ubuntu][SIZE=2][COLOR=#333333] and hope to get prompted the option to decide the size of the VG this time?

Thanks in advance for any answer!

Federico[/COLOR][/SIZE][/FONT]

---

### Post by slickymaster on 2013-06-06
Hi laars80, welcome to the forum.

There's a great [Beginner's Guide to LVM]("http://www.howtoforge.com/linux_lvm"). It shows all scenarios with examples. I'm sure you'll find what you need in there.

---

### Post by laars80 on 2013-06-12
Thanks for the pointer, I will look at that and hopefully find a solution :)

---

### Post by laars80 on 2013-06-20
Solved the problem. Just so anyone finding this post can try out what worked for me, I followed this tutorial: [http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/](http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/)

It would appear that the logical volume is full because it is the file system using all the space, not actual data. So reducing the file system first, allows to reduce the logical volume afterwords. To be sure not to lose data, one should never shrink more than the actual unused space on the file system, but how to find that out, I do not know. I have a 500 GB hard disk and had just installed Ubuntu, so I knew it would be safe to shrink to 200 GB. 

P.S.: when starting from a CD live, in order to get root access to perform the operations in the tutorial type "sudo su" in the terminal.

---

### Post by heiko_s on 2013-06-20
I use the df command in a terminal window to determine free disk space.

Xen is nice, especially when used with VGA passthrough for a Windows guest. You need suitable hardware for that supporting VT-d/IOMMU - if you are interested in it, look at my how-to for Linux Mint which should work for Ubuntu 12.04 or 12.10 too: [HOW-TO make dual-boot obsolete using XEN VGA passthrough]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013"). Again, this is for running Window under Linux / Xen. Doing VGA passthrough for a Linux HVM guest is actually more difficult, so if you don't want Windows, forget this link!

---

