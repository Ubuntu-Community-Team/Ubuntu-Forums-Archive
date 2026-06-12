---
title: "Hardware Enablement stack 12.04.5 Problem"
date: 2014-07-24
forum: Server Platforms
---

### Post by Deepcuts on 2014-07-24
Hello,

Using Ubuntu 12.04 64 bit
Like everyone else, I received the EOL message.

Ran: apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty
Everything seemed to go well and did a reboot
Now the machine does not start anymore and need to go and see what is wrong with it after this update, in DC.

Anything I missed?
Any other commands I should have run?


# apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic linux-headers-generic-lts-trusty linux-image-3.13.0-32-generic
Suggested packages:
  fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0 linux-lts-trusty-tools
The following NEW packages will be installed:
  linux-generic-lts-trusty linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic linux-headers-generic-lts-trusty linux-image-3.13.0-32-generic linux-image-generic-lts-trusty
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 66.4 MB of archives.
After this operation, 274 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.13.0-32-generic amd64 3.13.0-32.57~precise1 [52.4 MB]
Get:2 [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-generic-lts-trusty amd64 3.13.0.32.28 [2,494 B]
Get:3 [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.13.0-32 all 3.13.0-32.57~precise1 [12.8 MB]
Get:4 [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.13.0-32-generic amd64 3.13.0-32.57~precise1 [1,127 kB]
Get:5 [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic-lts-trusty amd64 3.13.0.32.28 [2,492 B]
Get:6 [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) precise-updates/main linux-generic-lts-trusty amd64 3.13.0.32.28 [1,746 B]
Fetched 66.4 MB in 5s (13.1 MB/s)
Selecting previously unselected package linux-image-3.13.0-32-generic.
(Reading database ... 167589 files and directories currently installed.)
Unpacking linux-image-3.13.0-32-generic (from .../linux-image-3.13.0-32-generic_3.13.0-32.57~precise1_amd64.deb) ...
Done.
Selecting previously unselected package linux-image-generic-lts-trusty.
Unpacking linux-image-generic-lts-trusty (from .../linux-image-generic-lts-trusty_3.13.0.32.28_amd64.deb) ...
Selecting previously unselected package linux-headers-3.13.0-32.
Unpacking linux-headers-3.13.0-32 (from .../linux-headers-3.13.0-32_3.13.0-32.57~precise1_all.deb) ...
Selecting previously unselected package linux-headers-3.13.0-32-generic.
Unpacking linux-headers-3.13.0-32-generic (from .../linux-headers-3.13.0-32-generic_3.13.0-32.57~precise1_amd64.deb) ...
Selecting previously unselected package linux-headers-generic-lts-trusty.
Unpacking linux-headers-generic-lts-trusty (from .../linux-headers-generic-lts-trusty_3.13.0.32.28_amd64.deb) ...
Selecting previously unselected package linux-generic-lts-trusty.
Unpacking linux-generic-lts-trusty (from .../linux-generic-lts-trusty_3.13.0.32.28_amd64.deb) ...
Setting up linux-image-3.13.0-32-generic (3.13.0-32.57~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-3.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-1.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8411-2.fw for module r8169
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.5.0-54-generic
Found initrd image: /boot/initrd.img-3.5.0-54-generic
Found linux image: /boot/vmlinuz-3.5.0-52-generic
Found initrd image: /boot/initrd.img-3.5.0-52-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic-lts-trusty (3.13.0.32.28) ...
Setting up linux-headers-3.13.0-32 (3.13.0-32.57~precise1) ...
Setting up linux-headers-3.13.0-32-generic (3.13.0-32.57~precise1) ...
Setting up linux-headers-generic-lts-trusty (3.13.0.32.28) ...
Setting up linux-generic-lts-trusty (3.13.0.32.28) ...
# reboot


Broadcast message from xxx
        (/dev/pts/1) at 4:05 ...


The system is going down for reboot NOW!

---

### Post by Deepcuts on 2014-07-24
Seems that running the above said command messed up grub somehow.
Booted a Live CD and **grub-install /dev/sda**
All good now.

---

