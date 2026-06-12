---
title: "Kernel update / Install issues"
date: 2020-07-27
forum: Server Platforms
---

### Post by wjhildreth on 2020-07-27
I am running Ubuntu 14.04.6 server.  I am having an issue that I cannot solve and hope someone here can provide me a little direction.  I have a failed kernel install and failed dependencies.

When running a df -h /boot I get the following information:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       237M   45M  180M  20% /boot
```

This leads me to believe I have room to install a kernel.

Doing a ls on on the /boot directory yields the following:

```
root@mail:/boot# ls -l
total 36651
-rw-r--r-- 1 root root  1169204 Aug 20  2018 abi-3.13.0-157-generic
-rw-r--r-- 1 root root   166094 Aug 20  2018 config-3.13.0-157-generic
-rw-r--r-- 1 root root   166221 May  9  2019 config-3.13.0-170-generic
drwxr-xr-x 5 root root     1024 May 13  2019 grub
-rw-r--r-- 1 root root 22594985 Aug 27  2018 initrd.img-3.13.0-157-generic
drwx------ 2 root root    12288 Sep 10  2014 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-r--r-- 1 root root      254 Aug 20  2018 retpoline-3.13.0-157-generic
-rw------- 1 root root  3416014 Aug 20  2018 System.map-3.13.0-157-generic
-rw------- 1 root root  3418683 May  9  2019 System.map-3.13.0-170-generic
-rw------- 1 root root  5892240 Aug 20  2018 vmlinuz-3.13.0-157-generic
root@mail:/boot# 

```

When installing kernel 3.13.0.170 it failed with an error message about running out of disk space.

When I run dpkg --audit I get the following:

```
root@mail:/boot# dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-headers-3.13.0-170 Header files related to Linux kernel version 3.13.0
 linux-modules-extra-3.13.0-170-generic Linux kernel extra modules for version 
 linux-modules-3.13.0-170-generic Linux kernel extra modules for version 3.13.0
 linux-headers-3.13.0-170-generic Linux kernel headers for version 3.13.0 on 64
 linux-image-generic  Generic Linux kernel image
 linux-generic        Complete Generic Linux kernel and headers
 linux-headers-generic Generic Linux kernel headers

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      tools for generating an initramfs

The following packages are missing the list control file in the
database, they need to be reinstalled:
 linux-image-3.13.0-169-generic Signed kernel image generic

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 linux-image-3.13.0-169-generic Signed kernel image generic

root@mail:/boot# 

```

if I run apt-get upgrade I get:

```
root@mail:/boot# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-3.13.0-170-generic but it is not installed or
                                linux-image-unsigned-3.13.0-170-generic but it is not installed
 linux-modules-extra-3.13.0-170-generic : Depends: linux-image-3.13.0-170-generic but it is not installed or
                                                   linux-image-unsigned-3.13.0-170-generic but it is not installed
E: Unmet dependencies. Try using -f.
root@mail:/boot# 

```

and when I run apt-get -f intsall I get the following:

```
root@mail:/boot# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-169 linux-headers-3.13.0-169-generic
  linux-image-3.13.0-169-generic linux-modules-3.13.0-169-generic
  linux-modules-extra-3.13.0-169-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-170-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-170-generic
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
8 not fully installed or removed.
Need to get 0 B/5,843 kB of archives.
After this operation, 5,951 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
dpkg: warning: files list file for package 'linux-image-3.13.0-169-generic' missing; assuming package has no files currently installed
(Reading database ... 162500 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-170-generic_3.13.0-170.220_amd64.deb ...
Unpacking linux-image-3.13.0-170-generic (3.13.0-170.220) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-170-generic_3.13.0-170.220_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-170-generic' to '/boot/vmlinuz-3.13.0-170-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mail:/boot# 

```

Can anyone point me in the direction of how to resolve this, please?

Regards,

Joe

---

### Post by monkeybrain20122 on 2020-07-27
Just uninstall some of the old kernels to free up the /boot partition.

---

### Post by wjhildreth on 2020-07-27
There is only one working kernel installed, 3.13.0-157 and one half installed failed kernel.  3.13.0-170

The /boot partition shows 180M free, 45M used

Joe

---

### Post by Bashing-om on 2020-07-27
wjhildreth - ouch !

I be that harbinger of Ill news:
> 
Ubuntu 14.04 LTS (Trusty Tahr) was the 20th release of Ubuntu. !End-of-life was April 25th, 2019. Paid 
               support (ESM) is available.


The software repository no longer exists as you once knew it.
I highly recommend that you upgrade to the current LTS 20.04.

[INDENT][INDENT]nothing last forever.
[/INDENT][/INDENT]

---

### Post by wjhildreth on 2020-07-28
I understand that.  I am just trying to make the machine work in a normal manner before migrating to a new one.  Thank you nonetheless.  :-)

Joe

---

### Post by Bashing-om on 2020-07-28
wjhildreth; Well -

> 
trying to make the machine work in a normal manner before migrating 


In that case - one can change the sources to "old-releases.ubuntu.com" and then see what it will take to install:
linux-image-3.13.0-169-generic
Signed kernel image generic

Check ALL available disk space as well as inodes:
```

df -h
df -i

```
and - the state of what kernels are installed:
```

dpkg -l | grep linux- 

```

Where we will seek a status of "ii" -> desired == (I)nstalled; status == (i)nstalled for only the current booted kernel and one other.
```

uname -r

``` to verify that booting kernel.

You are in for a long hard road - and there has been many changes to the system in 20,04 from that of 14.04 - and lots of time and bandwidth.

Be aware that 18.04 + has systemd as the initiate system, Many of your 14.04 upstart scrips will not migrate and there is no telling what all else may break.

The LTS path from 14.04 is via 16.04 (EOL - more pain)-> 18.04 ( still with support until April 2023 ) -> 20.04

I have done it - 
[INDENT][INDENT]I can attest it is possible
[/INDENT][/INDENT]

---

### Post by LHammonds on 2020-07-29
I would just setup a 20.04 server from scratch and make it work how you want and migrate the data over.

If you only have one physical box, consider setting up the server on your PC using a virtual environment like Oracle VirtualBox.

Once you can get a virtual version of it operating and working with your data, you should be able to wipe the old server, install the new OS and transfer the data from the 20.04 version you have working on a virtual environment.

LHammonds

---

