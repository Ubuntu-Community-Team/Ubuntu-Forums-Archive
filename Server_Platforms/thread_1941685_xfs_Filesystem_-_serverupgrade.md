---
title: "xfs Filesystem - serverupgrade"
date: 2012-03-16
forum: Server Platforms
---

### Post by hallo200 on 2012-03-16
Dear Forum,

Recently I upgraded ubuntu server from 8.04 to 10.04 32(bit).
I installed maverick Backportskernel.
I use two HP MAS60 with E500 Controller.

There was never a Problem with a xfs file system.

Yesterday I received:

Filesystem "cciss/c0d0p1":XFS internal error xfs_trans_cancel at line  1731 of file  /build/buildd/linx-lts-backport-maverick-2.6.35/fs/xfs/xfs_trans.c  Caller 0xf917d8b8

Any ideas?

There is a rsync Backup configured (rsnapshot). I get this in the rsnapshot report:
/bin/cp: cannot stat `/srv/backup/file': Cannot allocate memory

?

with kind regards
mike

---

