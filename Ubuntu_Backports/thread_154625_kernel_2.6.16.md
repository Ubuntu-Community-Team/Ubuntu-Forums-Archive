---
title: "kernel 2.6.16"
date: 2006-04-03
forum: Ubuntu Backports
---

### Post by asundaresan on 2006-04-03
Hi,

I'll state at the beginning that I have already read 
[https://wiki.ubuntu.com/KernelByHandHowto](https://wiki.ubuntu.com/KernelByHandHowto)
[https://wiki.ubuntu.com/KernelCompileHowto](https://wiki.ubuntu.com/KernelCompileHowto)

While these provide a single solution, I am not sure about that it is the best solution for me. I need some new features in my kernel and I wonder what the status of kernel back porting is. For instance can I install an kernel 2.6.15 on breezy? 

What is the best solution if I need a newer kernel version?

Suppose I need to compile the latest kernel (2.6.15) in breezy, can I do the following?

```
$ ls debian/config/i386/config debian/config/i386/config.server > .config
$ make menuconfig 
$ fakeroot make-kpkg clean
$ fakeroot make-kpkg --append-to-version -l1 --revision 0 --initrd binary

```

I realise that this will not be supported, but is there any other option? Is there anything I should be aware of when I do this?

Thanks,
Aravind.

---

### Post by asundaresan on 2006-04-03
[quote=asundaresan]Hi,

I'll state at the beginning that I have already read 
[https://wiki.ubuntu.com/KernelByHandHowto]("https://wiki.ubuntu.com/KernelByHandHowto")
[https://wiki.ubuntu.com/KernelCompileHowto]("https://wiki.ubuntu.com/KernelCompileHowto")

While these provide a single solution, I am not sure about that it is the best solution for me. I need some new features in my kernel and I wonder what the status of kernel back porting is. For instance can I install an kernel 2.6.15 on breezy? 

What is the best solution if I need a newer kernel version?

Suppose I need to compile the latest kernel (2.6.15) in breezy, can I do the following?

```
$ ls debian/config/i386/config debian/config/i386/config.server > .config
$ make menuconfig 
$ fakeroot make-kpkg clean
$ fakeroot make-kpkg --append-to-version -l1 --revision 0 --initrd binary

``` 
I realise that this will not be supported, but is there any other option? Is there anything I should be aware of when I do this?

Thanks,
Aravind.[/quote] 
Hi,

I actually used the .config file obtained as described above to make, build and install linux-2.6.16.1 obtained from kernel.org suing make-dpkg. There doesn't seem to be any problem, but there are some errors during boot up such as 

 ```

insmod: error inserting '/lib/modules/2.6.16.1-l1/kernel/drivers/video/console/bitblit.ko': -1 Unknown symbol in module
insmod: error inserting '/lib/modules/2.6.16.1-l1/kernel/drivers/video/console/fbcon.ko': -1 Unknown symbol in module
insmod: can't read '/lib/modules/2.6.16.1-l1/kernel/drivers/video/softcursor.ko': No such file or directory
 
```

during the initial part of the bootup.

However, these modules are indeed present and I can load them after boot up.

```

aravinds@lerna0:/lib/modules$ find . -iname fbcon.ko
./2.6.12-9-386/kernel/drivers/video/console/fbcon.ko
./2.6.16.1-l1/kernel/drivers/video/console/fbcon.ko
aravinds@lerna0:/lib/modules$ find . -iname softcursor.ko
./2.6.12-9-386/kernel/drivers/video/softcursor.ko
./2.6.16.1-l1/kernel/drivers/video/console/softcursor.ko
aravinds@lerna0:/lib/modules$ find . -iname bitblit.ko
./2.6.12-9-386/kernel/drivers/video/console/bitblit.ko
./2.6.16.1-l1/kernel/drivers/video/console/bitblit.ko

``` 

I also get these errors 

```

[42949426.070000] device-mapper: 4.5.0-ioctl (2005-10-04) initialised: dm-devel@redhat.com
[42949426.520000] device-mapper: dm-linear: Device lookup failed
[42949426.520000] device-mapper: error adding target to table
[42949426.530000] device-mapper: dm-linear: Device lookup failed
[42949426.530000] device-mapper: error adding target to table
[42949426.530000] device-mapper: dm-linear: Device lookup failed
[42949426.530000] device-mapper: error adding target to table
[42949426.540000] device-mapper: dm-linear: Device lookup failed
[42949426.540000] device-mapper: error adding target to table
[42949426.550000] device-mapper: dm-linear: Device lookup failed
[42949426.550000] device-mapper: error adding target to table
[42949426.550000] device-mapper: dm-linear: Device lookup failed
[42949426.550000] device-mapper: error adding target to table
[42949426.560000] device-mapper: dm-linear: Device lookup failed
[42949426.560000] device-mapper: error adding target to table
[42949426.560000] device-mapper: dm-linear: Device lookup failed
[42949426.560000] device-mapper: error adding target to table
[42949426.560000] device-mapper: dm-linear: Device lookup failed
[42949426.560000] device-mapper: error adding target to table
[42949426.560000] device-mapper: dm-linear: Device lookup failed
[42949426.560000] device-mapper: error adding target to table
[42949426.560000] device-mapper: dm-linear: Device lookup failed
[42949426.560000] device-mapper: error adding target to table
[42949426.560000] device-mapper: dm-linear: Device lookup failed
[42949426.560000] device-mapper: error adding target to table
[42949426.570000] device-mapper: dm-linear: Device lookup failed
[42949426.570000] device-mapper: error adding target to table
[42949426.570000] device-mapper: dm-linear: Device lookup failed
[42949426.570000] device-mapper: error adding target to table
[42949426.570000] device-mapper: dm-linear: Device lookup failed
[42949426.570000] device-mapper: error adding target to table
[42949426.570000] device-mapper: dm-linear: Device lookup failed
[42949426.570000] device-mapper: error adding target to table
[42949426.730000] kjournald starting.  Commit interval 5 seconds

``` 
The system however booted up completely. Are these errors serious?

Thanks,
Aravind.

---

