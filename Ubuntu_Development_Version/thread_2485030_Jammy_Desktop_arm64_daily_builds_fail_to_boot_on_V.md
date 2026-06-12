---
title: "Jammy Desktop arm64 daily builds fail to boot on VMware Fusion 13"
date: 2023-03-17
forum: Ubuntu Development Version
---

### Post by perockwell on 2023-03-17
The daily Jammy Desktop build for arm64 available from [jammy-desktop-arm64.iso]("https://cdimage.ubuntu.com/jammy/daily-live/current/jammy-desktop-arm64.iso") dated 2023-02-17 (the latest one available) fails to boot on VMware Fusion 13 on Apple Silicon. Or at least it seems that way. The boot attempt results in no output to the console window after initial boot.

This issue does not appear on Lunar with its 6.1 kernel. 

What kernel version is being used in these daily builds? If it's a 5.19 version, I'm wondering if it suffers from a regression in behavior of the 5.19 kernels that prompted the following Launchpad bug to be filed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2007001](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2007001)

---

