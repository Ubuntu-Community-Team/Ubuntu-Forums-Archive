---
title: "Issues upgrading Kernel, Highpoint Rocketraid 2720SGL"
date: 2016-08-02
forum: Server Platforms
---

### Post by David_Moore on 2016-08-02
I was running 14.04.1 LTS server successfully for a couple years and recently performed an upgrade to Xenial, 16.04.1 LTS.

I'm not exactly sure what happened, but the upgrade failed half way through, but 16.04.1 appears to be installed, but I'm running the old kernel.
```
david@FREYJA:~$ uname -r
3.19.0-64-generic
david@FREYJA:~$
```

At first, when booting, the server would fail to boot each time. I've attempted to uninstall the Kernel and reinstall again with different versions, but each time the server does not boot. My latest attempt was with 4.04.0-31.

First I removed the other kernels and attempted a fresh install of the kernel I'm attempting to boot.

```
david@FREYJA:~$ sudo apt-get install linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic --fix-missing
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-4.4.0-31 is already the newest version (4.4.0-31.50).
linux-headers-4.4.0-31 set to manually installed.
linux-headers-4.4.0-31-generic is already the newest version (4.4.0-31.50).
linux-headers-4.4.0-31-generic set to manually installed.
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-31-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/18.7 MB of archives.
After this operation, 55.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package linux-image-4.4.0-31-generic.
(Reading database ... 204256 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-31-generic_4.4.0-31.50_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Setting up linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-31-generic/boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-64-generic
Found initrd image: /boot/initrd.img-3.19.0-64-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```

I looked online at the Error I received above and it's an issue with dkms. I guess this is a problem for another day.
```
david@FREYJA:~$ dkms status
iser, 1.8.0, 3.19.0-64-generic, x86_64: installedError! Could not locate dkms.conf file.
File:  does not exist.
```

Anyway, my server is in use right now and I'll perform a reboot and attempt to boot up ASAP, but my first question is: is there a dump created when there is a boot failure? If so, where is it? I think my main issue is that I don't know where to look to begin troubleshooting why the server won't boot with the new kernel.

This is the first failed message that I receive.

Loading hangs on this for 1m30s.

This is where loading ends up. I was unable to use my keyboard to type anything even though it worked fine to access BIOS and to navigate grub.

---

### Post by howefield on 2016-08-02
Thread moved to the "*Server PLatforms*" forum and oversized images thumbnailed.

---

### Post by chase-gooding on 2016-08-02
maybe try:

sudo apt-get remove dkms
sudo apt-get install dkms

---

### Post by David_Moore on 2016-08-03
> **chase-gooding said:**
> maybe try:

sudo apt-get remove dkms
sudo apt-get install dkms

Thanks. I'll give this a try and report back.

---

### Post by David_Moore on 2016-08-03
> **chase-gooding said:**
> maybe try:

sudo apt-get remove dkms
sudo apt-get install dkms

So I removed and reinstalled DKMS.

