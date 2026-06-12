---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-11-14
forum: Texas Team - US
---

### Post by michael331 on 2015-11-14
I'm trying to update via putty and keep getting the following error when running apt-get upgrade:
```
Errors were encountered while processing: /var/cache/apt/archives/linux-image-3.13.0-68-generic_3.13.0-68.111_amd64.deb
 /var/cache/apt/archives/linux-image-3.13.0-67-generic_3.13.0-67.110_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
The output of sudo dpkg --configure -a is:
```
michael@ubuntu:~$ sudo dpkg --configure -adpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-68-generic:
 linux-image-extra-3.13.0-68-generic depends on linux-image-3.13.0-68-generic; however:
  Package linux-image-3.13.0-68-generic is not installed.


dpkg: error processing package linux-image-extra-3.13.0-68-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-libc-dev:amd64 (3.13.0-67.110) ...
Setting up libnspr4:amd64 (2:4.10.10-0ubuntu0.14.04.1) ...
Setting up linux-image-3.13.0-65-generic (3.13.0-65.106) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-65-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-65-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-65-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-65-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-68-generic; however:
  Package linux-image-3.13.0-68-generic is not installed.
 linux-image-generic depends on linux-image-extra-3.13.0-68-generic; however:
  Package linux-image-extra-3.13.0-68-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-67-generic:
 linux-image-extra-3.13.0-67-generic depends on linux-image-3.13.0-67-generic; however:
  Package linux-image-3.13.0-67-generic is not installed.


