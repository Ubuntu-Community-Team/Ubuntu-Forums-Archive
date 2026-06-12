---
title: "disk failure"
date: 2010-03-14
forum: Server Platforms
---

### Post by hr4_ on 2010-03-14
is it possible to fix my disk, at least partially ?

SCSI device sda: 976771055 512-byte hdwr sectors (500107 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
SCSI device sda: 976771055 512-byte hdwr sectors (500107 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
 sda: sda1 sda2
sd 2:0:0:0: Attached scsi disk sda
end_request: I/O error, dev sda, sector 208103
sda : READ CAPACITY failed.
sda : status=0, message=00, host=4, driver=00
sda : sense not available.
sda: Write Protect is off
sda: Mode Sense: 00 00 00 00
sda: asking for cache data failed
sda: assuming drive cache: write through
sda: detected capacity change from 500106780160 to 1073741824
sda : READ CAPACITY failed.
sda : status=0, message=00, host=4, driver=00
sda : sense not available.
sda: Write Protect is off
sda: Mode Sense: 00 00 00 00
sda: asking for cache data failed
sda: assuming drive cache: write through
 sda:<6>sd 2:0:0:0: SCSI error: return code = 0x00040000
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
Dev sda: unable to read RDB block 0
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0


dd if=/dev/sda of=/dev/null count=1 bs=512
dd: reading `/dev/sda': Input/output error
0+0 records in
0+0 records out

---

### Post by dudumomo on 2010-03-15
Hi hr4
Can you tell us a bit more about your problem ?
I guess you got this problem when you try to start your computer right ?
How did this problem occur ?

I would suggest you to boot on a LiveCD or LiveUSB and to try "testdisk" package.

---

