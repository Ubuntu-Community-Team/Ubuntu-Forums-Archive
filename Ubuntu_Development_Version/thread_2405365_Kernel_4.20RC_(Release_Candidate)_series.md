---
title: "Kernel 4.20RC (Release Candidate) series"
date: 2018-11-05
forum: Ubuntu Development Version
---

### Post by Doug S on 2018-11-05
We like to have one thread for every kernel release cycle series. This one is for the kernel 4.20 release candidate series.

While 4.20-rc1 is available now from [kernel.org]("https://www.kernel.org/"), it seems the [Ubuntu PPA builds]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.20-rc1/") are broken again, so you'll have to wait if you get from there.

I've been running it for just a few minutes, so far. The main thing I have noticed between kernels 4.18, 4.19 and just a bit before 4.20-rc1 is a significant variation in a 1 core pipe test, going from 4.8 to 5.2 to 4.2 uSeconds per loop, respectively. I'll check the 4.2 uSec/loop number with the actual 4.20-rc1 kernel soon.

EDIT: Kernel 4.20-rc1 seems to be about 4.45 uSec/loop for the 1 core pipe test.

---

### Post by zika on 2018-11-05
```
:~$ uname -a
Linux zika 4.20.0-rc1-acso #1 SMP Mon Nov 5 00:27:50 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2018-11-11
The daily mainline kernel build is still broken. I went on IRC and notified them.

---

### Post by fyfe54 on 2018-11-11
4.20rc2 appeared in Mainline.  It failed to build....

---

### Post by Doug S on 2018-11-12
> **fyfe54 said:**
> 4.20rc2 appeared in Mainline.  It failed to build....It has been fixed. There is now a complete [kernel 4.20-rc2 available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.20-rc2/").

---

### Post by fyfe54 on 2018-11-12
Thanks.  I have it, installed and running.   So far, so good....

---

### Post by corradoventu on 2018-11-20
Installation of 4.20rc3 on my Ubuntu 19.04 caused inconsistency to my root filesystem so i was forced to run fsck manually. After fsck now system runs smootly.
corrado@corrado-p13-dd-1107-x:~$ uname -a
Linux corrado-p13-dd-1107-x 4.20.0-042000rc3-generic #201811182231 SMP Sun Nov 18 22:33:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-p13-dd-1107-x:~$

---

### Post by Doug S on 2018-11-20
> **corradoventu said:**
> Installation of 4.20rc3 on my Ubuntu 19.04 caused inconsistency to my root filesystem so i was forced to run fsck manually. After fsck now system runs smootly.
corrado@corrado-p13-dd-1107-x:~$ uname -a
Linux corrado-p13-dd-1107-x 4.20.0-042000rc3-generic #201811182231 SMP Sun Nov 18 22:33:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-p13-dd-1107-x:~$Everything has been fine on my main test server, which is still on 16.04.5 (because I do not like netplan). Is 4.20-rc3 your first test of the 4.20-rc series? i.e. did you have any issues with -rc1 or -rc2? Or just didn't try them?

---

### Post by corradoventu on 2018-11-21
On the same partition I had installed also 4.20rc2 and I had no problems.

---

### Post by corradoventu on 2018-11-21
the install of -rc3 was run without problems
```
corrado@corrado-p13-dd-1107-x:~$ cd Downloads
corrado@corrado-p13-dd-1107-x:~/Downloads$ ls
228472349-wallpaper-bears.jpg
linux-headers-4.20.0-042000rc3_4.20.0-042000rc3.201811182231_all.deb
linux-headers-4.20.0-042000rc3-generic_4.20.0-042000rc3.201811182231_amd64.deb
linux-image-unsigned-4.20.0-042000rc3-generic_4.20.0-042000rc3.201811182231_amd64.deb
linux-modules-4.20.0-042000rc3-generic_4.20.0-042000rc3.201811182231_amd64.deb
corrado@corrado-p13-dd-1107-x:~/Downloads$ sudo dpkg -i linux*.deb
[sudo] password for corrado: 
Selecting previously unselected package linux-headers-4.20.0-042000rc3.
(Reading database ... 245409 files and directories currently installed.)
Preparing to unpack linux-headers-4.20.0-042000rc3_4.20.0-042000rc3.201811182231_all.deb ...
Unpacking linux-headers-4.20.0-042000rc3 (4.20.0-042000rc3.201811182231) ...
Selecting previously unselected package linux-headers-4.20.0-042000rc3-generic.
Preparing to unpack linux-headers-4.20.0-042000rc3-generic_4.20.0-042000rc3.201811182231_amd64.deb ...
Unpacking linux-headers-4.20.0-042000rc3-generic (4.20.0-042000rc3.201811182231) ...
Selecting previously unselected package linux-image-unsigned-4.20.0-042000rc3-generic.
Preparing to unpack linux-image-unsigned-4.20.0-042000rc3-generic_4.20.0-042000rc3.201811182231_amd64.deb ...
Unpacking linux-image-unsigned-4.20.0-042000rc3-generic (4.20.0-042000rc3.201811182231) ...
Selecting previously unselected package linux-modules-4.20.0-042000rc3-generic.
Preparing to unpack linux-modules-4.20.0-042000rc3-generic_4.20.0-042000rc3.201811182231_amd64.deb ...
Unpacking linux-modules-4.20.0-042000rc3-generic (4.20.0-042000rc3.201811182231) ...
Setting up linux-headers-4.20.0-042000rc3 (4.20.0-042000rc3.201811182231) ...
Setting up linux-headers-4.20.0-042000rc3-generic (4.20.0-042000rc3.201811182231) ...
Setting up linux-modules-4.20.0-042000rc3-generic (4.20.0-042000rc3.201811182231) ...
Setting up linux-image-unsigned-4.20.0-042000rc3-generic (4.20.0-042000rc3.201811182231) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-4.18.0-11-generic
I: /initrd.img.old is now a symlink to boot/initrd.img-4.18.0-11-generic
I: /vmlinuz is now a symlink to boot/vmlinuz-4.20.0-042000rc3-generic
I: /initrd.img is now a symlink to boot/initrd.img-4.20.0-042000rc3-generic
Processing triggers for linux-image-unsigned-4.20.0-042000rc3-generic (4.20.0-042000rc3.201811182231) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.20.0-042000rc3-generic
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=c86a81fa-1d97-483c-99f8-318382983ed7)
I: Set the RESUME variable to override this.
/etc/kernel/postinst.d/zz-update-grub:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.20.0-042000rc3-generic
Found initrd image: /boot/initrd.img-4.20.0-042000rc3-generic
Found linux image: /boot/vmlinuz-4.20.0-042000rc2-generic
Found initrd image: /boot/initrd.img-4.20.0-042000rc2-generic
Found linux image: /boot/vmlinuz-4.19.1-041901-generic
Found initrd image: /boot/initrd.img-4.19.1-041901-generic
Found linux image: /boot/vmlinuz-4.18.0-11-generic
Found initrd image: /boot/initrd.img-4.18.0-11-generic
Found linux image: /boot/vmlinuz-4.18.0-10-generic
Found initrd image: /boot/initrd.img-4.18.0-10-generic
Found Ubuntu 18.10 (18.10) on /dev/sda3
Found Ubuntu 16.04.5 LTS (16.04) on /dev/sda4
Found Ubuntu 17.10 (17.10) on /dev/sda5
Found Ubuntu Disco Dingo (development branch) (19.04) on /dev/sda6
Found Ubuntu Disco Dingo (development branch) (19.04) on /dev/sda7
Found Ubuntu 18.04.1 LTS (18.04) on /dev/sda8
Found Ubuntu 18.10 (18.10) on /dev/sda9
Adding boot menu entry for EFI firmware configuration
done
corrado@corrado-p13-dd-1107-x:~/Downloads$ 

