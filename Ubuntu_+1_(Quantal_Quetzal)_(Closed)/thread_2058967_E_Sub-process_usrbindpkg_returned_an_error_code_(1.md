---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-09-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by fantab on 2012-09-17
When upgrading from Terminal I get following ERROR:

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```On further Trouble Shooting I get:

```
dpkg: error processing linux-image-3.5.0-13-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.5.0-13-generic
 linux-image-3.5.0-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```When I try to remove the above packages from Synaptic I get:

```
E: linux-image-extra-3.5.0-13-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-3.5.0-13-generic: subprocess installed post-removal script returned error exit status 1
```~$ [B]dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
[/B]```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-python1.49.0 libcelt0-0 liblapack3gf libportmidi0 libsdl-ttf2.0-0
  libsmpeg0 libtiff4 python-libtorrent python-numpy python-pygame
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libc6-dev* linux-image-3.5.0-13-generic linux-image-extra-3.5.0-13-generic
  linux-libc-dev*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 167 MB disk space will be freed.
(Reading database ... 157616 files and directories currently installed.)
Removing linux-image-extra-3.5.0-13-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-13-generic /boot/vmlinuz-3.5.0-13-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-13-generic /boot/vmlinuz-3.5.0-13-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.5.0-13-generic.postrm line 328.
dpkg: error processing linux-image-extra-3.5.0-13-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.5.0-13-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-13-generic /boot/vmlinuz-3.5.0-13-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-13-generic /boot/vmlinuz-3.5.0-13-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.5.0-13-generic.postrm line 328.
dpkg: error processing linux-image-3.5.0-13-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.5.0-13-generic
 linux-image-3.5.0-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Please help me fix this...

thanks..

---

### Post by effenberg0x0 on 2012-09-17
> **fantab said:**
> When upgrading from Terminal I get following ERROR:

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```On further Trouble Shooting I get:

```
dpkg: error processing linux-image-3.5.0-13-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.5.0-13-generic
 linux-image-3.5.0-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```When I try to remove the above packages from Synaptic I get:

```
E: linux-image-extra-3.5.0-13-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-3.5.0-13-generic: subprocess installed post-removal script returned error exit status 1
```~$ [B]dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
[/B]```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-python1.49.0 libcelt0-0 liblapack3gf libportmidi0 libsdl-ttf2.0-0
  libsmpeg0 libtiff4 python-libtorrent python-numpy python-pygame
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libc6-dev* linux-image-3.5.0-13-generic linux-image-extra-3.5.0-13-generic
  linux-libc-dev*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 167 MB disk space will be freed.
(Reading database ... 157616 files and directories currently installed.)
Removing linux-image-extra-3.5.0-13-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-13-generic /boot/vmlinuz-3.5.0-13-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-13-generic /boot/vmlinuz-3.5.0-13-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.5.0-13-generic.postrm line 328.
dpkg: error processing linux-image-extra-3.5.0-13-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.5.0-13-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-13-generic /boot/vmlinuz-3.5.0-13-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-13-generic /boot/vmlinuz-3.5.0-13-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.5.0-13-generic.postrm line 328.
dpkg: error processing linux-image-3.5.0-13-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.5.0-13-generic
 linux-image-3.5.0-13-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Please help me fix this...

thanks..

[http://ubuntuforums.org/showthread.php?t=1735575](http://ubuntuforums.org/showthread.php?t=1735575)

---

### Post by fantab on 2012-09-18
Thanks **effenberg**... that solved it. Here is what I did:

> **drs305 said:**
> The problem appears to be in the post installation script of grub: */etc/kernel/postrm.d/zz-update-grub* 

I don't have the problem but I've done what follows. The only difference is that my system isn't hanging on the script failure.

Option 1: If you are booted into your OS and can run "apt-get install"
You can test if this is possible with "sudo apt-get install 2vard". It's a really small package. If it installs ok:
a. Purge grub-common. The command will uninstall grub-common and grub-pc
```
sudo apt-get purge grub-common
```This will remove the zz-update-grub script.
You will be warned you are removing your bootloader. Tab to OK and ENTER.
b. Install grub-pc. It will install grub-common and grub-pc.
```
sudo apt-get install grub-pc
```Tab to OK, and use the spacebar to select ONLY the Ubuntu drive, not the partition.
This will restore the zz-update-grub file. If the problem was with the grub file, this should fix it.
c. Try to update your system again.

---

