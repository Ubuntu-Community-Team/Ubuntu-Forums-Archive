---
title: "Maximum partition size in Ubuntu server 12.04"
date: 2012-08-16
forum: Server Platforms
---

### Post by rossj81 on 2012-08-16
Hi. Complete Ubuntu and Linux n00b here. I am in the process of building a file server for my media collection. I have bought a HP ProLiant Microserver, and want to configure it as follows: 1 x 250 GB HDD for OS + 4 x ? TB HDDs for content, using SnapRAID to build in redundancy for the content. I am more familiar with Windows, but its sys req's are a joke compared to Ubuntu. I have downloaded Ubuntu server and messed around with it in a VM, and would like to use that as the OS and ext4 as the FS.

So here's the question: should I buy 4 x 2 TB drives, or 4 x 3 TB drives? Obviously 3 TB is preferable, but I have read some old (2007/2008) literature that says the maximum supported partition is 2 TB. Yes, I could split the 3 TB disks into two partitions of 1.5 TB each, but I am concerned that SnapRAID will use a partition to create parity for another partition on the same physical disk. I would prefer to have a single partition per physical disk.

Obviously Ubuntu has developed a lot since 2007/2008, so I would assume the maximum supported partition size has increased, but I can't find anything to prove this.

I'd really appreciate it if someone could confirm that I can create a 3 TB partition before I go out and buy the disks. Even better, if someone has it running in production with SnapRAID!

---

### Post by smartboyhw on 2012-08-16
> **rossj81 said:**
> Hi. Complete Ubuntu and Linux n00b here. I am in the process of building a file server for my media collection. I have bought a HP ProLiant Microserver, and want to configure it as follows: 1 x 250 GB HDD for OS + 4 x ? TB HDDs for content, using SnapRAID to build in redundancy for the content. I am more familiar with Windows, but its sys req's are a joke compared to Ubuntu. I have downloaded Ubuntu server and messed around with it in a VM, and would like to use that as the OS and ext4 as the FS.
 
So here's the question: should I buy 4 x 2 TB drives, or 4 x 3 TB drives? Obviously 3 TB is preferable, but I have read some old (2007/2008) literature that says the maximum supported partition is 2 TB. Yes, I could split the 3 TB disks into two partitions of 1.5 TB each, but I am concerned that SnapRAID will use a partition to create parity for another partition on the same physical disk. I would prefer to have a single partition per physical disk.
 
Obviously Ubuntu has developed a lot since 2007/2008, so I would assume the maximum supported partition size has increased, but I can't find anything to prove this.
 
I'd really appreciate it if someone could confirm that I can create a 3 TB partition before I go out and buy the disks. Even better, if someone has it running in production with SnapRAID!
 Well, I think now it can support 3TB. Even Windows 8 can now support 1024TB. Shouldn't be difficult.

---

### Post by rossj81 on 2012-08-16
I agree, it *should*, but I'd like either documented proof or actual experience before I spend $560 on new disks... ;-)

---

### Post by mrlixam on 2012-08-16
Hey,
maybe this helps:

[http://askubuntu.com/questions/172930/resize-a-2tb-partition-on-a-3tb-disk-created-with-fdisk](http://askubuntu.com/questions/172930/resize-a-2tb-partition-on-a-3tb-disk-created-with-fdisk)

Cheers,

---

### Post by rossj81 on 2012-08-17
That's just what I was looking for, thank you.

---

### Post by ian dobson on 2012-08-17
Hi,

Linux supports gpt partitions that can be larger than 2Tb. 
The old partition table (msdos) only supports max 2Tb.
Linux can create a file system on a raw drive (no partition needed)

The only problem is that the BIOS also needs to support >2Tb drives. 

So you could use 3Tb drives if your BIOS supports them, but I would recommand buying 2Tb drives just get enough :)

Regards
Ian Dobson

---

### Post by CharlesA on 2012-08-17
Just use GPT partition tables and you will be fine.

I've got a 4TB partition on my 12.04 server and I've seen RAID arrays much larger than that.

---

### Post by rossj81 on 2012-08-19
> **ian dobson said:**
> Hi,
So you could use 3Tb drives if your BIOS supports them, but I would recommand buying 2Tb drives just get enough :)

Ooops, too late. Ordered the first of the 3 TBs on Friday ;)

---

### Post by rossj81 on 2012-08-19
> **CharlesA said:**
> Just use GPT partition tables and you will be fine.

I've got a 4TB partition on my 12.04 server and I've seen RAID arrays much larger than that.
Awesome, thanks. I let you know how it goes.

---

### Post by CharlesA on 2012-08-19
> **rossj81 said:**
> Ooops, too late. Ordered the first of the 3 TBs on Friday ;)
For what it's worth, I've been using 3TB USB3 drives to backup my data since I had my old server with a USB3 card. No problems at all. ;)

However, I haven't quite moved to using 3TB drives in my RAID, but I don't think there should be any problems.

---

