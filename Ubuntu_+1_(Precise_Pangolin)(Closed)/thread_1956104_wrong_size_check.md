---
title: "wrong size check"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Skaperen on 2012-04-10
I have a disk partitioned with plenty of space in /usr, where most of the files go to.  I've done this install before with the same DVD and the same partition layout, and it works fine (I knew it would and skipped the message).

But, wouldn't it be better for the calculation to at least get this right?  It should have numbers for the size needed for various subtrees and do the calculation based on what will be mounted.

[IMG]http://phil.ipal.org/ubuntuforums.org/2012-04-10/xubuntu-12.04-beta2-install-disk-size-error-00-0864x0576.jpg[/IMG]

---

### Post by fjgaude on 2012-04-10
Not sure if I can be of any help, but what's the sda120/121 partitions? And the sda6 swap at 51GBs?

I wonder if the installer was ever tested at such values?

---

### Post by Skaperen on 2012-04-11
> **fjgaude said:**
> Not sure if I can be of any help, but what's the sda120/121 partitions? And the sda6 swap at 51GBs?

I wonder if the installer was ever tested at such values?

sda120 is just a partition gap with a partition name given to it
sda121 is a backup for the MBR I do manually, right before the GPT backup

The issue is unrelated to them as it happens before I used those.

sda6 is swap space.  This is a rather big machine that could see a burst of processes in some cases.

Maybe it should be tested?  There are machines around with 40 cores and 1TB RAM and 150TB of RAID.  SANS could make a machines way larger than that.  You wouldn't want such machines to be stuck with Windows, would you?  Mine is not THAT large ... more like 10 core, 64GB RAM, 8TB disk (not yet in place, testing with 1TB).

---