``` but at restart i had this message:

---

### Post by corradoventu on 2018-11-30
Also 4.20RC4 seems ok```
corrado@corrado-p13-dd-1107-x:~$ inxi -CSx
System:    Host: corrado-p13-dd-1107-x Kernel: 4.20.0-042000rc4-generic x86_64 bits: 64 compiler: gcc v: 8.2.0 
           Desktop: Gnome 3.30.1 Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
corrado@corrado-p13-dd-1107-x:~$ 

```

---

### Post by corradoventu on 2018-12-04
also rc5
```
corrado@corrado-p13-dd-1107-x:~$ inxi -SCx
System:
  Host: corrado-p13-dd-1107-x Kernel: 4.20.0-042000rc5-generic x86_64 
  bits: 64 compiler: gcc v: 8.2.0 Desktop: Gnome 3.30.1 
  Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:
  Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
  Speed: 1397 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 3018 2: 2725 
  3: 3115 4: 2559 
corrado@corrado-p13-dd-1107-x:~$ 

```

---

### Post by Doug S on 2018-12-05
Yes, -rc5 seems O.K. for me so far. I missed -rc4, due to some testing where I did not want to have any changes to my baseline reference.

---

### Post by corradoventu on 2018-12-17
Also -rc7 seems ok```
corrado@corrado-p13-dd-1107-x:~/Downloads$ sudo dpkg -i linux*.deb
[sudo] password for corrado: 
Selecting previously unselected package linux-headers-4.20.0-042000rc7.
(Reading database ... 394145 files and directories currently installed.)
Preparing to unpack linux-headers-4.20.0-042000rc7_4.20.0-042000rc7.201812161930_all.deb ...
Unpacking linux-headers-4.20.0-042000rc7 (4.20.0-042000rc7.201812161930) ...
Selecting previously unselected package linux-headers-4.20.0-042000rc7-generic.
Preparing to unpack linux-headers-4.20.0-042000rc7-generic_4.20.0-042000rc7.201812161930_amd64.deb ...
Unpacking linux-headers-4.20.0-042000rc7-generic (4.20.0-042000rc7.201812161930) ...
Selecting previously unselected package linux-image-unsigned-4.20.0-042000rc7-generic.
Preparing to unpack linux-image-unsigned-4.20.0-042000rc7-generic_4.20.0-042000rc7.201812161930_amd64.deb ...
Unpacking linux-image-unsigned-4.20.0-042000rc7-generic (4.20.0-042000rc7.201812161930) ...
Selecting previously unselected package linux-modules-4.20.0-042000rc7-generic.
Preparing to unpack linux-modules-4.20.0-042000rc7-generic_4.20.0-042000rc7.201812161930_amd64.deb ...
Unpacking linux-modules-4.20.0-042000rc7-generic (4.20.0-042000rc7.201812161930) ...
Setting up linux-headers-4.20.0-042000rc7 (4.20.0-042000rc7.201812161930) ...
Setting up linux-headers-4.20.0-042000rc7-generic (4.20.0-042000rc7.201812161930) ...
Setting up linux-modules-4.20.0-042000rc7-generic (4.20.0-042000rc7.201812161930) ...
Setting up linux-image-unsigned-4.20.0-042000rc7-generic (4.20.0-042000rc7.201812161930) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-4.20.0-042000rc6-generic
I: /initrd.img.old is now a symlink to boot/initrd.img-4.20.0-042000rc6-generic
I: /vmlinuz is now a symlink to boot/vmlinuz-4.20.0-042000rc7-generic
I: /initrd.img is now a symlink to boot/initrd.img-4.20.0-042000rc7-generic
Processing triggers for linux-image-unsigned-4.20.0-042000rc7-generic (4.20.0-042000rc7.201812161930) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.20.0-042000rc7-generic
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=c86a81fa-1d97-483c-99f8-318382983ed7)
I: Set the RESUME variable to override this.
/etc/kernel/postinst.d/unattended-upgrades:
grep: /var/run/reboot-required.pkgs: No such file or directory
/etc/kernel/postinst.d/zz-update-grub:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.20.0-042000rc7-generic
Found initrd image: /boot/initrd.img-4.20.0-042000rc7-generic
Found linux image: /boot/vmlinuz-4.20.0-042000rc6-generic
Found initrd image: /boot/initrd.img-4.20.0-042000rc6-generic
Found linux image: /boot/vmlinuz-4.20.0-042000rc5-generic
Found initrd image: /boot/initrd.img-4.20.0-042000rc5-generic
Found linux image: /boot/vmlinuz-4.20.0-042000rc4-generic
Found initrd image: /boot/initrd.img-4.20.0-042000rc4-generic
Found linux image: /boot/vmlinuz-4.20.0-042000rc3-generic
Found initrd image: /boot/initrd.img-4.20.0-042000rc3-generic
Found linux image: /boot/vmlinuz-4.20.0-042000rc2-generic
Found initrd image: /boot/initrd.img-4.20.0-042000rc2-generic
Found linux image: /boot/vmlinuz-4.19.1-041901-generic
Found initrd image: /boot/initrd.img-4.19.1-041901-generic
Found linux image: /boot/vmlinuz-4.18.0-11-generic
Found initrd image: /boot/initrd.img-4.18.0-11-generic
Found linux image: /boot/vmlinuz-4.18.0-10-generic
Found initrd image: /boot/initrd.img-4.18.0-10-generic
Found Ubuntu 18.10 (18.10) on /dev/sda3
Found Ubuntu 16.04.5 LTS (16.04) on /dev/sda4
Found Ubuntu Disco Dingo (development branch) (19.04) on /dev/sda5
Found Ubuntu Disco Dingo (development branch) (19.04) on /dev/sda6
Found Ubuntu Disco Dingo (development branch) (19.04) on /dev/sda7
Found Ubuntu 18.04.1 LTS (18.04) on /dev/sda8
Found Ubuntu 18.10 (18.10) on /dev/sda9
Adding boot menu entry for EFI firmware configuration
done
corrado@corrado-p13-dd-1107-x:~/Downloads$ 

