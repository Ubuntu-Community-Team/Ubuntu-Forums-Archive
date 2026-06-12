---
title: "RocketRaid 26xx on 12.04 LTS Kernel 3.2"
date: 2012-04-26
forum: Server Platforms
---

### Post by djroketboy on 2012-04-26
I've used [this guide]("http://www.maistech.net/2011/12/rocketraid-26xx-driver-on-ubuntu-1004.html") in the past and its worked great at getting the driver up and running for Ubuntu. Well today I was dumb and upgraded my server to 12.04. I started searching and found [this update]("http://ubuntuforums.org/showthread.php?t=1856162") but am now running into a problem when compiling.

either manually or using DKMS, i get this error:
```
/lib/modules/3.2.0-24-generic/build/include/linux/linkage.h:5:25: fatal error: asm/linkage.h: No such file or directory
```

i *think* i found the file, but not sure where or if I should link it.
```
/usr/src/linux-headers-3.2.0-24/arch/ia64/include/asm/linkage.h
```

Anyone have any idea of what I should do?

Error output during make:

$ make
[CC] /usr/src/rr26xx-1.3/osm/linux/os_linux.c
In file included from /lib/modules/3.2.0-24-generic/build/include/linux/kernel.h:13:0,
                 from /lib/modules/3.2.0-24-generic/build/include/linux/cache.h:4,
                 from /lib/modules/3.2.0-24-generic/build/include/linux/time.h:7,
                 from /lib/modules/3.2.0-24-generic/build/include/linux/stat.h:60,
                 from /lib/modules/3.2.0-24-generic/build/include/linux/module.h:10,
                 from /usr/src/rr26xx-1.3/osm/linux/osm_linux.h:21,
                 from /usr/src/rr26xx-1.3/osm/linux/os_linux.c:6:
/lib/modules/3.2.0-24-generic/build/include/linux/linkage.h:5:25: fatal error: asm/linkage.h: No such file or directory
compilation terminated.
make: *** [os_linux.o] Error 1

---

### Post by dmalizia on 2012-04-27
Hi, I have the same problem after upgrading to Pangolin. 
Is your box 32 bit? 
I tried looking at the kernel 

```
dpkg -l|grep linux-image
```

and, though I'm not sure if it is relevant, I found 

```
ii  linux-image-3.0.0-16-generic           3.0.0-16.29                                Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-17-generic           3.0.0-17.30                                Linux kernel image for version 3.0.0 on x86/x86_64
iU  linux-image-3.2.0-24-generic           3.2.0-24.37                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-generic                    3.2.0.24.26                                Generic Linux kernel image
```

For some reason the last kernel looks different. I would have epected it to end in x86/x86_64.

Wonder how to fix it?

---

### Post by dmalizia on 2012-04-27
Oh, BTW I found I had an error during the upgrade while replacing the python version. I'm trying to fix that and hoping it might make a difference.

---
Yes, The version update had gone wrong. 

I booted with an old kernel and the following sorted me out

sudo apt-get update
sudo apt-get -f install
sudo apt-get dist-upgrade


I had to change the download server from Italy to the main one since the local one doesn't seem to have all the security updates. For the rest it seems to work.
Good Luck.

---

### Post by djroketboy on 2012-05-01
Nope, i'm on 64-bit. I've had to roll back to 10.04 LTS for now until I can get this resolved or buy a different eSATA card.

---

### Post by ulysses768 on 2012-05-06
Is asm folder in '/lib/modules/$(uname -r)/build/include' ?

If not try linking to it. 

'ln -s /lib/modules/$(uname -r)/arch/x86_64/include/asm /lib/modules/$(uname -r)/build/include/'

---

### Post by CharlesA on 2012-05-06
> **djroketboy said:**
> Nope, i'm on 64-bit. I've had to roll back to 10.04 LTS for now until I can get this resolved or buy a different eSATA card.
What card are you running?

I've got the drivers for my rr2640 to compile fine after following the directions in the RocketRaid wiki page:

