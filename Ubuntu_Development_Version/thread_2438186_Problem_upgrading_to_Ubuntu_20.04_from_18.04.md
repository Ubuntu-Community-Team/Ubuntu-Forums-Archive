---
title: "Problem upgrading to Ubuntu 20.04 from 18.04"
date: 2020-03-07
forum: Ubuntu Development Version
---

### Post by rakeshshrs on 2020-03-07
[COLOR=#242729][FONT=Arial][FONT=inherit]I tried to upgrade to 20.04 and it showed error at the end and upgrade was stopped. When I checked I found the upgrade to 20.04 was complete. After when I reboot it, the screen was stuck in black screen and when I boot in recovery mode with new 5.4.0-14-generic, there was issue regarding kernel panic error.[/FONT]
[FONT=inherit]So, I used 4.15.0-88-generic to boot and it worked. When I tried to "sudo apt-get upgrade" or "sudo apt-get autoclean" there was issue as follows:

[/FONT][INDENT][FONT=inherit]update-initramfs: Generating /boot/initrd.img-4.15.0-88-generic cp: cannot create regular file '/var/tmp/mkinitramfs_KlyqiO/usr/share/plymouth/themes/spinner/watermark.png': No such file or directory E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1. update-initramfs: failed for /boot/initrd.img-4.15.0-88-generic with 1. dpkg: error processing package linux-firmware (--configure): installed linux-firmware package post-installation script subprocess returned error exit status 1 Setting up linux-image-5.4.0-14-generic (5.4.0-14.17) ... dpkg: dependency problems prevent configuration of linux-image-generic: linux-image-generic depends on linux-firmware; however: Package linux-firmware is not configured yet.[/FONT]
[FONT=inherit]dpkg: error processing package linux-image-generic (--configure): dependency problems - leaving unconfigured No apport report written because the error message indicates its a followup error from a previous failure. No apport report written because the error message indicates its a followup error from a previous failure. dpkg: dependency problems prevent configuration of linux-generic: linux-generic depends on linux-image-generic (= 5.4.0.14.17); however: Package linux-image-generic is not configured yet.[/FONT]
[FONT=inherit]dpkg: error processing package linux-generic (--configure): dependency problems - leaving unconfigured Processing triggers for initramfs-tools (0.136ubuntu1) ... update-initramfs: Generating /boot/initrd.img-4.15.0-88-generic cp: cannot create regular file '/var/tmp/mkinitramfs_ZIHLgn/usr/share/plymouth/themes/spinner/watermark.png': No such file or directory E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1. update-initramfs: failed for /boot/initrd.img-4.15.0-88-generic with 1. dpkg: error processing package initramfs-tools (--configure): installed initramfs-tools package post-installation script subprocess returned error exit status 1 No apport report written because MaxReports is reached already Processing triggers for linux-image-5.4.0-14-generic (5.4.0-14.17) ... /etc/kernel/postinst.d/dkms: * dkms: running auto installation service for kernel 5.4.0-14-generic[/FONT]
[FONT=inherit]Kernel preparation unnecessary for this kernel. Skipping...[/FONT]
[FONT=inherit]Building module: cleaning build area... 'make' -j4 -C ashmem KERNEL_SRC=/lib/modules/5.4.0-14-generic/build && make -j4 -C binder KERNEL_SRC=/lib/modules/5.4.0-14-generic/build.........(bad exit status: 2) ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/anbox-modules-dkms.0.crash' Error! Bad return status for module build on kernel: 5.4.0-14-generic (x86_64) Consult /var/lib/dkms/anbox/1/build/make.log for more information. ...done. /etc/kernel/postinst.d/initramfs-tools: update-initramfs: Generating /boot/initrd.img-5.4.0-14-generic cp: cannot create regular file '/var/tmp/mkinitramfs_m9c6Ab/usr/share/plymouth/themes/spinner/watermark.png': No such file or directory E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1. update-initramfs: failed for /boot/initrd.img-5.4.0-14-generic with 1. run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1 dpkg: error processing package linux-image-5.4.0-14-generic (--configure): installed linux-image-5.4.0-14-generic package post-installation script subprocess returned error exit status 1 No apport report written because MaxReports is reached already[/FONT]
[FONT=inherit]Errors were encountered while processing: linux-firmware linux-image-generic linux-generic initramfs-tools linux-image-5.4.0-14-generic

[/FONT]
[/INDENT]
[FONT=inherit]I have tried many options that I found online like:[/FONT]
[FONT=inherit]sudo apt install linux-image-5.4.0-14-generic 
sudo apt-get install -f[/FONT]

[/FONT][/COLOR]

---

### Post by coffeecat on 2020-03-07
20.04, therefore thread moved to the *Ubuntu Development Version* sub-forum. 

Unfortunately, your terminal output is near unreadable. I see that you have used BBcode indent tags, but that doesn't help. Somehow you have lost a large number of line returns. Please re-run the commands that produce that output and repost them, preferably directly. It's possible that a browser addon is interfering with the formatting, or using a Windows text editor as an intermediary can cause the same. Please also ensure that the output is between BBCode code tags - link in my sig if you need it.

---

### Post by rakeshshrs on 2020-03-07
I was able to fix the upgrade issue. But now, I have issue with sound, WiFi and video driver. Graphics shows &#8220;llvmpipe LLVM 9.0.1, 256 bits&#8221;. And there is no option to increase refresh rate. It is too slow. And there is no option for WiFi.

---

### Post by rakeshshrs on 2020-03-07
It seems everything is working on Ubuntu with kernel 4.15. It is while booting from new kernel that there are numerous problems. Is there any information that I need to add to solve this issue?

---

### Post by dino99 on 2020-03-07
Think to clean the system to drop the old packages/settings no more needed which could disturbed the system:

> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

you can also install/use bleachbit to go further (use it as 'root' but carefully select items to run)

---

### Post by rakeshshrs on 2020-03-07
I have already done it. There is no change. Drivers are shown as unmanaged. Do I need to Install drivers again separately ? My laptop is dell inspiron 3421.

---

### Post by rakeshshrs on 2020-03-08
Finally it seems to be working. It seems linux-modules-extra was somehow not installed. So, I added it through "sudo apt-get install linux-modules-extra-5.4.0-14-generic".

---

### Post by dwilches on 2020-04-19
I had the same issue, Kernel 4.15.0 booted ok, but 5.4.24 didn't.
What I did to solve it was: `sudo dpkg --configure -a` which reconfigured something related to the kernel and initramfs. After this, I had a new kernel version: 5.4.25 listed among the startup options.

---

### Post by gabriellas on 2020-04-26
Upgrading to Ubuntu 20.04 from 19.10 and 18.04 means that you don’t need to create a live USB of Ubuntu and do a fresh install. All you need is a good internet connection that can download around 1.5 GB of data.

---

