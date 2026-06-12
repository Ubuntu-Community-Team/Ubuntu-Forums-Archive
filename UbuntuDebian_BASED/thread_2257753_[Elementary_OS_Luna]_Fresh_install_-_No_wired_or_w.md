---
title: "[Elementary OS Luna] Fresh install - No wired or wireless connection."
date: 2014-12-22
forum: Ubuntu/Debian BASED
---

### Post by jason160 on 2014-12-22
Hey, I'm a linux noob and decided to go with Elementary as a starter so I can enjoy the good looks while getting a feel for the OS. I installed it and everything went smoothly other than the fact that I couldn't connect to the internet, not through ethernet, or wireless. I'm on a Lenovo g510 laptop.

I saw some other threads for similar issues and they always told the OP to put a few commands in so here are mine:
```
jason@jason-L:~$ lspci00:00.0 Host bridge: Intel Corporation Haswell DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Haswell Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Haswell HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation Lynx Point USB xHCI Host Controller (rev 05)
00:16.0 Communication controller: Intel Corporation Lynx Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Lynx Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Lynx Point HD Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port 1 (rev d5)
00:1c.1 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port 2 (rev d5)
00:1c.2 PCI bridge: Intel Corporation Lynx Point PCI Express Root Port 3 (rev d5)
00:1d.0 USB controller: Intel Corporation Lynx Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Lynx Point LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Lynx Point 6-Port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Lynx Point SMBus Controller (rev 05)
02:00.0 Network controller: Broadcom Corporation Device 4365 (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. Device 10a0 (rev 10)
```
```
jason@jason-L:~$ uname -a
Linux jason-L 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:18:19 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by oldfred on 2014-12-22
Do not know Elementary, nor the one that knows Ethernet connections the best here in forum.

But you have a very new Haswell processor based system. And Intel has been good at providing software updates to Linux developers. But the updates are not in older releases and often may be only in the very newest release, unless you want to search Internet for ppa or software to totally reconfigure an older version to really be the newer version. Elementary may have done some of that but old kernel indicates to me that it is not that up to date.

Since you have the 3.2 kernel that is like Ubuntu 12.04 or based on 12.04. But to get all the newer Intel support you need at least 14.04 or maybe even 14.10. That may automatically resolve many issues.

---

### Post by kerry_s on 2014-12-23
i agree. grab a copy of ubuntu mate 14.10 you'll get a more to date mate system.
[https://ubuntu-mate.org/download/ubuntu-mate-14.10-desktop-amd64.iso.torrent](https://ubuntu-mate.org/download/ubuntu-mate-14.10-desktop-amd64.iso.torrent)

---

### Post by Elfy on 2014-12-23
*Thread moved to **Ubuntu/Debian BASED**.*

---