```

---

### Post by corradoventu on 2018-12-24
Today i installed last arrived kernel from [https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.20/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.20/) and now i'm using it without problems 
```
corrado@corrado-p13-dd-1107-x:~$ uname -a
Linux corrado-p13-dd-1107-x 4.20.0-042000-generic #201812232030 SMP Mon Dec 24 01:32:58 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-p13-dd-1107-x:~$ 
```
so i decided to remove some old ones. listing the kernels i have in boot directory I found something that I do not understand: I have all kernels fron -rc2 to -rc7 but retpoline only from -rc2 to -rc5.
can someone explain?
thanks```
corrado@corrado-p13-dd-1107-x:~$ ls /boot
abi-4.18.0-10-generic            initrd.img-4.18.0-11-generic         System.map-4.18.0-11-generic
abi-4.18.0-11-generic            initrd.img-4.19.0-9-generic          System.map-4.19.0-9-generic
abi-4.19.1-041901-generic        initrd.img-4.19.1-041901-generic     System.map-4.19.1-041901-generic
abi-4.20.0-042000rc2-generic     initrd.img-4.20.0-042000-generic     System.map-4.20.0-042000-generic
abi-4.20.0-042000rc3-generic     initrd.img-4.20.0-042000rc2-generic  System.map-4.20.0-042000rc2-generic
abi-4.20.0-042000rc4-generic     initrd.img-4.20.0-042000rc3-generic  System.map-4.20.0-042000rc3-generic
abi-4.20.0-042000rc5-generic     initrd.img-4.20.0-042000rc4-generic  System.map-4.20.0-042000rc4-generic
config-4.18.0-10-generic         initrd.img-4.20.0-042000rc5-generic  System.map-4.20.0-042000rc5-generic
config-4.18.0-11-generic         initrd.img-4.20.0-042000rc6-generic  System.map-4.20.0-042000rc6-generic
config-4.19.0-9-generic          initrd.img-4.20.0-042000rc7-generic  System.map-4.20.0-042000rc7-generic
config-4.19.1-041901-generic     memtest86+.bin                       vmlinuz-4.18.0-10-generic
config-4.20.0-042000-generic     memtest86+.elf                       vmlinuz-4.18.0-11-generic
config-4.20.0-042000rc2-generic  memtest86+_multiboot.bin             vmlinuz-4.19.0-9-generic
config-4.20.0-042000rc3-generic  retpoline-4.18.0-10-generic          vmlinuz-4.19.1-041901-generic
config-4.20.0-042000rc4-generic  retpoline-4.18.0-11-generic          vmlinuz-4.20.0-042000-generic
config-4.20.0-042000rc5-generic  retpoline-4.19.1-041901-generic      vmlinuz-4.20.0-042000rc2-generic
config-4.20.0-042000rc6-generic  retpoline-4.20.0-042000rc2-generic   vmlinuz-4.20.0-042000rc3-generic
config-4.20.0-042000rc7-generic  retpoline-4.20.0-042000rc3-generic   vmlinuz-4.20.0-042000rc4-generic
efi                              retpoline-4.20.0-042000rc4-generic   vmlinuz-4.20.0-042000rc5-generic
grub                             retpoline-4.20.0-042000rc5-generic   vmlinuz-4.20.0-042000rc6-generic
initrd.img-4.18.0-10-generic     System.map-4.18.0-10-generic         vmlinuz-4.20.0-042000rc7-generic
corrado@corrado-p13-dd-1107-x:~$ 

