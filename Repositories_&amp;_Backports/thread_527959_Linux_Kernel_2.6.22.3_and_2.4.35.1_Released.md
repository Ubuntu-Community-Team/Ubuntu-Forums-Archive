---
title: "Linux Kernel 2.6.22.3 and 2.4.35.1 Released"
date: 2007-08-17
forum: Repositories &amp; Backports
---

### Post by Dark Star on 2007-08-17
The 2.6.22.3 version from the 2.6 stable Linux kernel branch was released last night along with the 2.4.35.1 version of the 2.4 stable kernel branch. The 2.6.22.3 release contains some bugfixes and new power saving functions for laptop users:

"This release has a few bugfixes so all users of the 2.6.22 series are encouraged to update to it. Especially people with laptops, they will appreciate the power savings in this release.", stated Greg Kroah-Hartman.

**Changes from 2.6.22.2 to 2.6.22.3:**
[LIST]
[*] fix oops in __audit_signal_info()
[*] direct-io: fix error-path crashes
[*] powerpc: Fix size check for hugetlbfs
[*] stifb: detect cards in double buffer mode more reliably
[*] pata_atiixp: add SB700 PCI ID
[*] PPC: Revert "[POWERPC] Add 'mdio' to bus scan id list for platforms with QE UEC"
[*] random: fix bound check ordering (CVE-2007-3105)
[*] softmac: Fix deadlock of wx_set_essid with assoc work
[*] PPC: Revert "[POWERPC] Don't complain if size-cells == 0 in prom_parse()"
[*] ata_piix: update map 10b for ich8m
[*] CPUFREQ: ondemand: fix tickless accounting and software coordination bug
[*] CPUFREQ: ondemand: add a check to avoid negative load calculation
[/LIST]

**The 2.6.22 Linux kernel includes features and drivers such as:**
[LIST]
[*] New Slab allocator: SLUB
[*] New Wireless stack
[*] New Firewire stack
[*]Signal/timer events notifications through file descriptors
[*] Blackfin architecture
[*] UBI
[*] Secure RxRPC sockets
[*] Process footprint measurement facility
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

**Network drivers:**
[LIST]
[*] Mellanox ConnectX InfiniBand adapters driver
[*] Marvell Libertas 8388 802.11b/g USB driver
[*] zr364xx V4L2 driver for USB webcams based on the zr364xx chipsets
[/LIST]

The Linux Kernel is the essential part of all Linux Distributions, responsible for resource allocation, low-level hardware interfaces, security, simple communications, and basic file system management.

Linux is a clone of the Unix operating system, initially written from scratch by Linus Torvalds, assisted by a loosely-knit team of hackers across the Net. It aims to achieve POSIX and Single UNIX Specification compliance.

Source  : [http://article.gmane.org/gmane.linux.kernel/570815](http://article.gmane.org/gmane.linux.kernel/570815)
Download :[ Mirror 1]("ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.3.tar.gz") | [Mirror 2]("ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.3.tar.bz2")

---

### Post by gOLdenHaWK3D on 2007-09-02
Thanx for the info dude :)

---

