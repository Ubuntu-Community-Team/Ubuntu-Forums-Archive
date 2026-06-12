---
title: "KVM Guest on NVME - Half the Drive Throughput"
date: 2017-12-30
forum: Server Platforms
---

### Post by bsntech on 2017-12-30
Just installed a Samsung 960 EVO 500 GB NVME drive in my system using a PCIe interface card.

On the host machine:

```
hdparm -Tt /dev/nvme0n1p1

/dev/nvme0n1p1:
 Timing cached reads:   10044 MB in  2.00 seconds = 5025.19 MB/sec
 Timing buffered disk reads: 4106 MB in  3.00 seconds = 1368.23 MB/sec

```

Not as good as what the drive is rated for, but significantly faster than the SATA III SSD I had prior.

This is an Ext4 formatted partition and it is mounted to /VMs - which is how KVM accesses the raw files for the guest machines.  Configuration is set to VirtIO as disk bus, raw storage format, and "none" for cache mode.

If I log into the guest, the speed is significantly worse:

```
hdparm -Tt /dev/vda

/dev/vda:
 Timing cached reads:   9170 MB in  2.00 seconds = 4588.24 MB/sec
 Timing buffered disk reads: 2104 MB in  3.00 seconds = 700.60 MB/sec

```

With the prior SATA III SSD drive, the speeds were very close - maybe 10 MB/sec slower on the guest than the host OS.  But the speeds are only half.

Has anyone else tried using an NVMe drive and received similar results?  Looking for any guidance/advice on what could be done to bring the throughput more in line with what the host OS can do.

---

### Post by twoj on 2018-02-08
Have you had any success figuring this out?

---

