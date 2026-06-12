---
title: "Ubuntu 9.04 alpha4  raid 1 make both drives bootable"
date: 2009-02-13
forum: Server Platforms
---

### Post by j_reacher on 2009-02-13
Hi, i'm testing a new server with Ubuntu 9.04 alpha 4.
I must create a raid 1 configuration in Fujitsu RX 100 S4.
Ubuntu 8.10 failed raid creation with this bug

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/305500](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/305500)

The 9.04 alpha 4 worked well, raid 1 created without problem

Now, how can i make both drives bootable?

I'followed this step but not working (error 15 file not found)


    * Reboot the server from the original Ubuntu Server CDROM
    * From the Ubuntu boot menu, select “Rescue a broken system”
    * Continue through the prompts until the screen “Device to use as a root file system” appears
    * Press Alt-F2 to switch to a second console screen then press Enter to activate it.
    * Mount the md0 RAID device and use chroot and grub to install the bootloader onto both sda and sdb using the following commands

    mount /dev/md0 /mnt
    chroot /mnt
    grub
    device (hd0) /dev/sda
    root (hd0,0)
    setup (hd0)
    device (hd1) /dev/sdb
    root (hd1,0)
    setup (hd1)
    quit



thax 
J.

---

