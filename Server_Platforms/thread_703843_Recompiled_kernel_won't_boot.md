---
title: "Recompiled kernel won't boot"
date: 2008-02-21
forum: Server Platforms
---

### Post by TruckStuff on 2008-02-21
I've got several Dell PowerEdge servers running Feisty.  I need to update the kernel to address the vmsplice() vuln found a couple of weeks ago ([http://secunia.com/advisories/28835/](http://secunia.com/advisories/28835/)).  I've been recompiling kernels on other Linux distros for years without problem, but this is my first stab at doing it on Ubuntu.

I downloaded 2.6.24.2 from kernel.org and have made several attempts to recompile following the instructions [here](https://help.ubuntu.com/community/Kernel/Compile).  I am able to compile the kernel just fine, but none of them have been able to boot.  On boot, depmode, kbd_mode and udevd complain about not being able to find shared libraries (e.g. libc.so.6, libcutils.so.0, etc.).  Then it says "Mounting Root File System..." and "Running /scripts/local-top" and "Waiting for root file system...".  After a few minutes of waiting, I get dropped to a BusyBox shell.  

My guess is that my RAID driver and associated SCSI modules aren't getting loaded properly into the initrd image so the kernel can't find any volumes to boot from.  I added the module for my RAID controller (megaraid_sas) to /etc/initramfs-tools/modules, but even after rebuilding the initrd image, I am still unable to boot.  The BusyBox shell seems to look like a fairly sparse image, with almost nothing in /proc or /dev.  What am I doing wrong here?

---

### Post by Gen2ly on 2008-02-21
Nothing.... looks like.  Yeah the filesystem isn't being found.  To be truthful, I never really understood the initrd, I've always used the

```
make oldconfig
make menuconfig
make clean zImage modules modules_install install 
```

route and updated menu.1st.  Maybe I'm old fashioned.

---

### Post by TruckStuff on 2008-02-22
I like being able to use initrd's to make smaller kernels, but they can be a bit "tricky", IMHO.

When the initrd loads, it seems that none of the commands in the init script can find the required shared libraries.  For example, it calls depmod which needs libc.so.6 and ld-linux-x86-64.so.2.  In the initrd, these files are located in /lib64, not in /lib.  If I extract the initrd image onto a working system and ldd these binaries, it says that its looking for the libraries in /lib64, but I'm wondering if this isn't the case when its actually booting.  Is there a way to change the LD_PATH used by the binaries on the initrd?  Maybe /lib64 is left out of the LD_PATH and that is what is causing my problems.  Any thoughts on this?

---

### Post by TruckStuff on 2008-02-22
I guess another option would be to recompile module-init-tools statically so that shared libraries aren't needed.  Thoughts on this idea?

---

### Post by TruckStuff on 2008-02-22
> **TruckStuff said:**
> When the initrd loads, it seems that none of the commands in the init script can find the required shared libraries.  For example, it calls depmod which needs libc.so.6 and ld-linux-x86-64.so.2.  In the initrd, these files are located in /lib64, not in /lib.  If I extract the initrd image onto a working system and ldd these binaries, it says that its looking for the libraries in /lib64, but I'm wondering if this isn't the case when its actually booting.  Is there a way to change the LD_PATH used by the binaries on the initrd?  Maybe /lib64 is left out of the LD_PATH and that is what is causing my problems.  Any thoughts on this? Seems I am on to something here.  From the busybox shell, if I copy /lib64/* to /lib, all of the shared libraries are found and things start to work.  I'm still not able to boot just yet, but I am at least headed in the right direction.

So here are some additional questions:

1. Are there any known bugs with initramfs-tools on 64bit platforms?  I'm about to head over to the Bug Tracker myself, but thought I would ask while here.

2. How do I go about building a custom initrd?  I know they are zipped cpio images on Ubuntu, and can unpack them with cat initrd.img | gunzip -dc | cpio -i, but what is the proper way to reverse this process?

TIA

---

### Post by Gen2ly on 2008-02-22
All intersting questions.  I've always been curious what the initrd was and why it was needed.  I read the wikipedia explanation of it and its a temporary filesystem be able to help make preperations for the root filesystem.  I'm guessing it's ability  allows us to do such things as select noapic.  I'm not sure why the common user would need this.

---

### Post by TruckStuff on 2008-02-24
Well I have "resolved" this problem by creating a work-around.  Basically, I added the following line just before the depmod call in /usr/share/initramfs-tools/init: ```
cp /lib64/* /lib
``` Rebuild the initramfs image and everything boots fine.

Interestingly, I tried manually editing the initrd image with no luck.  I unpacked the image using the previously posted method, copied lib64/* to lib/, then recreated the image with the following: ```
find . -print | cpio -o | gzip > /boot/initrd.img
```  However, when I tried to boot using this image, I kernel paniced because it couldn't find my boot device.  Don't ask me what the difference is between these two methods, but one works and the other doesn't.

So my love-hate relationship with Ubuntu goes on.  Ubuntu continues to be one of the easiest, yet most over-whelmingly frustrating distros to use: some stuff is easy to do, but at times the easiest task can be so absurdly difficult that it almost warrants removal.  But enough ranting for one day...

---