[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

---

### Post by djroketboy on 2012-06-10
> **CharlesA said:**
> What card are you running?

I've got the drivers for my rr2640 to compile fine after following the directions in the RocketRaid wiki page:

[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

I have the RocketRaid 2642. I had purchased a JMicron SATA board to replace it, but the performance is just not there. So I am back attempting to compile this again. From what I've seen and read a lot has changed, and the drivers from High-Point have been updated, but I'm still running into a couple small errors.

From what I can tell the revisions from ([this site]("https://help.ubuntu.com/community/RocketRaid")) are now integrated into the v1.4 driver from High-Point.

My first problem is now when I add to DKMS, I get this error:
```
 /usr/src/rr26xx-1.4/dkms.conf: line 7: rr26xx: command not found

Creating symlink /var/lib/dkms/rr26xx/1.4/source ->
                 /usr/src/rr26xx-1.4

DKMS: add completed.
```

Line 7 is this line, but I'm not entirely sure how to change it.
```
POST_BUILD=”doModule.symvers rr26xx save $dkmstree/$module/$moduleversion/build/Module.symvers”
```

Ok, so I'll skip DKMS for now, and manually compile. But I get a stop error here...
```
make[2]: *** No rule to make target `/usr/src/rr26xx-1.4/lib/linux/free-x86_64-regparm0/him_odin.o', needed by `/usr/src/rr26xx-1.4/product/rr2640/linux/.build/him_odin.o'.  Stop.
make[1]: *** [_module_/usr/src/rr26xx-1.4/product/rr2640/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
make: *** [rr26xx.ko] Error 2
```

Info:
3.2.0-24-generic
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise
RocketRaid 2642
rr264x-linux-src-v1.4-120524-1520

---

### Post by CharlesA on 2012-06-10
I just tested the version 1.4 source drivers on 12.04, and make worked fine.

DKMS worked fine with this dkms.conf file:

After unpacking the source drivers from the site, add these lines to dkms.conf in the directory you unpacked to.

```
MAKE="make -C product/rr2640/linux KERNDIR=/lib/modules/${kernelver}/build"
CLEAN="make -C product/rr2640/linux/ clean"
BUILT_MODULE_NAME=rr26xx
DEST_MODULE_LOCATION=/kernel/drivers/scsi/
BUILT_MODULE_LOCATION=product/rr2640/linux/
PACKAGE_NAME=rr264x
PACKAGE_VERSION=1.4
AUTOINSTALL=yes
REMAKE_INITRD=yes

```

cd into that directory and run these:

```
sudo cp -R . /usr/src/rr264x-1.4
sudo dkms add -m rr264x -v 1.4
sudo dkms build -m rr264x -v 1.4
sudo dkms install -m rr264x -v 1.4

```

Check for build errors. It compiled fine on the test box I used:

charles@Tardis:~$ uname -r
3.2.0-24-generic

EDIT: I did not have to make any changes to the source with the v 1.4 driver.

---

### Post by djroketboy on 2012-06-10
> **CharlesA said:**
> I just tested the version 1.4 source drivers on 12.04, and make worked fine.

DKMS worked fine with this dkms.conf file:

After unpacking the source drivers from the site, add these lines to dkms.conf in the directory you unpacked to.

```
MAKE="make -C product/rr2640/linux KERNDIR=/lib/modules/${kernelver}/build"
CLEAN="make -C product/rr2640/linux/ clean"
BUILT_MODULE_NAME=rr26xx
DEST_MODULE_LOCATION=/kernel/drivers/scsi/
BUILT_MODULE_LOCATION=product/rr2640/linux/
PACKAGE_NAME=rr264x
PACKAGE_VERSION=1.4
AUTOINSTALL=yes
REMAKE_INITRD=yes

```

cd into that directory and run these:

```
sudo cp -R . /usr/src/rr264x-1.4
sudo dkms add -m rr264x -v 1.4
sudo dkms build -m rr264x -v 1.4
sudo dkms install -m rr264x -v 1.4

```

Check for build errors. It compiled fine on the test box I used:

charles@Tardis:~$ uname -r
3.2.0-24-generic

Sweet, that worked perfectly, and way less work :)

I caught some of my errors, and was just about to post and update. 

Thank you!!!

---

### Post by CharlesA on 2012-06-10
> **djroketboy said:**
> Sweet, that worked perfectly, and way less work :)

I caught some of my errors, and was just about to post and update. 

Thank you!!!
Yeah, I used the same dkms.conf that I used with the 1.3 drivers, but it looks like some of the directory names changed.

I just installed it on my server and everything is good now. :)

---

### Post by scotjam1981 on 2012-09-16
CharlesA - your posts / answers on the rocketraid 26xx card drivers have been hugely valuable. Just to provide an update to the instructions for the 2680 on v1.8 of the source (for the benefit of others - hopefully they can see the differences between what I have done and what you had done, and make the equivalent changes for newer versions such as 1.9), I used the following for the dkms.conf:
```
MAKE="make -C product/rr2680/linux/

KERNELDIR=/lib/modules/${kernelver}/build"

CLEAN="make -C product/rr2680/linux/ clean"

BUILT_MODULE_NAME=rr2680

DEST_MODULE_LOCATION=/kernel/drivers/scsi/ BUILT_MODULE_LOCATION=product/rr2680/linux/

PACKAGE_NAME=rr2680

PACKAGE_VERSION=1.8

AUTOINSTALL=yes

REMAKE_INITRD=yes
```
and then copy the folder contents to a new folder /usr/src/rr2680-1.8 and then:
```
sudo dkms add -m rr2680 -v 1.8
sudo dkms build -m rr2680 -v 1.8
sudo dkms install -m rr2680 -v 1.8
```

---

### Post by CharlesA on 2012-09-16
Awesome job.

---

