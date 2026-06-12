---
title: "faulty drive causes Raid 1 array endless syncing"
date: 2008-11-03
forum: Server Platforms
---

### Post by tasos.kleisas on 2008-11-03
Hi everybody,

I would like to share with you a problem I've been trying to solve and I would appreciate your feedback. Recently I set up a server with ubuntu 8.04. The machine is used primarily as a samba PDC/file server for a Windows Domain (the clients are Windows XP SP3 Professional machines). The server has 2 identical Samsung 500GB hard disks (sda and sdb). The disks are set up as software Raid 1, with md0 boot (500MB), md1 swap (8GB) and md2 as / 
```

Here's the output from df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md2              455G  5,8G  426G   2% /
varrun                2,0G  1,1M  2,0G   1% /var/run
varlock               2,0G     0  2,0G   0% /var/lock
udev                  2,0G   76K  2,0G   1% /dev
devshm                2,0G     0  2,0G   0% /dev/shm
/dev/md0              464M   65M  375M  15% /boot

```

The machine was deployed less than a month ago. A couple days ago, I noticed that sda starts resyncing, stops around 92% and starts all over again.
Here's the output from cat /proc/mdstat
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 sdb3[1] sda3[2]
      480078336 blocks [2/1] [_U]
      [========>............]  recovery = 41.9% (201335616/480078336) finish=68.1min speed=68180K/sec

md1 : active raid1 sda2[0] sdb2[1]
      7815552 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      489856 blocks [2/2] [UU]

unused devices: <none>

```
I searched kern.log and I have found that sdb drive has lots of read errors. The problem is that sda tries to sync to sdb but cannot read sdb, so an endless loop occurs.
here's the output from  mdadm --detail /dev/md2
```

