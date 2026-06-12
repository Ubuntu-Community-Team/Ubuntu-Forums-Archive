---
title: "Absolutely must partitions for any Linux"
date: 2015-07-02
forum: Windows
---

### Post by tech291083 on 2015-07-02
Dear Admin,

Please forgive me in advance if this is not the right forum for my thread. Thanks.

Hi Friends,

Ubuntu offers the option to install itself alongside an already Windows on the same hard drive and also there is an option to create the required partitions manually by selecting the optional called "Something else", but confuses me most is which of the following partitions are a must to install Ubuntu alongside Windows or to install it as the only OS on the entire hard drive? And what about other types of Linux ie Fedora, Suse, Debian, Gentoo, Puppy, Slackware etc? What partitions are a must for them? As far as I know, some Linux distributions do not create all of the below partitions when one chooses to install them automatically.

Swap
Grub
Home
Root

Thanks a lot.

---

### Post by buzzingrobot on 2015-07-02
Only one partition is required. The items you listed must exist, but they can exist as individual directories on a single partition, or each can reside as a directory on its own partition created for that purpose, or a mix and match of both. (Note that grub is a Linux bootloader program.)

While swap in Linux can be configured as a file, it is conventionally a separate partition and is not part of the filesystem.

---

### Post by The_Forgotten_King on 2015-07-02
I set mine up like this.

/
ext4 file system
25 gigabytes (I'm on a netbook)

/home
ext4 file system
<All remaining space, 130gigs for me>

swap space
<Double your ram>

All are logical.

---

