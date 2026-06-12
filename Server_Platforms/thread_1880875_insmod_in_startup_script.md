---
title: "insmod in startup script"
date: 2011-11-14
forum: Server Platforms
---

### Post by david.garceau on 2011-11-14
Hey guys, working on getting my areca raid card setup... I am now running into issues getting the driver to auto load on startup BEFORE the hard drives are mounted (the os is not on the raid card it is on a seperate drive). 

The command i run while in the os is 

insmod arcmsr.ko

How would i get this to startup by itself before the hard drives try to mount on startup.

---

### Post by david.garceau on 2011-11-17
bump...

---

### Post by hawkmage on 2011-11-17
It sounds like you need to install a Loadable Module.  Take a look at this: [https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

---

### Post by matt_symes on 2011-11-17
Hi

> **david.garceau said:**
> Hey guys, working on getting my areca raid card setup... I am now running into issues getting the driver to auto load on startup BEFORE the hard drives are mounted (the os is not on the raid card it is on a seperate drive). 

The command i run while in the os is 

insmod arcmsr.ko

How would i get this to startup by itself before the hard drives try to mount on startup.

Take a look at 

```
cat /etc/init/mountall.conf
```and the other mount scripts in /etc/init/

That may be the way forward for you. 

Kind regards

---

### Post by david.garceau on 2011-11-17
The driver that i need to use is not included with ubuntu. I had to build it myself, everything works when i manually load the module using insmod arcmsr.ko. I just need to figure out how to get it to start automatically.

> **hawkmage said:**
> It sounds like you need to install a Loadable Module.  Take a look at this: [https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

---

### Post by david.garceau on 2011-11-17
mounting isnt the issue. Getting the module to load prior to the hard drives being mounted is the issue.

> **matt_symes said:**
> Hi



Take a look at 

```
cat /etc/init/mountall.conf
```and the other mount scripts in /etc/init/

That may be the way forward for you. 

Kind regards

---

### Post by matt_symes on 2011-11-17
Hi

I think you missed my point entirely. 

mountall.conf is a script that is used to mount the partitions in /etc/fstab. It is called by init, the first main user space process after initramfs.

What about loading the module *(exec insmod)* before mountall *(exec mountall --daemon $force_fsck $fsck_fix)* is called in that file.

That may work for you.

Kind regards

---

### Post by david.garceau on 2011-11-17
I absolutely did haha. I went ahead and added exec insmod /home/david/arcmsr.1.20.0X.15-110622/arcmsr.ko right before the exec mountall --daemon $force_fsck $fsck_fix. I am now getting this at boot...

udevd-work[434]: open /dev/null failed no such file or directory

> **matt_symes said:**
> Hi

I think you missed my point entirely. 

mountall.conf is a script that is used to mount the partitions in /etc/fstab. It is called by init, the first main user space process after initramfs.

What about loading the module *(exec insmod)* before mountall *(exec mountall --daemon $force_fsck $fsck_fix)* is called in that file.

That may work for you.

Kind regards

---

### Post by matt_symes on 2011-11-17
Hi
> 
I absolutely did haha. I went ahead and added exec insmod  /home/david/arcmsr.1.20.0X.15-110622/arcmsr.ko right before the exec  mountall --daemon $force_fsck $fsck_fix. I am now getting this at  boot...

udevd-work[434]: open /dev/null failed no such file or directory

/dev/null is not created when mountall is called ? If that is correct then i am very surprised indeed.

It may be because it has not mounted the root partition at that point.

I don't use RAID in Linux so i may not be the best help, however it seems to me you may have a number of options.

You can add the module into your initramfs and get it loaded from there.

You can mount the root partition first in mountall.conf and then mount the RAID array after.

You can try to load the module using any specific configuration script for raid.

I'm not sure of the best approach as i don't use RAID. Give it some time to see what others think.

Kind regards

---

### Post by david.garceau on 2011-11-17
Got it working,

in /etc/init/mountall.conf

at the bottom this is how i got it to work, i just put the insmod below the rm -f /forcefsck 2>dev/null || true and it works great thanks for the help!

post-stop script
    rm -f /forcefsck 2>dev/null || true
    exec insmod /home/david/arcmsr.1.20.0X.15-110622/arcmsr.ko
end script

---

### Post by hawkmage on 2011-11-17
Since the arcmsr.ko is under you home directory I assume that it was not installed.  It really should be in the /lib/modules/*<kernel_version>*/kernel/drivers/scsi/ directory.  Then you should be able to add "arcmsr" to the end of the[FONT=Verdana] [/FONT]/etc/modules file to have it load automatically.

---

