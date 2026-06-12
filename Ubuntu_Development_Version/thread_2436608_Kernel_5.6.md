---
title: "Kernel 5.6"
date: 2020-02-10
forum: Ubuntu Development Version
---

### Post by zika on 2020-02-10
```
:~$ uname -a Linux zika 5.6.0-999-generic #202002092108 SMP Mon Feb 10 02:13:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2020-02-10
O.K. I have been running it overnight on two computers. Done a kernel compile on one. O.K. so far.
Clean kernel compile seems to take about 20% longer than it did for kernel 5.5.

As of the last few days, some kernel source tree tools seem to now be broken on 20.04, as the python 3 only saga continues.
Example:

```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]scripts/diffconfig .config .config-5.6.0-050600rc1-lowlatency[/COLOR]
-bash: scripts/diffconfig: /usr/bin/python: bad interpreter: No such file or directory
```Indeed, that file now seems to be gone, whereas I had assumed the link would just change from python 2.7 to python 3.7 or whatever. This is from an impure 20.04 server, with packages installed that also pulled in old stuff. However, I am able to compile the kernel on this computer:

```
doug@s15:~/temp-k-git/linux$ ls -l -d /usr/bin/pyt*
lrwxrwxrwx 1 root root       9 Jan 11 07:56 /usr/bin/python2 -> python2.7
-rwxr-xr-x 1 root root 3710992 Jan 21 15:28 /usr/bin/python2.7
lrwxrwxrwx 1 root root       9 Oct 18 08:23 /usr/bin/python3 -> python3.7
-rwxr-xr-x 2 root root 5106768 Jan 16 10:23 /usr/bin/python3.7
-rwxr-xr-x 2 root root 5106768 Jan 16 10:23 /usr/bin/python3.7m
lrwxrwxrwx 1 root root      10 Oct 18 08:23 /usr/bin/python3m -> python3.7m

```For reference, here is an older 16.04 server:

```
doug@DOUG-64:~$ ls -l -d /usr/bin/pyt*
lrwxrwxrwx 1 root root       9 Nov 23  2017 [COLOR="#FF0000"]/usr/bin/python[/COLOR] -> python2.7
lrwxrwxrwx 1 root root       9 Nov 23  2017 /usr/bin/python2 -> python2.7
-rwxr-xr-x 1 root root 3492656 Oct  8 10:01 /usr/bin/python2.7
lrwxrwxrwx 1 root root       9 Mar 23  2016 /usr/bin/python3 -> python3.5
-rwxr-xr-x 2 root root 4452016 Oct  8 07:41 /usr/bin/python3.5
-rwxr-xr-x 2 root root 4452016 Oct  8 07:41 /usr/bin/python3.5m
lrwxrwxrwx 1 root root      10 Mar 23  2016 /usr/bin/python3m -> python3.5m

```

For reference, here is a pure 20.04 server, with no packages installed that still want to also pull in old stuff. However, I am unable to compile the kernel on this computer:
```
doug@s18:~$ ls -l -d /usr/bin/pyt*
lrwxrwxrwx 1 root root       9 Jan 23 16:27 /usr/bin/python3 -> python3.7
-rwxr-xr-x 2 root root 5106768 Jan 16 10:23 /usr/bin/python3.7
-rwxr-xr-x 2 root root 5106768 Jan 16 10:23 /usr/bin/python3.7m
-rwxr-xr-x 1 root root 5445344 Jan 16 10:22 /usr/bin/python3.8
lrwxrwxrwx 1 root root      10 Jan 23 16:27 /usr/bin/python3m -> python3.7m

```EDIT: I like to have the linkback trail for previous kernel Kernel rc series threads: [5.5]("https://ubuntuforums.org/showthread.php?t=2432815"), [5.4]("https://ubuntuforums.org/showthread.php?t=2428734"), [5.3]("https://ubuntuforums.org/showthread.php?t=2423441"), [5.2]("https://ubuntuforums.org/showthread.php?t=2419363"), [5.1]("https://ubuntuforums.org/showthread.php?t=2414938"), [5.0]("https://ubuntuforums.org/showthread.php?t=2409811"), [4.20]("https://ubuntuforums.org/showthread.php?t=2405365"), 4.19 ?, [4.18]("https://ubuntuforums.org/showthread.php?t=2394500"), [4.17]("https://ubuntuforums.org/showthread.php?t=2389561"), [4.16]("https://ubuntuforums.org/showthread.php?t=2384781"), [4.15]("https://ubuntuforums.org/showthread.php?t=2378956"), [4.14]("https://ubuntuforums.org/showthread.php?t=2371638").

---

### Post by Doug S on 2020-02-12
Seems that I can not run a KVM/QEMU type VM with the mainstream kernel running on the host. I get this:

```
doug@s15:/etc/libvirt/qemu$ virsh start serv-ff
error: Failed to start domain serv-ff
error: internal error: cannot load AppArmor profile 'libvirt-4492f2aa-d512-4fc2-ac27-7fdc87ce9b5a'
```

I went back a few mainline kernel versions, and even mainline kernel 5.4-rc1 has this issue. However, the stock Ubuntu 20.04 kernel works fine:

```
doug@s15:~$ virsh start serv-debian
Domain serv-debian started

