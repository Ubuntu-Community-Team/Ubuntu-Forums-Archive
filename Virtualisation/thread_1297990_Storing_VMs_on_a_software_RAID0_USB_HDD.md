---
title: "Storing VMs on a software RAID0 USB HDD"
date: 2009-10-22
forum: Virtualisation
---

### Post by ricojonah on 2009-10-22
A while ago, I decided to start toying around with the idea of running all of my virtualbox machines from a software RAID0 array that consisted of three USB-attached, external hard disk drives.

Overall, I was very impressed with the noticeable improvement in the responsiveness & performance of my virtual machines. The throughput for file operations was much faster, boot times were extremely quick, and my host Ubuntu box didn't have to share the same disk with the VMs, sparing my host the battle over I/O operations.

Unfortunately, I have this lingering feeling that there might be some disadvantages to running virtual machines over a USB-connected device, but I don't know where to start and find out for myself. For example:

Wouldn't using an IDE drive w/enclosure, connected over a USB port, introduce some kind of latency for disk I/O between that storage and the VMs using it?

How might I be able to test or benchmark different types of disk performance--especially disk I/O latency?

---

### Post by fjgaude on 2009-10-22
Well, the USB bus is limited to about 53 MB/sec... the newer drives are in the 100 MB/sec range... so in a raid0, three-drive array, your thruput would top out at less than 150 MB/sec. Whereas the the drives in SATA bus arrangement could go as high as 300 MB/sec.

As far as latency, I'm not sure there is any.

Bench testing, I use **hdparm** and **dd**:

```
sudo hdparm -tT /dev/mdX
```

```
time dd bs=1M count=1000 if=/dev/zero of=1000M.bin
```

---

