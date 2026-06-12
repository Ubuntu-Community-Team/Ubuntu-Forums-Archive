---
title: "Need some smartmontools help, is this disk toast???"
date: 2016-12-29
forum: Server Platforms
---

### Post by darkod on 2016-12-29
Hi all,

Last night I noticed one of my fileserver mdadm raid1 disks is marked as failed (F) and I need some help to figure out if it's definitely toast.

I first tried to add it back to the array and it looked like it worked initially. Due to size (2TB) I had to leave it rebuilding overnight but this morning it was (F) again.

So I tried to use smartmontools and it seems it can't even read the disk correctly, although parted output looks normal. Outputs:
```
root@file-srv:~# smartctl -i /dev/sdb
smartctl 6.2 2013-07-26 r3841 [i686-linux-4.4.0-42-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Vendor:               /1:0:0:0
Product:              
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46
scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```
```
root@file-srv:~# smartctl -c /dev/sdb
smartctl 6.2 2013-07-26 r3841 [i686-linux-4.4.0-42-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


SCSI device successfully opened


Use 'smartctl -a' (or '-x') to print SMART (and more) information
```
```
root@file-srv:~# smartctl -H /dev/sdb
smartctl 6.2 2013-07-26 r3841 [i686-linux-4.4.0-42-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF READ SMART DATA SECTION ===
Log Sense failed, IE page [scsi response fails sanity test]
root@file-srv:~# smartctl -a -d ata /dev/sdb
smartctl 6.2 2013-07-26 r3841 [i686-linux-4.4.0-42-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


Read Device Identity failed: Input/output error


A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```
```
root@file-srv:~# parted /dev/sdb unit GiB print
Model: ATA ST2000DM001-9YN1 (scsi)
Disk /dev/sdb: 1863GiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start    End      Size     File system  Name  Flags
 1      0.00GiB  0.00GiB  0.00GiB               GRUB  bios_grub
 2      0.00GiB  32.0GiB  32.0GiB               ROOT  raid
 3      32.0GiB  1863GiB  1831GiB               LVM   raid
```

Even though parted output seems normal from all the other smartctl commands it seems to me like time for a new disk. Anything else I can try before purchasing one? Thanks in advance.

By the way, it's "only" 4 years old 2TB Seagate.

PS. Notice how smartctl says user capacity 600PB??? I wish...

---

### Post by sudodus on 2016-12-29
I think that the drive is bad, when smartctl has such problems. But I would [try to] wipe the beginning of it, overwrite at least the first mibibyte with zeros and try again with smartctl. Maybe there are some data that are confusing the tool.

---

### Post by darkod on 2016-12-29
Hmmm, even zeroing out seems to fail:
```
root@file-srv:~# dd if=/dev/zero of=/dev/sdb bs=1K count=1024
dd: error writing &#8216;/dev/sdb&#8217;: Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00404477 s, 0.0 kB/s
```

I think it's time to start shopping for a new disk... :(

---

### Post by sudodus on 2016-12-29
I'm sorry, but I think so too.

---

### Post by darkod on 2016-12-29
I might be opening a can of worms here, but because this will be for 24/7 home NAS with low traffic, should I be looking into NAS models or they are not worth the price premium?

The died disk is a standard Seagate Barracuda ST2000DM001, but I wouldn't say it was related to the failure. My NAS has ubuntu server and very low traffic and I am wondering if current Seagate prices justify NAS HDD model.

For example I can get the new generation Barracuda ST3000DM008 for 95&#8364; and the Ironwolf ST3000VN007 for 120&#8364;. The Ironwolf is designed for NAS but is it really worth 26% price premium???

---

### Post by sudodus on 2016-12-29
I think it is worth the premium price to get a higher quality drive. I have moved from cheap HDDs to more expensive ones. They work better and run longer (on the average a lot longer, but you can't tell for one individual drive).

---

### Post by darkod on 2016-12-30
I have ordered a Seagate Ironwolf 3TB, lets see how it goes... I consider this solved but if anyone wants to chip in with an opinion, please feel free...

On the other hand it is a bit disappointing that after M&A's it seems not many brands have left to pick from. HGST is owned by WD now too, so basically you can select from Seagate and WD... Toshiba seems to be on its own still but I'm not sure how good they are with HDDs.

---

### Post by sudodus on 2016-12-30
Good luck with the ironwolf :-)

---

