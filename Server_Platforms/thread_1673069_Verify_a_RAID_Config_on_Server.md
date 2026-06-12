---
title: "Verify a RAID Config on Server"
date: 2011-01-21
forum: Server Platforms
---

### Post by markosjal on 2011-01-21
We recently ordered a new server with Hardware RAID 1 and Ubuntu Server 64 bit. After activation, I installed Gnome Desktop and VNC Server. 

The question I have is whether we truly got a hardware RAID or this is a software RAID. Since we pay another monthly fee for a Hardware RAID controller and it appears this RAID may be integrated on the Motherboard. 

lspci -v reports the following;

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
	Subsystem: Super Micro Computer Inc Device d880
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
	I/O ports at 1c50 [size=8]
	I/O ports at 1c44 [size=4]
	I/O ports at 1c48 [size=8]
	I/O ports at 1c40 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at dc000800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci


The following attachments are from my correspondence with the DC. The first three screenshots were captured over VNC by myself. Collectively they appear to show a problem with the RAID in my opinion 

The BIOS setup was sent to me by the DC

and lastly this was later sent to me by the DC to support that it was working as well as the same 3 screens I previously captured.


~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/mapper/isw_ddafegdfbc_Volume01
440G 14G 405G 4% /
none 4.0G 212K 4.0G 1% /dev
none 4.0G 96K 4.0G 1% /dev/shm
none 4.0G 96K 4.0G 1% /var/run
none 4.0G 0 4.0G 0% /var/lock
none 4.0G 0 4.0G 0% /lib/init/rw
none 440G 14G 405G 4% /var/lib/ureadahead/debugfs




How do I know that this is a HARDWARE RAID and not some fakeraid that will be useless in a drive failure? 

It also looks to me like the swap drive is on a single drive when it too should be on both drives, correct?

We need to ensure this is a hardware RAID for data integrity reasons. It seems having swap not raided alone means that one drive failure can leave us dead in the water.

---

### Post by Vegan on 2011-01-21
Your machine is using a motherboard RAID array. A real controller costs $$$$.

I keep my server *in* shop so I know exactly what is in the box and I can fix it myself when it croaks.

---

### Post by markosjal on 2011-01-21
Vegan,

Rather than telling me how you do it, why dont you qualify your answer by saying why you say it is a Mobo RAID, and if you mean it is a software RAID why you say that. Your post really is more of your opinion against using a data center and that is ridiculous.

---

### Post by trundlenut on 2011-01-23
If you had proper hardware raid then ubuntu wouldn't see the individual disks.
You have fakeraid which is a sort of harlfway house where the mobo uses to OS to provide the raid capability.

Here is what fdisk -l spits out for a server with 4 hard drives running software raid

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6bd0f373

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux RAID autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9e2b0f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux RAID autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00067ece

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         730     5858304   fd  Linux RAID autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *         730       19458   150430720   fd  Linux RAID autodetect

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000da364

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         730     5858304   fd  Linux RAID autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdd2   *         730       19458   150430720   fd  Linux RAID autodetect

Disk /dev/md1: 500.1 GB, 500105150464 bytes
2 heads, 4 sectors/track, 122095984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 5998 MB, 5998837760 bytes
2 heads, 4 sectors/track, 1464560 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md2: 154.0 GB, 154040991744 bytes
2 heads, 4 sectors/track, 37607664 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

```

I'll post the output from a server running proper hardware raid in a bit.

---

### Post by trundlenut on 2011-01-23
Here is the same output from my server with proper hardware raid, this machine has 5 drives, 2 as raid1 and three as raid5.  Ubuntu sees it as two drives and is oblivious to the actual hardware.

```
Disk /dev/sda: 36.4 GB, 36364615680 bytes
255 heads, 63 sectors/track, 4421 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000727e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4329    34772661   83  Linux
/dev/sda2            4330        4421      738990    5  Extended
/dev/sda5            4330        4421      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 145.5 GB, 145479434240 bytes
255 heads, 63 sectors/track, 17686 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07c33a33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17686   142062763+  83  Linux
```

---