dpkg: error processing package linux-image-extra-3.13.0-67-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.13.0-66-generic (3.13.0-66.108) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.13.0-65-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-66-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-66-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-66-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-66-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.68.74); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.13.0-68 (3.13.0-68.111) ...
Setting up linux-headers-3.13.0-67 (3.13.0-67.110) ...
Setting up firefox (42.0+build2-0ubuntu0.14.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/firefox ...
Please restart all running instances of firefox, or you will experience problems.
Setting up linux-headers-3.13.0-67-generic (3.13.0-67.110) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
Setting up linux-headers-3.13.0-68-generic (3.13.0-68.111) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-65-generic:
 linux-image-extra-3.13.0-65-generic depends on linux-image-3.13.0-65-generic; however:
  Package linux-image-3.13.0-65-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.13.0-65-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-66-generic:
 linux-image-extra-3.13.0-66-generic depends on linux-image-3.13.0-66-generic; however:
  Package linux-image-3.13.0-66-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.13.0-66-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-generic (3.13.0.68.74) ...
Setting up libnss3-nssdb (2:3.19.2.1-0ubuntu0.14.04.1) ...
Setting up libnss3:amd64 (2:3.19.2.1-0ubuntu0.14.04.1) ...
Setting up libnss3-1d:amd64 (2:3.19.2.1-0ubuntu0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Errors were encountered while processing:
 linux-image-extra-3.13.0-68-generic
 linux-image-3.13.0-65-generic
 linux-image-generic
 linux-image-extra-3.13.0-67-generic
 linux-image-3.13.0-66-generic
 linux-generic
 linux-image-extra-3.13.0-65-generic
 linux-image-extra-3.13.0-66-generic

```
The output of sudo dpkg --configure -a is:
```
michael@ubuntu:~$ sudo dpkg --configure -adpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-68-generic:
 linux-image-extra-3.13.0-68-generic depends on linux-image-3.13.0-68-generic; however:
  Package linux-image-3.13.0-68-generic is not installed.


dpkg: error processing package linux-image-extra-3.13.0-68-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-libc-dev:amd64 (3.13.0-67.110) ...
Setting up libnspr4:amd64 (2:4.10.10-0ubuntu0.14.04.1) ...
Setting up linux-image-3.13.0-65-generic (3.13.0-65.106) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-65-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-65-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-65-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-65-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-68-generic; however:
  Package linux-image-3.13.0-68-generic is not installed.
 linux-image-generic depends on linux-image-extra-3.13.0-68-generic; however:
  Package linux-image-extra-3.13.0-68-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-67-generic:
 linux-image-extra-3.13.0-67-generic depends on linux-image-3.13.0-67-generic; however:
  Package linux-image-3.13.0-67-generic is not installed.


dpkg: error processing package linux-image-extra-3.13.0-67-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.13.0-66-generic (3.13.0-66.108) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.13.0-65-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-66-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-66-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-66-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-66-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.68.74); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.13.0-68 (3.13.0-68.111) ...
Setting up linux-headers-3.13.0-67 (3.13.0-67.110) ...
Setting up firefox (42.0+build2-0ubuntu0.14.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/firefox ...
Please restart all running instances of firefox, or you will experience problems.
Setting up linux-headers-3.13.0-67-generic (3.13.0-67.110) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
Setting up linux-headers-3.13.0-68-generic (3.13.0-68.111) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-65-generic:
 linux-image-extra-3.13.0-65-generic depends on linux-image-3.13.0-65-generic; however:
  Package linux-image-3.13.0-65-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.13.0-65-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-66-generic:
 linux-image-extra-3.13.0-66-generic depends on linux-image-3.13.0-66-generic; however:
  Package linux-image-3.13.0-66-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.13.0-66-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-generic (3.13.0.68.74) ...
Setting up libnss3-nssdb (2:3.19.2.1-0ubuntu0.14.04.1) ...
Setting up libnss3:amd64 (2:3.19.2.1-0ubuntu0.14.04.1) ...
Setting up libnss3-1d:amd64 (2:3.19.2.1-0ubuntu0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Errors were encountered while processing:
 linux-image-extra-3.13.0-68-generic
 linux-image-3.13.0-65-generic
 linux-image-generic
 linux-image-extra-3.13.0-67-generic
 linux-image-3.13.0-66-generic
 linux-generic
 linux-image-extra-3.13.0-65-generic
 linux-image-extra-3.13.0-66-generic
michael@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.13.0-65-generic linux-image-3.13.0-67-generic
  linux-image-extra-3.13.0-65-generic linux-image-extra-3.13.0-67-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-67-generic linux-image-3.13.0-68-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-67-generic linux-image-3.13.0-68-generic
0 upgraded, 2 newly installed, 0 to remove and 101 not upgraded.
8 not fully installed or removed.
Need to get 0 B/30.4 MB of archives.
After this operation, 85.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 489627 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-68-generic_3.13.0-68.111_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-68-generic (3.13.0-68.111) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-68-generic_3.13.0-68.111_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-68-generic' to '/boot/vmlinuz-3.13.0-68-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
The link /initrd.img is a damaged link
Removing symbolic link initrd.img
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old
 you may need to re-run your boot loader[grub]
Preparing to unpack .../linux-image-3.13.0-67-generic_3.13.0-67.110_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-67-generic (3.13.0-67.110) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-67-generic_3.13.0-67.110_amd64.deb (--unpack):
 cannot copy extracted data for './boot/abi-3.13.0-67-generic' to '/boot/abi-3.13.0-67-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-68-generic_3.13.0-68.111_amd64.deb
 /var/cache/apt/archives/linux-image-3.13.0-67-generic_3.13.0-67.110_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
And the output of cat /etc/apt/sources.list is:
```
michael@ubuntu:~$ cat /etc/apt/sources.list# deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


# deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
# deb http://security.ubuntu.com/ubuntu trusty-security main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main


## MyAdd
# virtualbox
deb http://download.virtualbox.org/virtualbox/debian saucy contrib
```
Clearly there are some issues, i've just hit a wall with where to go, and nothing that I have tried or researched has worked. Any help would be appreciated. I have also noticed that /boot is full, however it will not allow me to uninstall older versions from it.

---

### Post by v3.xx on 2015-11-14
Hi mike

Have you tried cleaning the file system?

```
sudo apt-get autoremove

```
and please post the output of

```
df -h
```

Also looks like kernels are overloaded.  Please post whats in /boot.

---

### Post by michael331 on 2015-11-15
Thanks for the response, I've tried autoremove but it won't work:
```
michael@ubuntu:~$ sudo apt-get autoremoveReading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-67-generic : Depends: linux-image-3.13.0-67-generic but it is not installed
 linux-image-extra-3.13.0-68-generic : Depends: linux-image-3.13.0-68-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-68-generic but it is not installed
E: Unmet dependencies. Try using -f.
```
apt-get -f install produces the original error
df -h produces:
```
michael@ubuntu:~$ sudo df -hFilesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  1.8T   22G  1.7T   2% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         7.6G  4.0K  7.6G   1% /dev
tmpfs                        1.6G  1.4M  1.6G   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         7.6G  4.0K  7.6G   1% /run/shm
none                         100M  4.0K  100M   1% /run/user
/dev/sda1                    236M  236M     0 100% /boot
/dev/sdb1                    2.7T  1.5T  1.1T  59% /media/dataDrive
```
contents of boot/
```
michael@ubuntu:~$ sudo ls -alh /boot/
total 227M
drwxr-xr-x  4 root root 4.0K Nov 15 00:32 .
drwxr-xr-x 24 root root 4.0K Nov 15 00:32 ..
-rw-------  1 root root 3.3M Dec  8  2014 System.map-3.13.0-43-generic
-rw-------  1 root root 3.3M Dec 15  2014 System.map-3.13.0-44-generic
-rw-------  1 root root 3.3M Mar 10  2015 System.map-3.13.0-46-generic
-rw-------  1 root root 3.3M Mar 12  2015 System.map-3.13.0-48-generic
-rw-------  1 root root 3.3M May 20 06:11 System.map-3.13.0-53-generic
-rw-------  1 root root 3.3M Aug 11 11:15 System.map-3.13.0-62-generic
-rw-------  1 root root 3.3M Aug 14 18:07 System.map-3.13.0-63-generic
-rw-------  1 root root 3.3M Oct  2 18:53 System.map-3.13.0-65-generic
-rw-------  1 root root 3.3M Oct  7 11:34 System.map-3.13.0-66-generic
-rw-r--r--  1 root root 1.2M Dec  8  2014 abi-3.13.0-43-generic
-rw-r--r--  1 root root 1.2M Dec 15  2014 abi-3.13.0-44-generic
-rw-r--r--  1 root root 1.2M Mar 10  2015 abi-3.13.0-46-generic
-rw-r--r--  1 root root 1.2M Mar 12  2015 abi-3.13.0-48-generic
-rw-r--r--  1 root root 1.2M May 20 06:11 abi-3.13.0-53-generic
-rw-r--r--  1 root root 1.2M Aug 11 11:15 abi-3.13.0-62-generic
-rw-r--r--  1 root root 1.2M Aug 14 18:07 abi-3.13.0-63-generic
-rw-r--r--  1 root root 1.2M Oct  2 18:53 abi-3.13.0-65-generic
-rw-r--r--  1 root root 1.2M Oct  7 11:34 abi-3.13.0-66-generic
-rw-r--r--  1 root root 162K Dec  8  2014 config-3.13.0-43-generic
-rw-r--r--  1 root root 162K Dec 15  2014 config-3.13.0-44-generic
-rw-r--r--  1 root root 162K Mar 10  2015 config-3.13.0-46-generic
-rw-r--r--  1 root root 162K Mar 12  2015 config-3.13.0-48-generic
-rw-r--r--  1 root root 162K May 20 06:11 config-3.13.0-53-generic
-rw-r--r--  1 root root 162K Aug 11 11:15 config-3.13.0-62-generic
-rw-r--r--  1 root root 162K Aug 14 18:07 config-3.13.0-63-generic
-rw-r--r--  1 root root 162K Oct  2 18:53 config-3.13.0-65-generic
-rw-r--r--  1 root root 162K Oct  7 11:34 config-3.13.0-66-generic
drwxr-xr-x  5 root root 1.0K Sep  5 07:55 grub
-rw-r--r--  1 root root  20M Dec 21  2014 initrd.img-3.13.0-43-generic
-rw-r--r--  1 root root  20M Mar 20  2015 initrd.img-3.13.0-44-generic
-rw-r--r--  1 root root  20M Mar 21  2015 initrd.img-3.13.0-46-generic
-rw-r--r--  1 root root  20M May 30 15:59 initrd.img-3.13.0-48-generic
-rw-r--r--  1 root root  20M Aug 20 21:37 initrd.img-3.13.0-53-generic
-rw-r--r--  1 root root  20M Aug 25 21:06 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root  20M Sep  5 07:55 initrd.img-3.13.0-63-generic
drwx------  2 root root  12K Apr 19  2014 lost+found
-rw-r--r--  1 root root 173K Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root 174K Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root 175K Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root 5.6M Dec  8  2014 vmlinuz-3.13.0-43-generic
-rw-------  1 root root 5.6M Dec 15  2014 vmlinuz-3.13.0-44-generic
-rw-------  1 root root 5.6M Mar 10  2015 vmlinuz-3.13.0-46-generic
-rw-------  1 root root 5.6M Mar 12  2015 vmlinuz-3.13.0-48-generic
-rw-------  1 root root 5.6M May 20 06:11 vmlinuz-3.13.0-53-generic
-rw-------  1 root root 5.6M Aug 11 11:15 vmlinuz-3.13.0-62-generic
-rw-------  1 root root 5.6M Aug 14 18:07 vmlinuz-3.13.0-63-generic
-rw-------  1 root root 5.6M Oct  2 18:53 vmlinuz-3.13.0-65-generic
-rw-------  1 root root 5.6M Oct  7 11:34 vmlinuz-3.13.0-66-generic
```

---

### Post by v3.xx on 2015-11-15
Looks like apt-get has not yet locked up (this usually happens).  So maybe a one line command will work.

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge

```
Have a read before you use it.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

If that will not work, then you can use dpkg.

```
sudo dpkg remove --purge **KERNEL VERSION**

```
After you have removed two or three kernels -f install should work, then followed with autoremove.  

Here's a reference.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9)

---

