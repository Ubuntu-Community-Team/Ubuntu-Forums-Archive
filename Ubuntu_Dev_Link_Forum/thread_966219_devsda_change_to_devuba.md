---
title: "/dev/sda change to /dev/uba?"
date: 2008-11-01
forum: Ubuntu Dev Link Forum
---

### Post by gaarie on 2008-11-01
so let me explain the situation. i've got a closed source program running that will automatically mount any flash drives plugged into /dev/uba-ubf. 

here's part of the fstab for the original system, on which the mounting worked perfectly...

```
/dev/uba	/mnt/flash1	vfat	noauto,owner	0	0
/dev/uba1	/mnt/flash1	vfat	noauto,owner	0	0
/dev/ubb	/mnt/flash2	vfat	noauto,owner	0	0
/dev/ubb1	/mnt/flash2	vfat	noauto,owner	0	0
/dev/ubc	/mnt/flash3	vfat	noauto,owner	0	0
/dev/ubc1	/mnt/flash3	vfat	noauto,owner	0	0
/dev/ubd	/mnt/flash4	vfat	noauto,owner	0	0
/dev/ubd1	/mnt/flash4	vfat	noauto,owner	0	0
/dev/ube	/mnt/flash5	vfat	noauto,owner	0	0
/dev/ube1	/mnt/flash5	vfat	noauto,owner	0	0
/dev/ubf	/mnt/flash6	vfat	noauto,owner	0	0
/dev/sdf1	/mnt/flash6	vfat	noauto,owner	0	0
```

i have switched the working operating system to ubuntu as opposed to debian sarge, and now the usb drive wants to mount on sdb by default, so now the program will not mount any drives plugged in automatically.

what can i do to change my ubuntu configuration so that flash drives mount to /dev/uba or /dev/ubb etc...

i have tried creating hard links using 

```
ln /dev/sda /dev/uba
```
etc...

but it does not seem to work. they are erased almost immediately.

thanks in advance for any pointers that you may be able to give me.

EDIT: i think i am on the right track with mknod, but i have no idea how to use it. i've got the usb .ko module files that came with the original distribution, and i am inserting them with insmod.

can anyone help me create the devices with mknod properly? i want to make sure i am doing it right.

i have four usb ports on the back of the computer. i need to make sure that when a usb drive is plugged into a specific port, it is assigned the right ub* based on bus and device IDs.

---

### Post by lensman3 on 2008-12-14
You did a "ln /dev/sda /dev/uba".  That is a hard link.  What happens with a softlink:

ln -s /dev/sda /dev/uba

---

