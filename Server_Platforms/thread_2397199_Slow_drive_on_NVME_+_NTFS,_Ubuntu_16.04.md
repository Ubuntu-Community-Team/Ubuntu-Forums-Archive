---
title: "Slow drive on NVME + NTFS, Ubuntu 16.04"
date: 2018-07-26
forum: Server Platforms
---

### Post by twoj on 2018-07-26
Hello 
I'm using an intel NVMe P4600, and I have it formatted as NTFS;  I brought the drive over from a windows system.

Copy speeds on this NVME are only about 95-120MB/s on large ~5GB size files.  Also copies between this drive and other drives NVMe Drives I have installed in this system are about the same speed.

One of my other NVMe drives formatted to ext4, is running much closer to full NVMe expected speed, all on the same system.

Is it because I'm using the NTFS?  Can anything be done to improve performance so I can get my data off the drive faster?

Thanks

---

### Post by TheFu on 2018-07-27
Don't use NTFS.

---

### Post by twoj on 2018-07-27
YES.   Agreed.

So, no 'special trick'?  No way to re-mount it so improve performance for that one copy out?

---

### Post by TheFu on 2018-07-27
The NTFS file system access uses FUSE, not kernel drivers.  FUSE is slow.  No way around that except to use a file system that has native, kernel, support.

You can use **bonnie++** to check performance of different disk access methods.  You can use **hdparm** to tune the disk access for the system, but nothing will significantly help the FUSE NTFS drivers be faster.

The only "trick" I have is to connect NTFS disks to Windows computers with GigE network connections, then transfer it over the network using an efficient transfer method.  BTW, forget about wifi it is nowhere near what GIgE provides, even the newest specs.

That's all I got.  I have 1 NTFS disk here that gets physically connected to a Linux machine.  It is connected to a video recording device that supports only NTFS or FAT32 file systems, so I don't have any choice.  I move the data off that HDD ASAP, before doing any processing by using a USB2 dock.  It is slow to transfer, so I usually let it run for a few hours while doing other things. The dock has an eSATA connection, but it doesn't work with any of my eSATA ports on multiple systems. The dock is about 10 yrs old, maybe older.

---

### Post by twoj on 2018-07-28
Thank you TheFu for the detailed explanation!

What you describe is the my current setup,  which I can not run fast enough away from.

I may try swapping out the NVME into Windows box, but using 1GB network still only get 110-120MB/s 

Lesson learned!

Thank you!

---

### Post by TheFu on 2018-07-28
Don't confuse MBps and Mbps.  Bandwidth is always in Mbps, except when software weenies are involved.  NOBODY else uses MBps.  Nobody.

110MB/s is 880 Mbps.  You are getting nearly a full 1Gbps.  Add in protocol overhead and that's actually pretty impressive if this was over a network.

For internal transfers, you'd need to look at the bus limitations of each component, including the motherboard.  I have an older Core i5 machine that can't handle USB3 speeds. It has a reputable USB3 PCI controller, but the motherboard bus architecture simply doesn't support that throughput on that bus.  At the time it was built, GPU performance was deemed more critical, so most of the motherboard bus throughput is allocated to GPU use. I looked into buying a new motherboard when I realized the issue.  Typical from Intel, the CPU socket only has CPU support for about 18 months.  Then they change the socket and only newer, expensive, CPUs will work. I'd need to build a new box to get the throughput I wanted.  The bus already has 8+ HDDs connected, plus 2 external via USB3.   One of the USB3 external disks is used for all the system backups on my network. I use efficient backup software, so most backups are 2-3 minutes a day. It works well enough.

AMD does it differently. They support almost their entire line of CPUs on a CPU socket for a long time.  AM4 is what current generation Ryzen CPUs support.  Older and newer CPUs gain motherboard support through BIOS updates.

---

