---
title: "Software RAID 10 power failure - 12.04"
date: 2016-05-18
forum: Server Platforms
---

### Post by papapig on 2016-05-18
Hi all.

I had a power failure on a server (Ubuntu 12.04.3 LTS ) with a raid 10 array.

When I restored the power, in dmesg there was the message:

```
md/raid1:md1: not clean -- starting background reconstruction
```

and it started resyncing the array.

I think the resync started because of the power failure, isn't it?

My question is: when the resync process will be complete, can I exclude that there are bad sectors on the disks due to the power failure?

Or have I to run badblocks or a similar tool from the Ubuntu Rescue Remix live CD?

In this case, which tool is much suitable for checking hard disks?

Thanks to all.

---

### Post by frostschutz on 2016-05-20
Don't use badblocks.

> My question is: when the resync process will be complete, can I exclude  that there are bad sectors on the disks due to the power failure?

It will read all data and write it to the disk that was out of sync. So in theory it's a good test but in case of RAID-10 it may read data only from one disk not of its mirror, so the mirror isn't tested.

Besides: You really don't want a RAID resync, to be your first read test in years. You should set up disk monitoring, regular RAID checks, regular disk self-tests using SMART.

> In this case, which tool is much suitable for checking hard disks?

`smartctl -t long /dev/disk` (then wait a long time...)
`smartctl -a /dev/disk` (smartmontools)

---

### Post by papapig on 2016-05-25
> **frostschutz said:**
> Don't use badblocks.



Ach.. I already used it.

Why I should not use badblocks?

I did a 

```
badblocks -v -s /dev/sda
```

and

```
badblocks -v -s /dev/sdb
```

that should be a read-only test.

No errors found, anyway.

Now I also launched a -t long test on all my disks..

Thank you

---