```
david@FREYJA:~$ sudo apt-get remove dkms
[sudo] password for david:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  dkms iser-dkms kernel-mft-dkms knem-dkms mlnx-ofed-kernel-dkms srp-dkms
0 upgraded, 0 newly installed, 6 to remove and 2 not upgraded.
After this operation, 17.0 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 205324 files and directories currently installed.)
Removing knem-dkms (1.1.2.90mlnx1-OFED.3.3.0.0.1.0.3.1.ga04469b) ...

-------- Uninstall Beginning --------
Module:  knem
Version: 1.1.2.90mlnx1
Kernel:  3.19.0-64-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

knem.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 1.1.2.90mlnx1
completely from the DKMS tree.
------------------------------
Done.
Removing iser-dkms (1.8.0-OFED.3.3.1.0.4.1.gcd30181) ...

-------- Uninstall Beginning --------
Module:  iser
Version: 1.8.0
Kernel:  3.19.0-64-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ib_iser.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 1.8.0
completely from the DKMS tree.
------------------------------
Done.
Removing kernel-mft-dkms (4.4.0-44) ...
Error! Could not locate dkms.conf file.
File:  does not exist.
Removing srp-dkms (1.6.0-OFED.3.3.1.0.4.1.gcd30181) ...

-------- Uninstall Beginning --------
Module:  srp
Version: 1.6.0
Kernel:  3.19.0-64-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ib_srp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


scsi_transport_srp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 1.6.0
completely from the DKMS tree.
------------------------------
Done.
Removing mlnx-ofed-kernel-dkms (3.3-OFED.3.3.1.0.4.1.gcd30181) ...

-------- Uninstall Beginning --------
Module:  mlnx-ofed-kernel
Version: 3.3
Kernel:  3.19.0-64-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

mlx_compat.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_core.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_mad.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_sa.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_cm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


iw_cm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_umad.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_uverbs.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_ucm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_addr.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_netlink.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rdma_cm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


rdma_ucm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


mlx4_core.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


mlx4_ib.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


mlx4_en.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


mlx5_core.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


mlx5_ib.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_ipoib.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


ib_sdp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


eth_ipoib.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-64-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

Backing up initrd.img-3.19.0-64-generic to /boot/initrd.img-3.19.0-64-generic.ol                                                                                                                                                                                                                                                                                                             d-dkms
Making new initrd.img-3.19.0-64-generic
(If next boot fails, revert to initrd.img-3.19.0-64-generic.old-dkms image)
update-initramfs....

DKMS: uninstall completed.

------------------------------
Deleting module version: 3.3
completely from the DKMS tree.
------------------------------
Done.
Removing dkms (2.2.0.3-2ubuntu11.1) ...
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
Processing triggers for man-db (2.7.5-1) ...
david@FREYJA:~$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/66.2 kB of archives.
After this operation, 265 kB of additional disk space will be used.
Selecting previously unselected package dkms.
(Reading database ... 204149 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11.1_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up dkms (2.2.0.3-2ubuntu11.1) ...
```


The problem still persists.

---

### Post by David_Moore on 2016-08-04
Is there a boot log so I can troubleshoot this problem?

---

### Post by Seb_Boffen on 2016-08-04
Personally I performed a restore to ubuntu 14.04 as far too many things are not backwards compatible. And hardware support is not forward compatible within my eyes is the beginning of a  complete failiure within linux. Its a matter of find and try out if 16.04 works if not revert. As this upgrade is far from any upgrade sinds I've done from 10.04 till 14.40 without a working system, which needed tweaking. Give it more time or realize your landscape is not supported and or search specifically for packpages your depend on and look for solutions before upgrading again.

---

### Post by David_Moore on 2016-08-09
So I performed the standard apt-get dist-upgrade and I got an error.

```
david@FREYJA:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.7 MB of archives.
After this operation, 77.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-34 all 4.4.0-34.53 [9,939 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-34-generic amd64 4.4.0-34.53 [784 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.34.36 [2,310 B]
Fetched 10.7 MB in 1s (5,532 kB/s)
Selecting previously unselected package linux-headers-4.4.0-34.
(Reading database ... 205324 files and directories currently installed.)
Preparing to unpack .../linux-headers-4.4.0-34_4.4.0-34.53_all.deb ...
Unpacking linux-headers-4.4.0-34 (4.4.0-34.53) ...
Selecting previously unselected package linux-headers-4.4.0-34-generic.
Preparing to unpack .../linux-headers-4.4.0-34-generic_4.4.0-34.53_amd64.deb ...
Unpacking linux-headers-4.4.0-34-generic (4.4.0-34.53) ...
Preparing to unpack .../linux-headers-generic_4.4.0.34.36_amd64.deb ...
Unpacking linux-headers-generic (4.4.0.34.36) over (4.4.0.31.33) ...
Setting up linux-headers-4.4.0-34 (4.4.0-34.53) ...
Setting up linux-headers-4.4.0-34-generic (4.4.0-34.53) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.
Setting up linux-headers-generic (4.4.0.34.36) ...
```

: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.