/dev/md2:
        Version : 00.90.03
  Creation Time : Mon Oct 20 15:12:29 2008
     Raid Level : raid1
     Array Size : 480078336 (457.84 GiB 491.60 GB)
  Used Dev Size : 480078336 (457.84 GiB 491.60 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Mon Nov  3 17:59:15 2008
          State : active, degraded, recovering
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 44% complete

           UUID : 1d249b14:0a999dec:01f9e43d:ac30fbff
         Events : 0.235091

    Number   Major   Minor   RaidDevice State
       2       8        3        0      spare rebuilding   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3


```
The errors in sdb are like the following

```

Nov  3 17:10:38 server kernel: [188041.793468] ata4.00: status: { DRDY ERR }
Nov  3 17:10:38 server kernel: [188041.793471] ata4.00: error: { UNC }
Nov  3 17:10:38 server kernel: [188041.806220] ata4.00: configured for UDMA/133
Nov  3 17:10:38 server kernel: [188041.806236] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov  3 17:10:38 server kernel: [188041.806242] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Nov  3 17:10:38 server kernel: [188041.806249] Descriptor sense data with sense descriptors (in hex):
Nov  3 17:10:38 server kernel: [188041.806252]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
Nov  3 17:10:38 server kernel: [188041.806266]         00 66 da dc
Nov  3 17:10:38 server kernel: [188041.806277] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Nov  3 17:10:38 server kernel: [188041.806282] end_request: I/O error, dev sdb, sector 879155837
Nov  3 17:10:38 server kernel: [188041.806290] ata4: EH complete
Nov  3 17:10:38 server kernel: [188041.806315] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Nov  3 17:10:38 server kernel: [188041.806324] sd 3:0:0:0: [sdb] Write Protect is off
Nov  3 17:10:38 server kernel: [188041.806326] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov  3 17:10:38 server kernel: [188041.806339] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 17:10:39 server kernel: [188043.740543] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Nov  3 17:10:39 server kernel: [188043.740551] ata4.00: irq_stat 0x40000008
Nov  3 17:10:39 server kernel: [188043.740560] ata4.00: cmd 60/08:00:1d:d0:66/00:00:34:00:00/40 tag 0 ncq 4096 in
Nov  3 17:10:39 server kernel: [188043.740562]          res 41/40:00:1d:d0:66/33:00:34:00:00/40 Emask 0x409 (media error) <F>
Nov  3 17:10:39 server kernel: [188043.740566] ata4.00: status: { DRDY ERR }
Nov  3 17:10:39 server kernel: [188043.740569] ata4.00: error: { UNC }
Nov  3 17:10:39 server kernel: [188043.753322] ata4.00: configured for UDMA/133
Nov  3 17:10:39 server kernel: [188043.753333] ata4: EH complete
Nov  3 17:10:39 server kernel: [188043.753380] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Nov  3 17:10:39 server kernel: [188043.753389] sd 3:0:0:0: [sdb] Write Protect is off
Nov  3 17:10:39 server kernel: [188043.753392] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov  3 17:10:39 server kernel: [188043.753404] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 17:10:41 server kernel: [188045.671063] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Nov  3 17:10:41 server kernel: [188045.671071] ata4.00: irq_stat 0x40000008
Nov  3 17:10:41 server kernel: [188045.671080] ata4.00: cmd 60/08:00:1d:d0:66/00:00:34:00:00/40 tag 0 ncq 4096 in
Nov  3 17:10:41 server kernel: [188045.671082]          res 41/40:00:1d:d0:66/33:00:34:00:00/40 Emask 0x409 (media error) <F>
Nov  3 17:10:41 server kernel: [188045.671086] ata4.00: status: { DRDY ERR }
Nov  3 17:10:41 server kernel: [188045.671089] ata4.00: error: { UNC }
Nov  3 17:10:41 server kernel: [188045.683849] ata4.00: configured for UDMA/133
Nov  3 17:10:41 server kernel: [188045.683860] ata4: EH complete
Nov  3 17:10:41 server kernel: [188045.683922] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Nov  3 17:10:41 server kernel: [188045.683933] sd 3:0:0:0: [sdb] Write Protect is off
Nov  3 17:10:41 server kernel: [188045.683935] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov  3 17:10:41 server kernel: [188045.683948] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
--
Nov  3 17:10:53 server kernel: [188057.341547] ata4.00: configured for UDMA/133
Nov  3 17:10:53 server kernel: [188057.341558] ata4: EH complete
Nov  3 17:10:53 server kernel: [188057.341605] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Nov  3 17:10:53 server kernel: [188057.341615] sd 3:0:0:0: [sdb] Write Protect is off
Nov  3 17:10:53 server kernel: [188057.341617] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov  3 17:10:53 server kernel: [188057.341630] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 17:10:55 server kernel: [188059.284149] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Nov  3 17:10:55 server kernel: [188059.284156] ata4.00: irq_stat 0x40000008
Nov  3 17:10:55 server kernel: [188059.284165] ata4.00: cmd 60/08:00:d5:da:66/00:00:34:00:00/40 tag 0 ncq 4096 in
Nov  3 17:10:55 server kernel: [188059.284167]          res 41/40:00:dc:da:66/33:00:34:00:00/40 Emask 0x409 (media error) <F>
Nov  3 17:10:55 server kernel: [188059.284172] ata4.00: status: { DRDY ERR }
Nov  3 17:10:55 server kernel: [188059.284174] ata4.00: error: { UNC }
Nov  3 17:10:55 server kernel: [188059.296927] ata4.00: configured for UDMA/133
Nov  3 17:10:55 server kernel: [188059.296938] ata4: EH complete
Nov  3 17:10:55 server kernel: [188059.296985] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Nov  3 17:10:55 server kernel: [188059.296994] sd 3:0:0:0: [sdb] Write Protect is off
Nov  3 17:10:55 server kernel: [188059.296996] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov  3 17:10:55 server kernel: [188059.297009] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 17:10:57 server kernel: [188061.214667] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Nov  3 17:10:57 server kernel: [188061.214675] ata4.00: irq_stat 0x40000008
Nov  3 17:10:57 server kernel: [188061.214684] ata4.00: cmd 60/08:00:d5:da:66/00:00:34:00:00/40 tag 0 ncq 4096 in
Nov  3 17:10:57 server kernel: [188061.214686]          res 41/40:00:dc:da:66/33:00:34:00:00/40 Emask 0x409 (media error) <F>
Nov  3 17:10:57 server kernel: [188061.214691] ata4.00: status: { DRDY ERR }
Nov  3 17:10:57 server kernel: [188061.214694] ata4.00: error: { UNC }
Nov  3 17:10:57 server kernel: [188061.228287] ata4.00: configured for UDMA/133
Nov  3 17:10:57 server kernel: [188061.228302] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov  3 17:10:57 server kernel: [188061.228308] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Nov  3 17:10:57 server kernel: [188061.228315] Descriptor sense data with sense descriptors (in hex):
Nov  3 17:10:57 server kernel: [188061.228319]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
Nov  3 17:10:57 server kernel: [188061.228333]         00 66 da dc
Nov  3 17:10:57 server kernel: [188061.228339] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Nov  3 17:10:57 server kernel: [188061.228348] end_request: I/O error, dev sdb, sector 879155925
Nov  3 17:10:57 server kernel: [188061.228359] ata4: EH complete
Nov  3 17:10:57 server kernel: [188061.228378] raid1: sdb: unrecoverable I/O read error for block 878175872
Nov  3 17:10:57 server kernel: [188061.229163] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Nov  3 17:10:57 server kernel: [188061.229173] sd 3:0:0:0: [sdb] Write Protect is off
Nov  3 17:10:57 server kernel: [188061.229176] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Nov  3 17:10:57 server kernel: [188061.229189] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 17:10:57 server kernel: [188061.230361] md: md2: recovery done.
Nov  3 17:10:58 server kernel: [188061.764850] RAID1 conf printout:
Nov  3 17:10:58 server kernel: [188061.764857]  --- wd:1 rd:2
Nov  3 17:10:58 server kernel: [188061.764861]  disk 0, wo:1, o:1, dev:sda3
Nov  3 17:10:58 server kernel: [188061.764864]  disk 1, wo:0, o:1, dev:sdb3
Nov  3 17:10:58 server kernel: [188061.791516] RAID1 conf printout:
Nov  3 17:10:58 server kernel: [188061.791521]  --- wd:1 rd:2
Nov  3 17:10:58 server kernel: [188061.791524]  disk 1, wo:0, o:1, dev:sdb3
Nov  3 17:10:58 server kernel: [188061.791538] RAID1 conf printout:
Nov  3 17:10:58 server kernel: [188061.791540]  --- wd:1 rd:2
Nov  3 17:10:58 server kernel: [188061.791543]  disk 0, wo:1, o:1, dev:sda3
Nov  3 17:10:58 server kernel: [188061.791547]  disk 1, wo:0, o:1, dev:sdb3
Nov  3 17:10:58 server kernel: [188061.791626] md: recovery of RAID array md2
Nov  3 17:10:58 server kernel: [188061.791628] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Nov  3 17:10:58 server kernel: [188061.791630] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
Nov  3 17:10:58 server kernel: [188061.791633] md: using 128k window, over a total of 480078336 blocks.

```
I am afraid that the drive will soon fail and I will lose all of my data. what can I do to replace the faulty drive?

---

### Post by fjgaude on 2008-11-03
The normal way to remove a failing, failed drive from an **mdadm** software array is to fail, remove, the old; add back a new drive. I think you can do this on a mounted, running array, of course using mdadm:

```
sudo mdadm /dev/md[n] -f  or -r  or  -a  /dev/sd[nn]      # fail, remove, add device
```

I don't do raid1 arrays but with a little study that should work:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
/usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Let us know how you are doing.

---

### Post by psusi on 2008-11-03
It looks like your sda failed and was replaced, and in the process of trying to resync, sdb is having media errors, so the array can not be correctly repaired.  At this point your raid0 is failed and you need to back up all of your data, replace or repair the bad sdb, and reformat the raid0 from scratch.

You might look at the smartmontools package to run low level diagnostics on the disk and possibly repair the bad sectors if there are only a few of them, but whatever data was stored in them is lost.

---

### Post by tasos.kleisas on 2008-11-04
The resync started after reboot. So I will disable write caching on the drives, force a file system check on reboot with touch /forcefsck and reboot with my fingers crossed.

---

### Post by fjgaude on 2008-11-04
You can watch the rebuilding with this command:

```
sudo watch cat /proc/mdstat
```

I noramally let things completely finish before doing anything else to an array.

---

### Post by ptader on 2008-11-04
psusi,

"It looks like your sda failed and was replaced..."

I'm curious how you came to this conclusion.

---

### Post by psusi on 2008-11-04
> **ptader said:**
> psusi,

"It looks like your sda failed and was replaced..."

I'm curious how you came to this conclusion.

Because mdadm says that sda is the drive that is out of sync, and it is trying to copy data from sdb to sda to get them back in sync, but some of the sectors on sdb can't be read.

---

### Post by tasos.kleisas on 2008-11-09
I got a new identical drive, replaced the faulty one and I reinstalled the system with the required packages (ebox, etc...). Afterwards, I restored my files from a backup I've taken and everything is back to normal. Now the disks sync ok.

---

### Post by fjgaude on 2008-11-09
Great, glad you found your problem, buying and installing a new drive.

---

