---
title: "Install JRE-7-headless - issues"
date: 2014-02-17
forum: Server Platforms
---

### Post by Eric_Snyder on 2014-02-17
I have the following issues using install openjdk-7-jre-headless. I ran sudo apt-get update and then sudo apt-get -f install. I get the following errors:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  openjdk-7-jre-lib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 505 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-35-generic (3.2.0-35.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-35-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-35-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-35-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-35-generic; however:
  Package linux-image-3.2.0-35-generic is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.35.40); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-3.2.0-35-generic
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
Any help would be greatly appreciated.

Ubuntu server 12.04

---

### Post by Doug S on 2014-02-17
Is your /boot full? There is a "no space left on device" message. What do you get for this (example):```
doug@doug-64:~$ [COLOR=#ff0000]df[/COLOR]
Filesystem                1K-blocks      Used Available Use% Mounted on
/dev/mapper/doug--64-root 958055968 470158800 439230752  52% /
udev                        1527832         4   1527828   1% /dev
tmpfs                        614768       844    613924   1% /run
none                           5120         0      5120   0% /run/lock
none                        1536916         0   1536916   0% /run/shm
/dev/sda1                    233191     73938    146812  34% /boot
```

---

### Post by Eric_Snyder on 2014-02-19
Sorry for the delayed response. I was out yesterday.

Yep:
> Filesystem               1K-blocks      Used Available Use% Mounted on/dev/mapper/system-root   48057224  23743568  21872440  53% /
udev                       5111112         4   5111108   1% /dev
tmpfs                      2048076      1540   2046536   1% /run
none                          5120         0      5120   0% /run/lock
none                       5120188       212   5119976   1% /run/shm
/dev/sda1                153794688 151510504         0 100% /mnt/backup
/dev/sdb1                   283691    279136         0 100% /boot
/dev/mapper/data-home   1038133640 536907844 448503268  55% /mnt/home


I have a lot of unused kernals?
> eric@sl24:~$ ls /bootabi-2.6.32-24-generic         initrd.img-3.2.0-31-generic
abi-2.6.32-36-generic         initrd.img-3.2.0-32-generic
abi-3.2.0-23-generic          initrd.img-3.2.0-33-generic
abi-3.2.0-24-generic          initrd.img-3.2.0-34-generic
abi-3.2.0-25-generic          lost+found
abi-3.2.0-26-generic          memtest86+.bin
abi-3.2.0-27-generic          memtest86+_multiboot.bin
abi-3.2.0-29-generic          System.map-2.6.32-24-generic
abi-3.2.0-31-generic          System.map-2.6.32-36-generic
abi-3.2.0-32-generic          System.map-3.2.0-23-generic
abi-3.2.0-33-generic          System.map-3.2.0-24-generic
abi-3.2.0-34-generic          System.map-3.2.0-25-generic
abi-3.2.0-35-generic          System.map-3.2.0-26-generic
config-2.6.32-24-generic      System.map-3.2.0-27-generic
config-2.6.32-36-generic      System.map-3.2.0-29-generic
config-3.2.0-23-generic       System.map-3.2.0-31-generic
config-3.2.0-24-generic       System.map-3.2.0-32-generic
config-3.2.0-25-generic       System.map-3.2.0-33-generic
config-3.2.0-26-generic       System.map-3.2.0-34-generic
config-3.2.0-27-generic       System.map-3.2.0-35-generic
config-3.2.0-29-generic       vmcoreinfo-2.6.32-24-generic
config-3.2.0-31-generic       vmcoreinfo-2.6.32-36-generic
config-3.2.0-32-generic       vmlinuz-2.6.32-24-generic
config-3.2.0-33-generic       vmlinuz-2.6.32-36-generic
config-3.2.0-34-generic       vmlinuz-3.2.0-23-generic
config-3.2.0-35-generic       vmlinuz-3.2.0-24-generic
grub                          vmlinuz-3.2.0-25-generic
grub.bak                      vmlinuz-3.2.0-26-generic
initrd.img-2.6.32-24-generic  vmlinuz-3.2.0-27-generic
initrd.img-2.6.32-36-generic  vmlinuz-3.2.0-29-generic
initrd.img-3.2.0-23-generic   vmlinuz-3.2.0-31-generic
initrd.img-3.2.0-24-generic   vmlinuz-3.2.0-32-generic
initrd.img-3.2.0-25-generic   vmlinuz-3.2.0-33-generic
initrd.img-3.2.0-26-generic   vmlinuz-3.2.0-34-generic
initrd.img-3.2.0-27-generic   vmlinuz-3.2.0-35-generic
initrd.img-3.2.0-29-generic


How do I get rid of them without killing something I need?
Would it be smart to resize the boot volume? If so, would I need to boot from a CD or is Ubuntu Super-Uber awesome and allow this while running?

---

### Post by slickymaster on 2014-02-19
> **Eric_Snyder said:**
> <---snip--->
I have a lot of unused kernals?
<---snip--->
How do I get rid of them without killing something I need?
<---snip--->

[Remove or hide old kernel versions, to clean up the boot menu]("http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu")

---

