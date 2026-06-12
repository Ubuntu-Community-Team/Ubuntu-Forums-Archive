---
title: "RAID mess"
date: 2010-01-08
forum: Server Platforms
---

### Post by chewy75 on 2010-01-08
Hi

I setup my server a few months back and thought all was going well until I checked my disk usage, to the extent I'm not convinced how I thought my system was setup is actually correct.

Basically my system is an Intel Atom low wattage box that consists of three physical drives.  The first drive (sda) is a 500gb and the other two are 1TB (sdb and sdc).  The first contains the /boot /swap and root as separate partitions.  The other two are plugged into a basic hardware RAID (this I'm certain of because I checked before the system booted).  Somehow sdb and sdc are mapped to /raid but the issue is that I'm not sure how I've achieved this.  I know fstab contains a mapping from /dev/md0 to /raid but I cannot see /dev/md0 as a device.  I've checked mdadm.conf and cannot find any mention of it.  Am I missing something blindingly obvious?  How do I confirm /raid is definitely on sdb and sdc?

Presuming I've failed to understand something obvious how do I find the disk usage or sdb and sdc?

The two drives should be setup as RAID1 by the way.

Thanks in advance!

---

### Post by HighCommander540 on 2010-01-08
> **chewy75 said:**
> Hi

I setup my server a few months back and thought all was going well until I checked my disk usage, to the extent I'm not convinced how I thought my system was setup is actually correct.

Basically my system is an Intel Atom low wattage box that consists of three physical drives.  The first drive (sda) is a 500gb and the other two are 1TB (sdb and sdc).  The first contains the /boot /swap and root as separate partitions.  The other two are plugged into a basic hardware RAID (this I'm certain of because I checked before the system booted).  Somehow sdb and sdc are mapped to /raid but the issue is that I'm not sure how I've achieved this.  I know fstab contains a mapping from /dev/md0 to /raid but I cannot see /dev/md0 as a device.  I've checked mdadm.conf and cannot find any mention of it.  Am I missing something blindingly obvious?  How do I confirm /raid is definitely on sdb and sdc?

Presuming I've failed to understand something obvious how do I find the disk usage or sdb and sdc?

The two drives should be setup as RAID1 by the way.

Thanks in advance!

If its a hardware RAID...I am pretty sure the RAID controller does all that stuff on its own without telling the OS. If it was a software RAID that would be a different story. YOu would have to know how to access the information that your hardware RAID controller is creating and monitoring.

---

### Post by chewy75 on 2010-01-08
OK can I phrase it another way, how can I check which physical disk /raid is sitting on?  The fstab led me to believe /dev/md0 was being mapped to /raid but if I cannot find /dev/md0 how can I be sure.

---

### Post by fjgaude on 2010-01-08
Here's a useful command or two:

```
sudo mdadm -E /dev/sd[nn]
```

That will show what array it is in.

```
sudo mdadm -D /dev/md0
```

This shows the array and the partitions associated with it.

Hope this helps.

---

### Post by chewy75 on 2010-01-08
Thanks that was a huge help.  In short my /raid folder wasn't on the sdb and sdc disks.

---

### Post by Vegan on 2010-01-08
I suggest not using a software RAID, I have seen far too many failures of such setups.

---

### Post by bikeman1 on 2010-01-08
Vegan is right.  Get a hardware card like the 3ware 9550 (8 drives) and set up a Raid 5 array.  Its a few hundred bucks but pretty  bombproof.  

[http://www.provantage.com/3ware-9550sxu-8lp-sgl~73WAR04F.htm](http://www.provantage.com/3ware-9550sxu-8lp-sgl~73WAR04F.htm)

---

### Post by HighCommander540 on 2010-01-08
> **bikeman1 said:**
> Vegan is right.  Get a hardware card like the 3ware 9550 (8 drives) and set up a Raid 5 array.  Its a few hundred bucks but pretty  bombproof.  

[http://www.provantage.com/3ware-9550sxu-8lp-sgl~73WAR04F.htm](http://www.provantage.com/3ware-9550sxu-8lp-sgl~73WAR04F.htm)

Also, you really need at least 1 hotswap (otherwise having a RAID is pretty much pointless), 2 if you can afford it.

---

### Post by chrisinspace on 2010-01-08
It wouldn't be true RAID, but for a cheaper alternative, can't you mirror disks with LVM?

---

### Post by Fcon_Vpro on 2010-01-10
I disagree with the claims about software raid not being safe.
I use MDADM on a few servers and all issues Ive run into have been my own fault.
My own personal home server with raid5 has been moved between 3 operating systems and still runs 100% (9.04(32bit)->9.10(32bit)->8.04.3(64bit)).
With the cpu power of today, hardware controllers dont make that much of a difference unless you have some really high end servers.

I will agree that raid1 is a waste of time and its better to go raid5

---

### Post by The Real Dave on 2010-01-10
> **Fcon_Vpro said:**
> I disagree with the claims about software raid not being safe.
I use MDADM on a few servers and all issues Ive run into have been my own fault.
My own personal home server with raid5 has been moved between 3 operating systems and still runs 100% (9.04(32bit)->9.10(32bit)->8.04.3(64bit)).
With the cpu power of today, hardware controllers dont make that much of a difference unless you have some really high end servers.

I will agree that raid1 is a waste of time and its better to go raid5

Ya, I'll +1 that, I've never had a problem with software RAID that I didn't cause. Sure, hardware RAID can be bulletproof, but its expensive. For a small home or media server, you don't need to spend more on the RAID card than the drives.

And as to having hot swap bays, they're really not essential. It depends on the server, and how comfortable you are opening it up. Harddrives don't fail that often in average use.

---

### Post by chrisinspace on 2010-01-11
> **Fcon_Vpro said:**
> I will agree that raid1 is a waste of time and its better to go raid5

RAID 5 is definitely better if you have enough drives. You get the benefits of redundancy and striping for additional performance.  The problem is you have to have at least 3 drives.  I'm building a server right now that is only 1U with 2 HDD bays.  RAID 1 and 0 are my only options.

---

### Post by barnex on 2010-01-11
> **Fcon_Vpro said:**
> I disagree with the claims about software raid not being safe.
I use MDADM on a few servers and all issues Ive run into have been my own fault.
My own personal home server with raid5 has been moved between 3 operating systems and still runs 100% (9.04(32bit)->9.10(32bit)->8.04.3(64bit)).
With the cpu power of today, hardware controllers dont make that much of a difference unless you have some really high end servers.

I will agree that raid1 is a waste of time and its better to go raid5

I agree. This is just my personal experience, but for me software RAID5 with mdadm is running flawlessly on my production server. Also, it never uses more than 1% of the cpu power.

---

