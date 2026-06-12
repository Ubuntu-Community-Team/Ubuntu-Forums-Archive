---
title: "LVM + trim on ubuntu server 12.04"
date: 2012-08-22
forum: Server Platforms
---

### Post by Blackra1n on 2012-08-22
I just got my new home server up and running and I have some questions regarding trim. (I got an Intel 330 ssd) According to this page [http://wiki.debian.org/SSDoptimization](http://wiki.debian.org/SSDoptimization) issue_discards = 1 setting is required in lvm.conf and discard mount option is not enough to make trim working. Is it really true?

I also have an ext2 boot partition in my lvm setup (I just accepted the default lvm formatting option during the ubuntu 12.04 64 bit server install process). Is that bad? (ext2 does not have trim support).

Debian SSD optimization guide also mentions about setting "discard" mount option for swap partition. Is that really necessary?

My server:

Intel Core i5 3450S
120GB Intel 330 Series SSD
8GB RAM
ASRock H77M-ITX mobo

---

