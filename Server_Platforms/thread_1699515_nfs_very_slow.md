---
title: "nfs very slow"
date: 2011-03-03
forum: Server Platforms
---

### Post by spakker on 2011-03-03
Very slow nfs transfers - between ESX4 and Ubuntu server 10.10, with a sata disk shared via NFS, over a Intel Pro 1000 desktop NIC.

fstab:
/dev/sdb1       /export         xfs     rw                      0       0

exports:
/export         10.0.0.0/24(rw,no_root_squash,async) 127.0.0.1/8(rw)

Mounted on ESX4.0:
[root@esx03 nfsvm01]# dd if=/dev/zero of=test1 bs=1K count=16K
16384+0 records in
16384+0 records out
16777216 bytes (17 MB) copied, 2.68705 seconds, 6.2 MB/s

Local test:
root@ubuntu01:/export/vm# dd if=/dev/zero of=test1 bs=1K count=512K
524288+0 records in
524288+0 records out
536870912 bytes (537 MB) copied, 7.19362 s, 74.6 MB/s

jperf/iperf between a windows client and the Ubuntu server gives me about 280Mbit/sec - so in the region of 37.5 MB/s.

Results are consistent even when I vary the block size significantly.

I can copy files faster with scp than nfs.

What can I do?

---

