---
title: "Want to Remove Software RAID"
date: 2010-12-16
forum: Server Platforms
---

### Post by putz3000 on 2010-12-16
I am trying to build a storage server using software RAID.  After getting writing RAID information to what I thought was the drives, I realized the configuration was not going to work.  Since that time I have modified the RAID configuration more than once plus this is a project that was started a few months back.  Between the time delays and currently written configuration, things are a confusing mess.

What I would like to do is wipe out all software RAID and start all over again.  The problem is that I am unable to figure out how to get rid of it.  I used DBAN to wipe out all four of my 1 TB drives which took a while.  But still, the RAID configuration pulls up when I try to do a new install.  

Where is the RAID configuration data stored at if not on the HD?  How can I scrub that information off so I can start all over again?

Thanks,

---

### Post by arrrghhh on 2010-12-16
[Software RAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) Ubuntu Community Doc.  Hopefully that helps ;)

---

### Post by SaturnusDJ on 2010-12-16
Zeroing the superblock should work.

---

### Post by putz3000 on 2010-12-16
> **arrrghhh said:**
> [Software RAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) Ubuntu Community Doc.  Hopefully that helps ;)

Doesn't look like it.  that document is for setting up RAID.  What I want to do is remove the RAID configuration, then start again - which is when that document will be handy.

---

### Post by putz3000 on 2010-12-16
> **SaturnusDJ said:**
> Zeroing the superblock should work.

I will look into this.  thank you

---

### Post by oldfred on 2010-12-16
Not sure where it writes this, this should work.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by rubylaser on 2010-12-16
First, stop the array.
```
mdadm --stop /dev/md0
```
Here's how to zero the superblocks.
```
mdadm --zero-superblock /dev/sdb1
```
Just do that for each drive in the array.

Finally, remove your /etc/mdadm/mdadm.conf file.  Now, you should be able to start from scratch assembling a new RAID array, and then adding a filesystem.  Hope that helps.

---

### Post by putz3000 on 2010-12-16
Not sure if this changes anything, but I am wanting to do this on a system that does not actually have the OS installed yet.  I have never made it that far.  

So are the command line instructions able to be done from a live cd?

---

### Post by bigsigh on 2010-12-17
Yes, I was zeroing superblocks just tonight with a live Mint dvd.
Enter mdadm, if your distro doesn't have it you'll just need to apt-get.

---