I did a google search and this came back as a damaged symlink error. I saw online that I needed to rebuild the initrd.img so I ran this.

david@FREYJA:~$ sudo update-initramfs -c -k $(uname -r)
update-initramfs: Generating /boot/initrd.img-3.19.0-64-generic

I performed a grub update to see where I was at with things:

david@FREYJA:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-64-generic
Found initrd image: /boot/initrd.img-3.19.0-64-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

I attempted to reinstall the new image via apt-get:

```
david@FREYJA:~$ sudo apt-get install linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-headers-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-headers-generic
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/10.7 MB of archives.
After this operation, 77.6 MB of additional disk space will be used.
Selecting previously unselected package linux-headers-4.4.0-34.
(Reading database ... 204253 files and directories currently installed.)
Preparing to unpack .../linux-headers-4.4.0-34_4.4.0-34.53_all.deb ...
Unpacking linux-headers-4.4.0-34 (4.4.0-34.53) ...
Selecting previously unselected package linux-headers-4.4.0-34-generic.
Preparing to unpack .../linux-headers-4.4.0-34-generic_4.4.0-34.53_amd64.deb ...
Unpacking linux-headers-4.4.0-34-generic (4.4.0-34.53) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack .../linux-headers-generic_4.4.0.34.36_amd64.deb ...
Unpacking linux-headers-generic (4.4.0.34.36) ...
Setting up linux-headers-4.4.0-34 (4.4.0-34.53) ...
Setting up linux-headers-4.4.0-34-generic (4.4.0-34.53) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
Setting up linux-headers-generic (4.4.0.34.36) ...
david@FREYJA:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-64-generic
Found initrd image: /boot/initrd.img-3.19.0-64-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```

So now it looks like I'm missing the new images from the /boot/ folder. How do I manually create them?

---

### Post by Graham_Willis on 2016-08-09
I'm not sure if it's actually what you're asking about, but you can download a package without installing it using **apt-get download **(for example **apt-get download linux-image-4.4.0.3**) and then just extract files from the downloaded archive (**dpkg -c** **package.deb targetdir)**.

---

### Post by David_Moore on 2016-08-09
> **Graham_Willis said:**
> I'm not sure if it's actually what you're asking about, but you can download a package without installing it using **apt-get download **(for example **apt-get download linux-image-4.4.0.3**) and then just extract files from the downloaded archive (**dpkg -c** **package.deb targetdir)**.

After reading your response I realized that I never did an apt-get on the new images.

```
david@FREYJA:~$ sudo apt-get install linux-image-4.4.0-34-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-34-generic
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
Need to get 18.7 MB of archives.
After this operation, 55.5 MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-34-generic amd64 4.4.0-34.53 [18.7 MB]
Fetched 18.7 MB in 1s (11.5 MB/s)
Selecting previously unselected package linux-image-4.4.0-34-generic.
(Reading database ... 230886 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-34-generic_4.4.0-34.53_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-34-generic (4.4.0-34.53) ...
Setting up linux-image-4.4.0-34-generic (4.4.0-34.53) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-3.19.0-64-generic
Found initrd image: /boot/initrd.img-3.19.0-64-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

I'll try to reboot again and see if problems still persist.

---

### Post by David_Moore on 2016-08-10
This can be marked as resolved.

During boot up with the new kernel, I kept getting this timeout:
[https://goo.gl/photos/cxcZ17tW8fepJ7Yb7](https://goo.gl/photos/cxcZ17tW8fepJ7Yb7)

WTF is this?

So I ran journalctl -xb and went through all the boot logs and came across this:
[https://goo.gl/photos/wGw4Ewa5uFGSjpGx7](https://goo.gl/photos/wGw4Ewa5uFGSjpGx7)

So I commented out my fstab for that /Storage, which is my Highpoint Raid 2720SGL array mount.

BOOM booted right up.

I then found that lsblk was showing all my drive individually instead of the array.

I reinstalled the .bin file and rebooted.

Array was back. I then uncommented the entry in fstab and reboot once again.

Array is back. It's mounted. Everything appears to be working.

---

