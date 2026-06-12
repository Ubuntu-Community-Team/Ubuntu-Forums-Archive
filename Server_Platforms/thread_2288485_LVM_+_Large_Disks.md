---
title: "LVM + Large Disks"
date: 2015-07-27
forum: Server Platforms
---

### Post by LHammonds on 2015-07-27
I have many terrabytes of storage I need to allocate to Ubuntu Servers (backup repositories) which are virtual machines on VMware.

Is it best to allocated just a few very large disks or many small disks?

I would assume fewest disks as possible to reduce the amount of "drives" the system has to keep track of when allocating and being utilized in an LVM.

Ideas / Thoughts?

Thanks,
LHammonds

---

### Post by oldfred on 2015-07-27
I do not use LVM, but only have Desktop installs.
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)

      
 [URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup
[/URL]
 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

[URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]
[/URL]

---

### Post by LHammonds on 2015-07-27
Thanks but I'm not hear to debate the use of LVM, RAID or backup methodologies.  Simply want to know about making small vs large "disks" (sdb,sdc,etc.) in relation to long-term operation of a server.

If you want to know, I have an IBM V3700 with ~85TB of storage over multiple arrays of disks which are all maintained on the fiber storage.  If a drive dies, it auto-rebuilds a hot-spare and we just pull the bad drive, insert a new one and let it xfer the data off the spare onto the replacement disk...all in about 1 hr.

In the virtual, we simply add a virtual disk of whatever size and assign it to the virtual machine.

This particular server is nothing more than a file repository for our backup system.  We don't even need to backup this particular server or configuration.  Its a standard server setup and takes 10 minutes to spin up an identical system.  I'm using Veeam Backup & Replication to place backups on a local repository and then a "copy" job to duplicate those backups (fulls and differentials with deduplication) to an identical server in an offsite location (same for the reverse).  I also have the servers being replicated to offsite locations.

So this huge backup repository is not actually a "critical" system.  Yes, it would suck if it died but only because I'd have to tinker with it.  The remote servers can easily re-direct to another repository.

---

### Post by CharlesA on 2015-07-27
Probably doesn't matter. I've always just used one very large disk when I have a large array. My main array is 8TB, with my backup array being 6TB.

When you said you wanted to know if there were any downfalls to large vs small disks, were you talking physical disks or LVM partitions?

I don't really use any features of LVM, though, even tho my main server uses it, so I can't really answer your question for sure.

---

### Post by Vegan on 2015-07-27
I have one of those front chassis docks for hard disks, makes backups easy. Hard disks have taken over the role from tape. Now that is how cheap they have become, hard to imagine how much they cost back in say 1978.

---

### Post by LHammonds on 2015-07-28
> **CharlesA said:**
> Probably doesn't matter.That is my guess as well.  Just wanted to see if there were any "gotchas" surrounding this before committing to a design.  Such as any issues of > 2TB disks, slow performance if there are tons of small drives attached and so on.  Most Linux boxes I setup usually just have a single 25GB storage drive.  I rarely have to add more but I design the file system to easily handle expansion by separating all main storage folders into their own partitions using LVM (except /boot).  If curious, how I setup my servers is in my sig.

> **CharlesA said:**
> were you talking physical disks or LVM partitions?
Whether I'm using LVM or not really isn't the main concern. Mainly talking about Linux with its handling of /dev/sd? disks that it sees.  I use LVM so its related and mentioned just in case anyone knows of potential issues.  None of the "drives" that fdisk will see are physical drives.  Physical drives are all in a storage rack system and that storage system handles the RAID and LUN allocations.  VMware simply accesses those LUNs I present and I carve out a random amount of GB to present it to a virtual server as a "disk drive" (aka /dev/sd?).

Thanks for your time and replies.

---

### Post by LHammonds on 2015-07-28
I've decided to do the following:

Create 2TB LUNs and configure as VMSF-5 format in VMware
Create 900GB drives (2 per LUN) and add them to the Linux servers

Even though I can create larger LUNs and VMware can handle > 2TB, I am keeping them smaller for compatibility / portability reasons.

I am creating two drives per LUN so if I needed to move drives around using vMotion, it would be easier to move/fit in other LUNs and have some room left over for VMware snapshots (even though we never intend on using snapshots for the Linux repositories)

**EDIT:** Side note - I install the "scsitools" package so I can run the "rescan-scsi-bus" script to detect newly added drives without needing to reboot...so fdisk can see and allocate the space.

Thanks,
LHammonds

---

### Post by LHammonds on 2015-07-31
Well, that's just great.  Didn't take me very long to run into a problem.

```
resize2fs: New size too large to be expressed in 32 bits
```

I've added several ~1TB drives and now have a 6TB LV Group

Every time I added a new drive, I added it to my LVG and then expanded my backup volume...then resized the file system to increase it an additional 1TB at a time.

My backup volume is now 6TB and my file system is 4TB.  Trying to resize it to 5TB caused it to spit out the above error message. (using resize2fs 1.42.9 on Ubuntu Server 14.04.2 LTS)

Related topics:
 - [EXT4 and the 16TB limit solved]("http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/")
 - [EXT4 resize2fs .. error "New size too large to be expressed in 32 bits"]("http://ubuntuforums.org/showthread.php?t=2275529")
 - [Cannot grow ext4 past 16tb without 64bit]("http://www.reddit.com/r/DataHoarder/comments/1uxg3r/til_cant_grow_ext4_past_16tb_without_o_64bit/")
 - [Resize ext4 filesystem on LVM2]("http://ubuntuforums.org/showthread.php?t=1791544")

I used "tune2fs -l /dev/LVG/bak" and noticed the 64-bit flag was not set since the initial creation of the file system was less than 4TB (which defaults to 32-bit).

So, if anyone posts a similar question as my original post, Linux does not have a good method for supporting large volumes.  If you know about the limitations beforehand, you can set the 64-bit feature when formatting the file system but you still have to create the file system one time at the largest possible size you will need because the tools don't exist that allow for resizing large volumes.  Other file systems than ext4 are typically noted as being experimental and not for production or have show-stopping bugs that can cause corruption in large multi-terrabyte volumes.

It pains me to do this but I'm thinking about using Windows 2012 as the OS that will house my storage backups.  I was excited that I could finally use a Linux server as part of a large and important system but I have failed to make it happen successfully.  I have a Win2008 PACS imaging server that has had its data drive expanded many times and is pushing about 6TB by itself and I have 60 other servers to backup too. I cannot afford something like this putting me in a bind where backup jobs stop working.

Sure, I could add multiple Linux servers with set maximum space that is additional CPU/RAM for each server and my VM hosts are already spread thin.

Thanks,
LHammonds

---

### Post by CharlesA on 2015-08-01
I've heard of people using ZFS or BTRFS, but I don't think ZFS has native Linux support.

I totally agree with you on the reluctance of using a system that might work/might not work. If you have an alternative that has already been tested in production, use it. :)

---

### Post by LHammonds on 2015-08-10
Yes, Windows will work just fine regarding the file system and the flexibility to expand over and over in a stable and fairly easy manner.

I am back from vacation so I will start to dismantle the Linux repository servers and setup Windows servers to replace them.

Sure wish more development was more focused on a stable file system in the terabyte / petabyte range...but if they are using the 80/20 rule for focusing their time, us guys with huge storage must be in the <1% and those in that category are NOT using Linux and thus its a chicken vs egg syndrome.  However, the support has to be there BEFORE anyone in their right mind will actually "use" it in production.

LHammonds

---