doug@s15:~$ virsh start serv-ff
Domain serv-ff started

doug@s15:~$ uname -a
Linux s15 5.4.0-12-generic #15-Ubuntu SMP Tue Jan 21 15:12:29 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```This may or may not be related to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1745114").

---

### Post by corradoventu on 2020-03-02
Installed kernel 5.6.0-050600rc4-generic
```
corrado@corrado-p9-ff-0104-x:~$ cd Downloads
corrado@corrado-p9-ff-0104-x:~/Downloads$ ls linux*
linux-headers-5.6.0-050600rc4_5.6.0-050600rc4.202003012332_all.deb
linux-headers-5.6.0-050600rc4-generic_5.6.0-050600rc4.202003012332_amd64.deb
linux-image-unsigned-5.6.0-050600rc4-generic_5.6.0-050600rc4.202003012332_amd64.deb
linux-modules-5.6.0-050600rc4-generic_5.6.0-050600rc4.202003012332_amd64.deb
corrado@corrado-p9-ff-0104-x:~/Downloads$ sudo dpkg -i linux*.deb
```
I have a lot (more than 4.000) messages:
depmod: ERROR: ../libkmod/libkmod.c:515 lookup_builtin_file() could not open builtin file '/lib/modules/5.6.0-050600rc4-generic/modules.builtin.bin' 
but the install seems end correctly:
```
Setting up linux-image-unsigned-5.6.0-050600rc4-generic (5.6.0-050600rc4.202003012332) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.6.0-050600rc3-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.6.0-050600rc3-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.6.0-050600rc4-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.6.0-050600rc4-generic
Processing triggers for linux-image-unsigned-5.6.0-050600rc4-generic (5.6.0-050600rc4.202003012332) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.6.0-050600rc4-generic
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=c86a81fa-1d97-483c-99f8-318382983ed7)
I: Set the RESUME variable to override this.
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
```

but then the kernel boots correctly
```
corrado@corrado-p9-ff-0104-x:~$ inxi -Sx
System:
  Host: corrado-p9-ff-0104-x Kernel: 5.6.0-050600rc4-generic x86_64 bits: 64 
  compiler: gcc v: 9.2.1 Desktop: Gnome 3.34.3 
  Distro: Ubuntu 20.04 LTS (Focal Fossa) 
corrado@corrado-p9-ff-0104-x:~$
```

---

### Post by Doug S on 2020-03-02
> **corradoventu said:**
> 
I have a lot (more than 4.000) messages:
depmod: ERROR: ../libkmod/libkmod.c:515 lookup_builtin_file() could not open builtin file '/lib/modules/5.6.0-050600rc4-generic/modules.builtin.bin' 
but the install seems end correctly:
I get the same(well, i get the error 5601 times), and added effects me also to an existing [launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/kmod/+bug/1864436"). I also see an [upstream bug report]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=948257"). Hmmm... upstream says "fixed" for version 0.136 of initramfs-tools, but that seems to be what I have:

```
doug@s15:~/test_kernels$ dpkg -l | grep initramfs-tools
ii  initramfs-tools                                 0.136ubuntu1                        all          generic modular initramfs generator (automation)
ii  initramfs-tools-bin                             0.136ubuntu1                        amd64        binaries used by initramfs-tools
ii  initramfs-tools-core                            0.136ubuntu1                        all          generic modular initramfs generator (core tools)

```More investigation needed, but I don't have time now.

EDIT 1: If I compile the kernel myself, I get this message [COLOR="#FF0000"]5600 times[/COLOR]:
```
depmod: ERROR: ../libkmod/libkmod.c:515 lookup_builtin_file() could not open builtin file '/home/doug/temp-k-git/linux/debian/linux-image/lib/modules/5.6.0-rc4-stock/modules.builtin.bin'
```But the compile seemed to actually work fine and that file is there:

```
doug@s15:~/temp-k-git/linux$ ls -l /home/doug/temp-k-git/linux/debian/linux-image/lib/modules/5.6.0-rc4-stock/modules.builtin.bin
-rw-r--r-- 1 doug doug 12324 Mar  2 16:01 /home/doug/temp-k-git/linux/debian/linux-image/lib/modules/5.6.0-rc4-stock/modules.builtin.bin

```Hmmmm... now that I bother to look, the other file is there also:

```
doug@s15:~/temp-k-git/linux$ ls -l /lib/modules/5.6.0-050600rc4-lowlatency/modules.builtin.bin
-rw-r--r-- 1 root root 12324 Mar  2 08:38 /lib/modules/5.6.0-050600rc4-lowlatency/modules.builtin.bin

```By the way, the number of the times the error is listed seems to be once per module:
```
doug@s15:~/temp-k-git/linux$ locate /lib/modules/5.6.0-050600rc4-lowlatency | grep "\.ko" | wc -l
[COLOR="#FF0000"]5600[/COLOR]

```

EDIT 2: This is actually [the more related bug report]("https://bugs.launchpad.net/curtin/+bug/1864992"). I agree that the root issue is a regression on the kmod package, where 27-1ubuntu1 is bad and 26-3ubuntu1 is good.

---

