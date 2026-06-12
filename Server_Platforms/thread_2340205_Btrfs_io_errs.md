---
title: "Btrfs io_errs"
date: 2016-10-16
forum: Server Platforms
---

### Post by Speculos on 2016-10-16
Evening all,

I'm having issue on a BTRFS FS, recently I've just lost a disk on a RAID5 array (mdadm), I've replaced the disk and rebuild the array, but it seems that there was some corruption on a particular file cause by the failing disk.

I've try deleting and recreating the file without succes still having issues, such as can't backup the file on my another backup server, having some checksum issue with rsync.

I've try several actions to try to correct this, but first let's show you the errors I've got on the dmesg:

```

BTRFS error (device dm-0): bdev /dev/mapper/vg0-data_01 errs: wr 6, rd 74, flush 0, corrupt 0, gen 0
BTRFS error (device dm-0): bdev /dev/mapper/vg0-data_01 errs: wr 6, rd 75, flush 0, corrupt 0, gen 0
BTRFS error (device dm-0): bdev /dev/mapper/vg0-data_01 errs: wr 6, rd 76, flush 0, corrupt 0, gen 0
BTRFS error (device dm-0): bdev /dev/mapper/vg0-data_01 errs: wr 6, rd 77, flush 0, corrupt 0, gen 0
...
BTRFS error (device dm-0): bdev /dev/mapper/vg0-data_01 errs: wr 6, rd 104, flush 0, corrupt 0, gen 0
BTRFS error (device dm-0): bdev /dev/mapper/vg0-data_01 errs: wr 6, rd 105, flush 0, corrupt 0, gen 0
BTRFS error (device dm-0): bdev /dev/mapper/vg0-data_01 errs: wr 6, rd 106, flush 0, corrupt 0, gen 0

```

```

BTRFS warning (device dm-0): csum failed ino 2257866 off 7643377664 csum 102040691 expected csum 2397698439
BTRFS warning (device dm-0): csum failed ino 2257890 off 8949051392 csum 4170460904 expected csum 1268509404
BTRFS warning (device dm-0): csum failed ino 2257890 off 8949071872 csum 1978651236 expected csum 3474740822
BTRFS warning (device dm-0): csum failed ino 2257890 off 8949051392 csum 744554306 expected csum 1268509404
BTRFS warning (device dm-0): csum failed ino 2257890 off 8949051392 csum 3372512547 expected csum 1268509404
BTRFS warning (device dm-0): csum failed ino 2257890 off 8949071872 csum 1418956053 expected csum 3474740822
BTRFS warning (device dm-0): csum failed ino 2259365 off 7819276288 csum 4245020043 expected csum 419260330

```

So as I said, I've try to repair the FS

```

sudo btrfs check /dev/mapper/vg0-data_01

```

```
Checking filesystem on /dev/mapper/vg0-data_01
UUID: 15596747-d913-4ff1-b477-b21a8f8b48c5
checking extents
checking free space cache
checking fs roots
checking csums
checking root refs
found 18420688228210 bytes used err is 0
total csum bytes: 17969634424
total tree bytes: 19782565888
total fs tree bytes: 66846720
total extent tree bytes: 174063616
btree space waste bytes: 1083496681
file data blocks allocated: 18404166070272
 referenced 18403623936000
```

And also with the repair options

```
sudo btrfs check --repair /dev/mapper/vg0-data_01
```

```
enabling repair mode
Checking filesystem on /dev/mapper/vg0-data_01
UUID: 15596747-d913-4ff1-b477-b21a8f8b48c5
checking extents
Fixed 0 roots.
checking free space cache
cache and super generation don't match, space cache will be invalidated
checking fs roots
checking csums
checking root refs
found 18398670118767 bytes used err is 0
total csum bytes: 17948154380
total tree bytes: 19760021504
total fs tree bytes: 66846720
total extent tree bytes: 174030848
btree space waste bytes: 1082888653
file data blocks allocated: 18382169980928
 referenced 18381627842560
```

I've also try a scrub on It

```
sudo btrfs scrub start /dev/mapper/vg0-data_01
```

```
scrub status for 15596747-d913-4ff1-b477-b21a8f8b48c5
        scrub started at Sat Oct 15 22:29:48 2016 and finished after 07:22:32
        total bytes scrubbed: 16.80TiB with 16 errors
        error details: read=16
        corrected errors: 0, uncorrectable errors: 16, unverified errors: 0
```

And came with this error message pretty clear saying that errors are uncorrectable

```
BTRFS error (device dm-0): bdev /dev/mapper/vg0-data_01 errs: wr 6, rd 94, flush 0, corrupt 0, gen 0
BTRFS error (device dm-0): unable to fixup (regular) error at logical 34040065896448 on dev /dev/mapper/vg0-data_01
BTRFS warning (device dm-0): i/o error at logical 34040065900544 on dev /dev/mapper/vg0-data_01, sector 35071280288, root 5, inode 2257890, offset 8949088256, length 4096, links 1 (path: Videos/Pilotage/session_matin.mkv)
```

Here the actual status of my BTRFS FS (LV)

```
sudo btrfs device stats /data_01/
```

```
[/dev/mapper/vg0-data_01].write_io_errs   6
[/dev/mapper/vg0-data_01].read_io_errs    101
[/dev/mapper/vg0-data_01].flush_io_errs   0
[/dev/mapper/vg0-data_01].corruption_errs 0
[/dev/mapper/vg0-data_01].generation_errs 0
```

I've try everything not dangerous to test on the FS, I'm a bit lost now, do you have any ideas how to fix this ?

**More informations about my server**
OS: Ubuntu 16.04.1 LTS
MDADM Version: mdadm - v3.3 - 3rd September 2013
LVM Version: 2.02.133(2) (2015-10-30) / Library version: 1.02.110 (2015-10-30) / Driver version: 4.34.0
BTRFS Version: btrfs-progs v4.4

Best regards.

Speculos.

---

