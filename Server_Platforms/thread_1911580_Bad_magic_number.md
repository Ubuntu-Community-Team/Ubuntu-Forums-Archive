---
title: "Bad magic number"
date: 2012-01-19
forum: Server Platforms
---

### Post by kalosh on 2012-01-19
Hello.
While mounting "working until today" disk I have following error:
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1.
mke2fs says:
```
mke2fs 1.41.14 (22-Dec-2010)
Filesystem label=
Typ OS: Linux
Size of block=4096 (log=2)
Size of fragment=4096 (log=2)
Stride=0 bloków, szeroko&#347;&#263; Stripe=0 bloków
4890624 i-w&#281;z&#322;ów, 19537430 bloków
976871 bloków (5.00%) reserved to superuser
Pierwszy blok danych=0
Maksymalna liczba bloków systemu plików=0
597 grup bloków
32768 bloków w grupie, 32768 fragmentów w grupie
8192 i-w&#281;z&#322;ów w grupie
Backup copies of super-block (translated):
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424
```
I have tried the backup block numbers and still e2fsck cannot open the disk.
partition table (read from fdisk):
```
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
heads: 81, sectors/path: 63, cylinders: 30629, all sectors: 156301488
Unit = sectors, czyli 1 * 512 = 512 bytes
Sector size (logic/physical) in bytes: 512 / 512
Size in/out (minimal/optimal) in bytes: 512 / 512
Disk id: 0x00000001

device boot flag begin end blocks ID  System
/dev/sdb1            2048   156301487    78149720   83  Linux

```
Do you have any idea how to force this to work? Disk was being used by me couple of weeks and previously by some one else. It was formatted by my to ext4. It has 20GB of data in it.
Any ideas?
Best regards, Dawid.

---

### Post by rubylaser on 2012-01-19
If all of the superblocks aren't working to restore the filesystem, I'd be restoring from backup (it's only 20GB, I hope you have a backup).  Have, you checked the disk with smartmontools? If there is no backup, you're going to need to use a recovery tool like scapel, or photorec.

---

### Post by kalosh on 2012-01-19
Thanks. The data was not priceless so no problem with that. I was trying to fix that one more time and I typed mk2fs command without any switch (by mistake) and my problem (with the data) disappeared.
Have a nice day.

---

