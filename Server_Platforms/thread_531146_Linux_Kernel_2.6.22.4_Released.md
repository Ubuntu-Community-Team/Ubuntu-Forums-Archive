---
title: "Linux Kernel 2.6.22.4 Released"
date: 2007-08-21
forum: Server Platforms
---

### Post by Dark Star on 2007-08-21
The Linux Kernel is the essential part of all Linux Distributions, responsible for resource allocation, low-level hardware interfaces, security, simple communications, and basic file system management.

Linux is a clone of the Unix operating system, initially written from scratch by Linus Torvalds, assisted by a loosely-knit team of hackers across the Net. It aims to achieve POSIX and Single UNIX Specification compliance.

The 2.6.22.4 version from the 2.6 stable Linux kernel branch was released last night and it fixes an important vulnerability that allowed an unprivileged local user to send arbitrary signals to a child process despite security restrictions:

"This fixes a vulnerability in the "parent process death signal" implementation discoverd by Wojciech Purczynski of COSEINC PTE Ltd. and iSEC Security Research.", stated Greg Kroah-Hartman.

In a sane environment, non-root users can't send signals to processes running with different UID, but this vulnerability found in the Linux kernel by Wojciech Purczynski, allowed any local user to bypass security restrictions and send arbitrary signals to any child process executed by the user.

For more information about this vulnerability [please go here.]("http://marc.info/?l=bugtraq&m=118711306802632&w=2")

**Changes from version 2.6.22.3 to 2.6.22.4:**

[LIST]
[*] Reset current->pdeath_signal on SUID binary execution (CVE-2007-3848)
[/LIST]

**The 2.6.22 Linux kernel includes features and drivers such as:**
[LIST]
[*] New Slab allocator: SLUB
[*] New Wireless stack
[*] New Firewire stack
[*] Signal/timer events notifications through file descriptors
[*] Blackfin architecture
[*] UBI
[*] Secure RxRPC sockets
[*]Process footprint measurement facility
[*] utimensat()
[/LIST]

**Graphic drivers:**
[LIST]
[*] pm3fb: Preliminary 2.4 to 2.6 port
[*] New framebuffer driver (vt8623fb) for VIA VT8623
[*] Hecuba framebuffer driver
[*] arkfb: new framebuffer driver for ARK Logic cards
[*] atmel_lcdfb: AT91/AT32 LCD Controller framebuffer driver
[*] Add Sun XVR-500 framebuffer driver. (commit) and Sun XVR-2500 framebuffer driver
[/LIST]

**Network drivers:[LIST]**
[*] Mellanox ConnectX InfiniBand adapters driver
[*] Marvell Libertas 8388 802.11b/g USB driver
[*] zr364xx V4L2 driver for USB webcams based on the zr364xx chipsets
[/LIST]

Download : [Mirror 1]("ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.4.tar.gz") | [Mirror 2]("ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.4.tar.bz2")

---

