---
title: "udev_monitor_new_from_netlink desperate!"
date: 2010-08-15
forum: Server Platforms
---

### Post by goatcow on 2010-08-15
Tonight i had the bright idea to upgrade from the previous LTS release to 10.04 LTS on my **physical** collocate in texas.

Ran do-release-upgrade --proposed per the [ubuntu LTS upgrade guide]("https://help.ubuntu.com/community/LucidUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29"), everything went smoothly, few random package issues with spamassasin and my apache configs but nothing that made me weep.  Rand a apt-get -u dist-upgrade after to make sure nothing was missed and all was right in the world.

....Until i rebooted. Now my machine fails to boot and falls through to a (initramfs) prompt.

Any help you can provide would be greatly appreciated - everything was hosted off this box and i'm desperate to get it back up.  After hours of googling all i can find is info for DomU's with the same issue....but that has to due with the ubunut developers making 10.04 incompatible with older dom0's or something....and again this is a phyiscal machine.  

My hosting provider has me booted into a RIPlinux rescue disk to work on this

Here is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda2
UUID=bf12e965-a154-4d6f-aff2-428cdfeae1f1       /    ext3    defaults,errors=remount-ro    0       1
#/dev/sda1
UUID=b396676a-55ef-4a1c-8faf-3b7369723709       /boot     ext3    defaults,errors=remount-ro    1       2
#/dev/sda3
UUID=23c6c0ec-dd70-4b8f-aca8-08921a9b7509    none    swap    sw                0    0
#/dev/sda5
UUID=9c18bc4d-5952-4ecf-8c80-8312b63cc93e       /home   ext3    defaults            0       0
```and relevant grub menu stanza
```
title        UUID Ubuntu 10.04.1 LTS, kernel 2.6.24-24-server Default
root        (hd0,0)
kernel        /vmlinuz root=UUID=bf12e965-a154-4d6f-aff2-428cdfeae1f1 ro 
initrd        /initrd.img
``````
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Done.
libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument [   38.043839] wait-for-root[870]: segfault at 00000030 eip b7f76f2b esp bfbc5f80 error 4
Segementation fault
There appears to be one or more degraded LVM volumes, and your root device may depend on the LVM volumes being online.  One or more of the following LVM volumes are degraded:
    read_urandom: /dev/urandom: open failed: No such file or directory
Gave up waiting for root device. Common problems
  - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enoug?)
    - Check root = (did the system wait for the right device?)
  - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/bf12e965-a154-4d6f-aff2-428cdfeae1f1 does not exist. Dropping to a shell!
```[IMG]http://www.xmission.com/%7Erocky/photouuid.jpg[/IMG]

---

### Post by goatcow on 2010-08-16
mount /dev/sda2 /mnt/chroot
mount /dev/sda1 /mnt/chroot/boot
mount --bind /dev /mnt/chroot/dev
mount --bind /dev/pts /mnt/chroot/dev/pts
mount --bind /sys /mnt/chroot/sys
mount --bind /proc /mnt/chroot/proc
chroot /mnt/chroot
update-grub
update-initramfs -c -k all


some how some way something must have been missed by do-release-upgrade.

---

