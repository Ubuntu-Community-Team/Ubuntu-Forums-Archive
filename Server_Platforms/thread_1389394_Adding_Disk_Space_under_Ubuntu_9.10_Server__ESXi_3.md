---
title: "Adding Disk Space under Ubuntu 9.10 Server / ESXi 3.5"
date: 2010-01-24
forum: Server Platforms
---

### Post by Claudius1974 on 2010-01-24
I'm running a Ubuntu 9.10 server on my VMware ESXi 3.5 server. I've added a second hard drive to the ESXi box so have increased the amount of disk space allocated to my VMware server from 10Gb to 20Gb.

My question is it is possible to increase the main partition within Ubuntu to take advantage of the extra space allocated to the virtual server? 

I'm still a bit of a newbie so apologies if this is not possible. I know that it's only really possible under Windows 2003/2008 depending on the drive format chosen when the drive was installed.

---

### Post by ICEB3AR on 2010-01-24
1) I don't know ESXi, but did this "second hard drive" is as if you put in a "real" computer a second hard drive? 
2) Did you install Logical Volume Manager (LVM) - There is a option at the install of ubuntu if you do not manually set up the partitions.

---

### Post by Claudius1974 on 2010-01-28
I might have installed LVM, as I have two Ubuntu virtual machines and did install one with and one without LVM. Can you describe how I would confirm?

---

