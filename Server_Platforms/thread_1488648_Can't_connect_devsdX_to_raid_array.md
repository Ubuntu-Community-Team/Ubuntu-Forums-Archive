---
title: "Can't connect /dev/sdX to raid array"
date: 2010-05-20
forum: Server Platforms
---

### Post by a.santini on 2010-05-20
Hello everybody,
I have a problem with my Ubuntu 8.04 server with two hard drives in raid1.
An hard disk crashed and I had to replace it (is the primary disk 750GB).
I replace it with another hard disk of 1000GB.
I performed the usual procedures for changing and rebuilt the same partition table.
I have 3 partitions:
md0 = /boot
md1 = /
md2 = swap

The problem is that I can not add the partition / dev/sda3 in the array md2. With command : mdamd --examine /dev/sda3 I obtain : mdadm: No md superblock detect on /dev/sda3
How can I fix this error?
Thanks

---

