---
title: "Gazelle Professional Configuring for Multiboot"
date: 2012-11-14
forum: System76 Support
---

### Post by DanDennison84 on 2012-11-14
Hi everyone,  I've bought a new System76 Gazelle professional

[LIST]
[*]Ubuntu 12.10 64 bit
[*]5 Free GB of Ubuntu One Online Storage and Sync
[*]15.6" 1080p Full High Definition LED Backlit Display featuring 95% NTSC Color Gamut in Matte Finished Surface ( 1920 x 1080 )
[*]Intel HD Graphics 4000
[*]3rd Generation Intel Core i7-3630QM Processor ( 2.40GHz 6MB L3 Cache - 4 Cores plus Hyperthreading )
[*]8 GB Dual Channel DDR3 SDRAM at 1600MHz - 2 X 4GB
[*]750 GB 7200 RPM SATA II
[*]United States Keyboard Layout
[*]8X DVD±R/RW/4X +DL Super-Multi Drive
[*]Intel Centrino 1030 - 802.11 b/g/n Wireless LAN + Bluetooth Combo Module
[/LIST]

I've been using Ubuntu for about 1 year on another system.  I've also been trying other distros in VirtualBox on Ubuntu.  I would really like to configuring my system to multiboot.  Are there any issues with repartitioning my HD and installing slackware 14 and possibly ubuntu with my hardware above?  Do I need the system76 drivers, for example?

---

### Post by isantop on 2012-11-14
> **DanDennison84 said:**
> Hi everyone,  I've bought a new System76 Gazelle professional

[LIST]
[*]Ubuntu 12.10 64 bit
[*]5 Free GB of Ubuntu One Online Storage and Sync
[*]15.6" 1080p Full High Definition LED Backlit Display featuring 95% NTSC Color Gamut in Matte Finished Surface ( 1920 x 1080 )
[*]Intel HD Graphics 4000
[*]3rd Generation Intel Core i7-3630QM Processor ( 2.40GHz 6MB L3 Cache - 4 Cores plus Hyperthreading )
[*]8 GB Dual Channel DDR3 SDRAM at 1600MHz - 2 X 4GB
[*]750 GB 7200 RPM SATA II
[*]United States Keyboard Layout
[*]8X DVD±R/RW/4X +DL Super-Multi Drive
[*]Intel Centrino 1030 - 802.11 b/g/n Wireless LAN + Bluetooth Combo Module
[/LIST]

I've been using Ubuntu for about 1 year on another system.  I've also been trying other distros in VirtualBox on Ubuntu.  I would really like to configuring my system to multiboot.  Are there any issues with repartitioning my HD and installing slackware 14 and possibly ubuntu with my hardware above?  Do I need the system76 drivers, for example?

You're free to do whatever you like with the software. That said, we can't guarantee that Slackware will work, though. The System76 Driver is only compatible with Ubuntu.

---

### Post by DanDennison84 on 2012-11-14
Ok, I tried it out and it worked.  For those interested, here is what I did.
```

    P     TYPE     LABEL    FS    SIZE
|--sda1  primary   grub2   ext4     1GB
|--sda2  primary   swap    swap     9GB
|--sda3  logical   distros lvm    740GB
    |--sda5 ---->  home           100GB
    |--sda6 ---->  ubuntu64       100GB
    |--sda7 ---->  slackware64    100GB
    |--sda8 ---->  spare1         100GB
    |--sda9 ---->  spare2         100GB
    |--sda10 --->  spare3         240GB

```
[LIST]
[*]grub2 - dedicated grub2 partition that I update from ubuntu64
[*]swap  - dedicated swap partition used by all distros
[*]home  - dedicated home
[*]ubuntu64     - LVs for /, /boot, /usr/local
[*]slackware64  - LVs for /, /boot, /usr/local
[/LIST]

Rather than use 1 lv group, I created separate lv groups for each distro and home.  This lets me use names like 'boot', 'root', and 'usrlocal' for the logical volumes in each group.

Home is setup so that there is a /home/ubuntu64, /home/slackware64, etc.  Links are used to map in shared directories between distros.  So:

[LIST]
[*]/home/dan
[*]/home/ubuntu64/dan - symlinks to /home/dan/projects for example.
[*]/home/slackware64/dan - symlinks to /home/dan/projects as well.
[/LIST]

---