```
but retpoline seems activated for my kernel:```
corrado@corrado-p13-dd-1107-x:~$ uname -a
Linux corrado-p13-dd-1107-x 4.20.0-042000-generic #201812232030 SMP Mon Dec 24 01:32:58 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-p13-dd-1107-x:~$ cat /sys/devices/system/cpu/vulnerabilities/spectre_v2
Mitigation: Full generic retpoline, IBPB: conditional, IBRS_FW, STIBP: conditional, RSB filling
corrado@corrado-p13-dd-1107-x:~$ 
```

---

### Post by Doug S on 2018-12-24
> **corradoventu said:**
> Today i installed last arrived kernel from [https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.20/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.20/) and now i'm using it without problems 
```
corrado@corrado-p13-dd-1107-x:~$ uname -a
Linux corrado-p13-dd-1107-x 4.20.0-042000-generic #201812232030 SMP Mon Dec 24 01:32:58 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-p13-dd-1107-x:~$ 
```
so i decided to remove some old ones. listing the kernels i have in boot directory I found something that I do not understand: I have all kernels fron -rc2 to -rc7 but retpoline only from -rc2 to -rc5.
can someone explain?Due some continued testing I am doing, I am still on kernel 4.20-rc5. As you may or may not know, I always compile my own test kernels, and I don't have those file at all for them. I have spent time attempting to figure out what they are for, and have made no progress (I am out of time for this now). I have 36 kernels installed at the moment, but only those files for these 5, which are the only ones I didn't compile myself (well, since this retpoline stuff started at least):

```
doug@s15:~$ ls -l /boot/retp*
-rw-r--r-- 1 root root 15945 Apr  1  2018 /boot/retpoline-4.16.0-041600-lowlatency
-rw-r--r-- 1 root root    17 Oct 22 15:30 /boot/retpoline-4.19.0-041900-lowlatency
-rw-r--r-- 1 root root   255 Oct 24 08:31 /boot/retpoline-4.4.0-139-generic
-rw-r--r-- 1 root root   255 Nov 14 14:11 /boot/retpoline-4.4.0-140-generic
-rw-r--r-- 1 root root   255 Dec  5 06:08 /boot/retpoline-4.4.0-141-generic

```

---

