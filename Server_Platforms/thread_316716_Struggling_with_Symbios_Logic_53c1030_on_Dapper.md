---
title: "Struggling with Symbios Logic 53c1030 on Dapper"
date: 2006-12-11
forum: Server Platforms
---

### Post by melon on 2006-12-11
Hi,

I wanted to set up Ubuntu 6.06 LTS Server to be a VMware Server host. This is a dual Xeon system on an Intel 7520JR2 board with 2G RAM and an external Promise VTrak 12110 storage. The storage attaches to the mainboard's SCSI backplane, all hw works fine.

The problem is that disk IO performance is very slow. First I tested the guest OSes (FreeBSD) then I tested the host (both with bonnie) and the results are really disappointing.

Both the host and the guest tests gave almost the same results:

Test run on the FreeBSD guest OS:
```
# time bonnie -d /filesrv/ -s 4096
...
              -------Sequential Output-------- ---Sequential Input-- --Random--
              -Per Char- --Block--- -Rewrite-- -Per Char- --Block--- --Seeks---
Machine    MB K/sec %CPU K/sec %CPU K/sec %CPU K/sec %CPU K/sec %CPU  /sec %CPU
         4096 16969 28.2  8098  7.5  7597  8.3 11760 18.6 15411 10.6  47.3  0.8
```

Test run on the host OS (Dapper):
```
# time bonnie -u root -d /vm -s 4096
...
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
stan             4G 16092  36  9563   1  6068   1 11202  24 49497   5 180.6   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16   294   1 +++++ +++   311   1   382   2 +++++ +++   117   0
stan,4G,16092,36,9563,1,6068,1,11202,24,49497,5,180.6,0,16,294,1,+++++,+++,311,1,382,2,+++++,+++,117,0
```

The point is that the same hardware performs at least 4 times faster on FreeBSD:
```
              -------Sequential Output-------- ---Sequential Input-- --Random--
              -Per Char- --Block--- -Rewrite-- -Per Char- --Block--- --Seeks---
Machine    MB K/sec %CPU K/sec %CPU K/sec %CPU K/sec %CPU K/sec %CPU  /sec %CPU
stan     4096 67903 61.8 59348 21.0  7413  4.1 38698 36.3 51930 12.9 676.0  1.5
stan     8192 67343 61.0 61342 22.2  7043  4.0 39466 37.1 52458 12.6 384.6  0.9
```

I tried not only the external storage but the internal two 74G Fujitsu U320 drives, which is:
```
# time bonnie -u root -d /vm -s 4096
...
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
stan             4G 39389  96 86195  32 33475   8 38358  80 83507   8 518.0   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  2675  98 +++++ +++ +++++ +++  2687  98 +++++ +++  8592  97
stan,4G,39389,96,86195,32,33475,8,38358,80,83507,8,518.0,0,16,2675,98,+++++,+++,+++++,+++,2687,98,+++++,+++,8592,97
```

All tests were run on almost empty volumes and the external scsi volume was built of four similar sata drives and are in RAID10 mode.

How can I fix the problem? How can I tune SCSI performance? The Ubuntu install is a standard install, with fresh updates and almost no additional software installed.

Here is the lspci output:
```
0000:00:00.0 Host bridge: Intel Corporation E7520 Memory Controller Hub (rev 0c)
0000:00:00.1 ff00: Intel Corporation E7525/E7520 Error Reporting Registers (rev 0c)
0000:00:01.0 System peripheral: Intel Corporation E7520 DMA Controller (rev 0c)
0000:00:02.0 PCI bridge: Intel Corporation E7525/E7520/E7320 PCI Express Port A (rev 0c)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:01:00.0 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A (rev 09)
0000:01:00.2 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge B (rev 09)
0000:02:03.0 Ethernet controller: Intel Corporation 82545GM Gigabit Ethernet Controller (rev 04)
0000:02:05.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 08)
0000:02:05.1 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 08)
0000:03:04.0 Ethernet controller: Intel Corporation 82546GB Gigabit Ethernet Controller (rev 03)
0000:03:04.1 Ethernet controller: Intel Corporation 82546GB Gigabit Ethernet Controller (rev 03)
0000:04:0c.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)

```

```
# uname -a
Linux stan 2.6.15-26-server #1 SMP Fri Sep 8 21:00:37 UTC 2006 i686 GNU/Linux
```

I will have to concentrate at least 3 virtual servers onto one host and it's simply not possible with this slow IO. Any help would be greatly appreciated.

---

### Post by melon on 2006-12-14
Any ideas?

---

