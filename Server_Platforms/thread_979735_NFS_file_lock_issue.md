---
title: "NFS file lock issue"
date: 2008-11-12
forum: Server Platforms
---

### Post by rozilla on 2008-11-12
My desktops are having login issue. You login then the login window disappears, as if it's about to show your gnome-desktop and then nothing happens. After a few minutes you get an empty white box at the top left corner of your screen, and that's it.
vi /var/log/kern.log gives the following output.

```
Nov 12 07:51:25 files kernel: [   88.176773]   Using irq 21
Nov 12 07:51:25 files kernel: [   88.362565] ipmi: interfacing existing BMC (man_id: 0x00000b, prod_id: 0x0000, dev_id: 0x11)
Nov 12 07:51:25 files kernel: [   88.362579] IPMI kcs interface initialized
Nov 12 07:51:25 files kernel: [   88.465402] loop: module loaded
Nov 12 07:51:25 files kernel: [   88.511022] lp: driver loaded but no devices found
Nov 12 07:51:25 files kernel: [   88.669164] Adding 489940k swap on /dev/cciss/c0d0p6.  Priority:-1 extents:1 across:489940k
Nov 12 07:51:25 files kernel: [   88.900262] EXT3 FS on cciss/c0d0p7, internal journal
Nov 12 07:51:25 files kernel: [   90.921521] bnx2: eth0 NIC Copper Link is Up, 1000 Mbps full duplex
Nov 12 07:51:25 files kernel: [  172.907304] kjournald starting.  Commit interval 5 seconds
Nov 12 07:51:25 files kernel: [  172.907396] EXT3 FS on cciss/c0d0p1, internal journal
Nov 12 07:51:25 files kernel: [  172.907403] EXT3-fs: mounted filesystem with ordered data mode.
Nov 12 07:51:25 files kernel: [  173.002263] kjournald starting.  Commit interval 5 seconds
Nov 12 07:51:25 files kernel: [  173.010937] EXT3 FS on cciss/c0d0p8, internal journal
Nov 12 07:51:25 files kernel: [  173.010942] EXT3-fs: mounted filesystem with ordered data mode.
Nov 12 07:51:25 files kernel: [  173.011499] kjournald starting.  Commit interval 5 seconds
Nov 12 07:51:25 files kernel: [  173.011569] EXT3 FS on cciss/c0d0p5, internal journal
Nov 12 07:51:25 files kernel: [  173.011574] EXT3-fs: mounted filesystem with ordered data mode.
Nov 12 07:51:25 files kernel: [  176.544305] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 12 07:51:25 files kernel: [  182.709253] RPC: Registered udp transport module.
Nov 12 07:51:25 files kernel: [  182.709256] RPC: Registered tcp transport module.
Nov 12 07:51:25 files kernel: [  184.727370] No dock devices found.
Nov 12 07:51:26 files kernel: [  186.463174] NET: Registered protocol family 10
Nov 12 07:51:26 files kernel: [  186.463399] lo: Disabled Privacy Extensions
Nov 12 07:51:37 files kernel: [  197.386185] eth0: no IPv6 routers present
Nov 12 07:51:38 files kernel: [  199.019107] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Nov 12 07:51:38 files kernel: [  199.075939] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Nov 12 07:51:38 files kernel: [  199.078616] NFSD: starting 90-second grace period
Nov 12 09:05:18 files kernel: [ 4610.287570] statd: server localhost not responding, timed out
Nov 12 09:05:18 files kernel: [ 4610.287582] nsm_mon_unmon: rpc failed, status=-5
Nov 12 09:05:18 files kernel: [ 4610.287597] lockd: cannot unmonitor fct107
```

I googled **nsm_mon_unmon: rpc failed, status=-5** and it seems like it's some kind of NFS file lock issue. But so far I haven't come across any way to resolve the issue. It seems like an NFS issue? And so I've tried restarting nfs-common and nfs-kernel-server. But that doesn't work. In fact login is not possible until I reboot the fileserver.
Any ideas?
I'm running Ubuntu Hardy desktops, which mount their home dirs via NFS on a Hardy server.

---

