---
title: "recovering root password off LVM partition"
date: 2021-10-25
forum: Server Platforms
---

### Post by espressobeanmachine on 2021-10-25
I am needing to recover the account passwords, I am using a Live CD regarding this since I cannot boot into the recovery mode for some reason. I have a hard drive that has three partitions on it, the main one being on /dev/sda3, the issue is that I get 
```
mount: unknown filesystem type 'LVM2_member'. 
```
How do I go about getting this resolved so I can mount the partition and change the passwords?

---

### Post by rsteinmetz70112 on 2021-10-25
I think you may need to install lvm2 and maybe mdadm into the live system.

---

### Post by Tadaen_Sylvermane on 2021-10-26
Indeed. You need to install the lvm2 package. You will then need to execute ```
vgscan && vgchange -ay
``` [https://wiki.archlinux.org/title/LVM#Logical_Volumes_do_not_show_up](https://wiki.archlinux.org/title/LVM#Logical_Volumes_do_not_show_up)

---

### Post by MAFoElffen on 2021-10-27
Can you not get to a Grub Menu on Boot? (pressing the left-shift key repeatedly as it ends the POST process)?

---

