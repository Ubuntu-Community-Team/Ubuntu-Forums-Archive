---
title: "Ubuntu Server 16.04 and Highpoint RocketRAID 2680 SAS Controller"
date: 2016-08-02
forum: Server Platforms
---

### Post by Seb_Boffen on 2016-08-02
Did anyone get a Highpoint RocketRAID 2680 SAS Controller working on Ubuntu Server 16.04?
I've tried drivers: RR268x_Linux_Src_v2.1.1.0_14_02_24.tar.gz and RR268x-Linux-Src-v1.9-120817-1639.tar.gz the last one did not support the new kernel version, I was unable to edit the kernel settings within the driver to accept kernel 4.4
Maybe someone can help?

---

### Post by headward721 on 2016-10-07
Probably a few months late, but I seem to have got it working using the 2.1.1.0 drivers "Linux Open Source" drivers from High Point.  Usual disclaimer of taking backups, this is not supported by the vendor, blah blah blah apply.

Instructions below are borrowed heavily from [http://pastebin.com/54B86c0q](http://pastebin.com/54B86c0q)  and may not be 100% accurate as I didn't document as I was going and had to try a few things along the way, but should point you in the right direction.

# wget [www.highpoint-tech.com/BIOS_Driver/rr268x/linux/RR268x_Linux_Src_v2.1.1.0_14_02_24.tar.gz](www.highpoint-tech.com/BIOS_Driver/rr268x/linux/RR268x_Linux_Src_v2.1.1.0_14_02_24.tar.gz)
# tar -zxf RR268x-Linux-Src-v2.1.1.0_14_02_24.tar.gz
# sudo ./RR268x_Linux_Src_v2.1_14_02_24.bin

on line 26 of /usr/share/hptdrv/rr2680/product/rr2680/linux/config.c change

char driver_ver[] = "v2.1 (" __DATE__ " " __TIME__ ")";

to

char driver_ver[] = "v2.1";

and in /usr/share/hptdrv/rr2680/inc/linux_32mpa/Makefile.def at line 91 change

ifneq ($(MAJOR), 3)
ifneq ($(KERNEL_VER), 2.6)
ifneq ($(KERNEL_VER), 2.4)
$(error Only kernel 2.4/2.6/3.x is supported but you use $(KERNEL_VER))
endif
endif
endif

to

ifneq ($(MAJOR), 4)
ifneq ($(MAJOR), 3)
ifneq ($(KERNEL_VER), 2.6)
ifneq ($(KERNEL_VER), 2.4)
$(error Only kernel 2.4/2.6/3.x is supported but you use $(KERNEL_VER))
endif
endif
endif
endif

#cd /usr/share/hptdrv/rr2680
#nano dkms.conf
Then paste in the following:
MAKE="make -C product/rr2680/linux/ KERNELDIR=/lib/modules/${kernelver}/build"
CLEAN="make -C product/rr2680/linux/ clean"
BUILT_MODULE_NAME=rr2680
DEST_MODULE_LOCATION=/kernel/drivers/scsi/
BUILT_MODULE_LOCATION=product/rr2680/linux/
PACKAGE_NAME=rr2680
PACKAGE_VERSION=2.1
AUTOINSTALL=yes
REMAKE_INITRD=yes
 
Then save and close, and run the following:
# sudo cp -R . /usr/src/rr2680-2.1

I had to install dkms at this point
# sudo apt-get install dkms

# sudo dkms add -m rr2680 -v 2.1
# sudo dkms build -m rr2680 -v 2.1
# sudo dkms install -m rr2680 -v 2.1

After a reboot all my drives attached to the rr2680 were accessible again.

Thus far it seems to be working, reads and writes haven't blown anything up, but it's only been a couple of hours.  Did I mention having backups would be a good idea?

---

### Post by Seb_Boffen on 2016-10-11
Thank you I'll give it a try.

---

### Post by roman-b on 2016-10-12
Worked like a charm for me, thanks headward721!

---

### Post by alexemena on 2016-12-06
Thanks headward721,

For some reason the "real" source isn't published for the rr2680 like it is for the 264x. I had previously stumbled on this thread labeled for rr26xx but it doesn't work for the 2680.
[URL="https://help.ubuntu.com/community/RocketRaid#RocketRaid_26xx_Driver"]
https://help.ubuntu.com/community/RocketRaid#RocketRaid_26xx_Driver[/URL]

Combining the details from this post with the link above I modified the requisite config files & was able to build my drivers successfully.

here is a .zip with all the requisite details. I included a *very * basic read-me. Hope it helps someone.

---

### Post by alexemena on 2016-12-06
Thanks headward721,

For some reason the "real" source isn't published for the rr2680 like it is for the 264x. I had previously stumbled on this thread labeled for rr26xx but it doesn't work for the 2680.
[URL="https://help.ubuntu.com/community/RocketRaid#RocketRaid_26xx_Driver"]
https://help.ubuntu.com/community/RocketRaid#RocketRaid_26xx_Driver[/URL]

Combining the details from this post with the link above I modified the requisite config files & was able to build my drivers successfully.

here is a .zip with all the requisite details.
[ATTACH]272589[/ATTACH]

---

### Post by djxtreme on 2017-05-15
Trying to compile on Ubuntu 16.04 
```

[COLOR=#000000]sudo dkms build -m rr2680 -v 2.1[/COLOR]

```
and got the following errors:
```

cat /var/lib/dkms/rr2680/2.1/build/make.log

[COLOR=#000000]*Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.c:278:41: error: ‘struct gendisk’ has no member named ‘driverfs_dev’*[/COLOR]
[COLOR=#000000]*Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.c:283:35: error: ‘struct inode’ has no member named ‘i_mutex’; did you mean ‘i_mode’?*[/COLOR]
[COLOR=#000000]*mutex_lock(&bdev->bd_inode->i_mutex);*[/COLOR]
[COLOR=#000000]*Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.c:283:35: error: ‘struct inode’ has no member named ‘i_mutex’; did you mean ‘i_mode’?*[/COLOR]
[COLOR=#000000]*mutex_lock(&bdev->bd_inode->i_mutex);*[/COLOR]

```

The following patches can solve the problem:
[https://github.com/NP-Hardass/np-hardass-overlay/tree/master/sys-block/rocketraid62x/files](https://github.com/NP-Hardass/np-hardass-overlay/tree/master/sys-block/rocketraid62x/files)

```

cd /usr/src/rr2680-2.1
wget https://github.com/NP-Hardass/np-hardass-overlay/raw/master/sys-block/rocketraid62x/files/rocketraid62x-1.3.3-support-kernel-4.7-fix-inode-mutex.patch
wget https://github.com/NP-Hardass/np-hardass-overlay/raw/master/sys-block/rocketraid62x/files/rocketraid62x-1.3.3-support-kernel-4.8-fix-gendev-driverfs_dev-ref.patch
patch -p1 < ./rocketraid62x-1.3.3-support-kernel-4.7-fix-inode-mutex.patch
patch -p1 < ./rocketraid62x-1.3.3-support-kernel-4.8-fix-gendev-driverfs_dev-ref.patch

```

---

### Post by Seb_Boffen on 2018-04-28
Tried installing the same driver working on server 16.04 on 18.04 ended in error:

```
DKMS make.log for rr2680-2.1 for kernel 4.15.0-20-generic (x86_64) Fri Apr 27 02:03:09 CEST 2018
make: Entering directory
'/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux'
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-20-generic'
   CC [M]
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/os_linux.o
   CC [M]
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.o
   CC [M] /var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/div64.o
   CC [M]
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/hptinfo.o
   CC [M]
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/config.o
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/os_linux.c: 
In function &#8216;refresh_sd_flags&#8217;:
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/os_linux.c:367:41: 
error: &#8216;struct gendisk&#8217; has no member named &#8216;driverfs_dev&#8217;
        if (bdev->bd_disk && 
bdev->bd_disk->driverfs_dev==&SDptr->sdev_gendev) {
                                          ^~
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/os_linux.c:372:37: 
error: &#8216;struct inode&#8217; has no member named &#8216;i_mutex&#8217;; did you mean &#8216;i_mode&#8217;?
          mutex_lock(&bdev->bd_inode->i_mutex);
                                      ^~~~~~~
                                      i_mode
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/os_linux.c:378:39: 
error: &#8216;struct inode&#8217; has no member named &#8216;i_mutex&#8217;; did you mean &#8216;i_mode&#8217;?
          mutex_unlock(&bdev->bd_inode->i_mutex);
                                        ^~~~~~~
                                        i_mode
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/os_linux.c: 
In function &#8216;os_request_timer&#8217;:
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/os_linux.c:639:27: 
error: assignment from incompatible pointer type [-Werror=incompatible-pointer-types]
   vbus_ext->timer.function = os_timer_for_ldm;
                            ^
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/os_linux.c:640:17: 
error: &#8216;struct timer_list&#8217; has no member named &#8216;data&#8217;
   vbus_ext->timer.data = (unsigned long)vbus_ext;
                  ^
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.c: 
In function &#8216;hpt_detect&#8217;:
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.c:322:3: 
error: implicit declaration of function &#8216;init_timer&#8217;; did you mean &#8216;init_timers&#8217;? [-Werror=implicit-function-declaration]
    init_timer(&vbus_ext->timer);
    ^~~~~~~~~~
    init_timers
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/os_linux.o' 
failed
make[2]: ***
[/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/os_linux.o]
Error 1
make[2]: *** Waiting for unfinished jobs....
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.c: 
In function &#8216;hpt_flush_vdev&#8217;:
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.c:1626:8: 
error: &#8216;struct timer_list&#8217; has no member named &#8216;data&#8217;
    timer.data = (HPT_UPTR)&sem;
         ^
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.c:1627:18: 
error: assignment from incompatible pointer type [-Werror=incompatible-pointer-types]
    timer.function = cmd_timeout_sem;
                   ^
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.c: 
In function &#8216;__hpt_do_ioctl&#8217;:
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.c:1902:8: 
error: &#8216;struct timer_list&#8217; has no member named &#8216;data&#8217;
    timer.data = (HPT_UPTR)&sem;
         ^
/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.c:1903:18: 
error: assignment from incompatible pointer type [-Werror=incompatible-pointer-types]
    timer.function = hpt_ioctl_timeout;
                   ^
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.o' 
failed
make[2]: ***
[/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build/osm_linux.o]
Error 1
Makefile:1552: recipe for target
'_module_/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build' failed
make[1]: ***
[_module_/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux/.build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-20-generic'
../../../inc/linux_32mpa/Makefile.def:106: recipe for target 'rr2680.ko' 
failed
make: *** [rr2680.ko] Error 2
make: Leaving directory
'/var/lib/dkms/rr2680/2.1/build/product/rr2680/linux'
```
 
Would somebody assist?

---

### Post by drw06g0w7-frank on 2018-08-21
Given the elapsed time I suspect that you have solved this by now.

I fixed this problem for rr640L. It took me a while to figure out what to do, but it is not too difficult. Just glancing the code looks very similar to what you listed here. For example, my os_linux.c has the changes:

 #if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
< static void os_timer_for_ldm(struct timer_list *t)
< #else
640d632
< #endif
642,644d633
< #if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
<         PVBUS_EXT vbus_ext = from_timer(vbus_ext, t, timer);
< #else
646d634
< #endif
662d649
< #if LINUX_VERSION_CODE < KERNEL_VERSION(4, 15, 0)
664d650
< #endif

---

### Post by ignalex on 2018-10-29
have exactly the same. 
if anyone ported to Ubuntu bionic pls share how ...

---

### Post by ignalex on 2018-10-29
[h=2]Re: Ubuntu Server 16.04 and Highpoint RocketRAID 2680 SAS Controller[/h][COLOR=#000000][INDENT]Given the elapsed time I suspect that you have solved this by now.

I fixed this problem for rr640L. It took me a while to figure out what to do, but it is not too difficult. Just glancing the code looks very similar to what you listed here. For example, my os_linux.c has the changes:

#if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
< static void os_timer_for_ldm(struct timer_list *t)
< #else
640d632
< #endif
642,644d633
< #if LINUX_VERSION_CODE >= KERNEL_VERSION(4, 15, 0)
< PVBUS_EXT vbus_ext = from_timer(vbus_ext, t, timer);
< #else
646d634
< #endif
662d649
< #if LINUX_VERSION_CODE < KERNEL_VERSION(4, 15, 0)
664d650
< #endif[/INDENT]
[/COLOR]

hi mate, 
looks your approach could be the one I need. but can't really get the right understanding from the code you posted. would you mind posting it as a patch or which lines to replace / add? 
thanks 
Alex

---

