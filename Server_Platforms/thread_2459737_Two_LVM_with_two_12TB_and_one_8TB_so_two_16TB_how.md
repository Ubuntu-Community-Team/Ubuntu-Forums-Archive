---
title: "Two LVM with two 12TB and one 8TB so two 16TB how?"
date: 2021-03-24
forum: Server Platforms
---

### Post by Raymond Day on 2021-03-24
Hi.

I got two 12TB hard drives so one is a backup.

Want to add storage so will have to make the 12TB new to make it a LVM drive. But I only want to add 4TB to the 8TB drive and then the other 12TB make it a LVM and add it to the 2nd half of the 4TB drive.

Do I have to partition the 8TB in half then make the LVM or how do I do that with out getting two 4TB drives?

Thank you.

-Raymond Day

---

### Post by volkswagner on 2021-03-24
Some folks don't like adding multiple physical disks to a Volume Group.
I've never done it.

It certainly is possible to create two partitions on the 8TB drive, then
add each partition to the Volume Group of your choosing.

I think adding a physical volume to an existing storage group
is "sort of like" RAID0. The risks are similar. You could have
massive data loss if either volume fails because the data
spans multiple physical disks. Since there will be two
disks are your risks twice as high????

Perhaps you can plan to segregate the data within
your directory structure so you can simply create
additional mount points with the added disk.

One bad idea is having a backup partition shared
with your data partition on the same drive. If the
8tb disk fails, you have no backup and no original
files, so really it's not a backup (is it)?

---

### Post by Raymond Day on 2021-03-24
Yes you are right. I got another 4GB so I will use that and then I will just use the 8GB for only 4GB then. Thank you.

Yes that would not be a backup then your right I did not think about that.

-Raymond Day

---

### Post by TheFu on 2021-03-25
> **volkswagner said:**
> Some folks don't like adding multiple physical disks to a Volume Group.
I've never done it.

Put me in that group. I learned the hard way how bad of an idea it was. My story:
Started with one 80GB HDD.  LVM is cool, so I used that from the start. 
Then I added another 80G HDD to the VG and extended the LV from the first disk in size to use the next 80G. This concatenated into 160G.
Then I added a new 160G HDD to the VG and extended the LV onto the 3rd HDD.  Total 320G. It was convenient to have 1 mount, but all that storage inside a single file system. HDD prices were falling.

Then one of the drives died. Dead.  I didn't have backup religion, so that data was gone, but I still had the other 2 disks, right?  Well - no.  At the time, I wasn't skilled enough to attempt any data recovery and the tools for that were terrible.  It was mostly usenet stuff anyway, so the data wasn't important.  After screwing around for about 2 months, I put those 2 other disks onto a shelf in the closet with plans to attempt recovery later and bought 4x320G drives, and external array, and setup a RAID5 subsystem.  

I still didn't setup backups for that data.  Why?  Because I'm stupid.

Inside that machine was the OS drive and I did have another HDD inside it that I'd scripted a weekly mount-rsync-umount ; you know - a backup. It was manually run, from time to time. I intended to run it weekly, but often it would be monthly or every 6 months. I was busy.

Then that box got hacked through a flaw in DNS. I was a few months behind on patching the box, but had happened to run the rsync a week earlier - purely by chance. It was a different time on the internet.  Someone got in - probably through an automated process, created some directories under /tmp/.../.system32/.{some random characters}/ where they downloaded other stuff and tried to gain root access. All those files were running with the named userid, which really had no access on the box, except to write to /tmp/ area.  A few hours later, I wokeup for the day and my email was flooded with thousands of warnings about someone trying to gain root access on the machine. Each attempt caused an email.  I had patched the specific library they were trying to use for that purpose - hah!

So, I powered off my cable modem, killed all the named processes, mounted the "backup" and did a diff for all the files between the week-old mirror and the current OS.  I hadn't used the machine much, so hardly any files had changed which I recognized and remembered ... except some files in /tmp/.../.system32/ ... which were all new.  So I was convinced nothing bad had yet happened to the machine.  I wasn't really using bind and it shouldn't have been available over the internet since I only intended it to be used on the LAN.  My mistake.  Again, I was stupid and had enabled 53/udp on the router to pass through to the server. That got taken advantage.

On the external array was just data, no programs, so I wasn't worried about nasty stuff there. A quick 'find' for files without media extensions and smaller than media files should be quickly confirmed it was fine. I did a deeper search using the "file" command and only a few of my scripts and m3u playlist files were found. They hadn't touched that storage at all.

After all this research, killing named processes, checking for hidden files, removing the 53/udp port rule on the router, I reconnected the internal network to the Internet. I'd dodged a bullet.  I didn't mention rebooting, because I didn't. At the time, I was trying to keep long uptimes (because I'm stupid). It was almost a point of pride.  At one point that machine had been up over a year. It was located in a closet off the laundry room with just the box, power cord and a long ethernet cable. Nothing else. It sat in that room for years.

So - being hacked pointed out many flaws in my backup methods. What if they'd been there for months? What if their attack hadn't caused all those emails?  What if they had deleted all the data "just because" they could?  This was the 2nd time I'd been hacked, but it had been over 5 yrs since the first time.  It changed everything about my security stance.

I'd always buy backup storage to go with primary storage.
I'd never make any primary storage file systems larger than could be backed up to a single HDD.
I'd automate backups, since even just running a script weekly was beyond my ability.
I'd have those backups on a different system, so if a bad group deleted the entire server, the data wouldn't be lost.
I'd learn about versioned backups, since files can be corrupted over time.
I'd find a way to ensure very important files were not corrupted and try to automate that as much as possible.

Over the years, I've looked at lots and lots of backups between home, my little consulting company and enterprise clients. I've seen enterprise clients with about 100,000 servers have 10% backup failures nightly due to different issues. One of these places appeared to have nearly unlimited money for backups and storage, so I knew it wasn't because they weren't using the most reliable and best tools. It came down to technique.  I'd scroll through the list of server backups on one of my current projects there and the overview would show that every night a few of the hundreds of servers had backup faults of some sort, but it appeared to be mostly random.

In these forums, I've posted lots of times about backups. I feel like a broken record. ... again today.  Storage design is all about the backups. Don't break that first rule.  If you can't backup the data to a different disk, then you shouldn't have the data.  Data is much more important than hardware. Computers can be replaced for a few hundred $$$, but data cannot.  Begin with the backup solution in mind, then deal with the storage, then with the LVM layouts, and finally with the way things will be mounted.

Hopefully, this story will help others figure out that backups are important.  
Backups need to be:
[LIST]
[*]Automatic
[*]Versioned
[*]Fast, long backups never get performed
[*]On different physical disks, preferably not connected to the same system as the primary, but that isn't always possible.
[*]Encryption would be good, since if a backup HDD fails and needs to be returned for warranty, but cannot be wiped due to physical failures, the encryption for the storage is the only safety.
[*]Storage efficient; we can't expect to have 5 backup drives to have 5 versions of backups. Thankfully, differential backups really work and are very storage efficient. They are also fast.
[/LIST]

I'm still stupid sometimes, just in different ways than 20 yrs ago. ;)

---

### Post by darkod on 2021-03-25
My personal opinion.

LVM for me is just what it says: Logical Volume Management.
The benefit is to have an easy way to extend/shrink volumes (mostly extend).

It is not RAID nor backup, so I don't try to make it be.

If you can afford the budget and have enough HDD space in the box, you could try RAID + LVM (I know, some people use LVM as RAID but I'm still old fashioned, one bit at a time). The RAID gives you redundancy for HDD failure and using the arrays as physical device for LVM gives you flexibility for volume management.

Backups are separate thing and you should have a backup of all important data without saying.

Actually in my server box I have as first layer mdadm RAID, then those arrays are used as physical devices for LVM and then the LVM volumes are used as physical devices for LUKS encryption. So you could say I have RAID + LVM + LUKS in that order. :)

---

### Post by TheFu on 2021-03-25
LVM stole the mdadm code a while ago.  [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/6.2_release_notes/storage](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/6.2_release_notes/storage) - so in the RHEL 6.2 timeframe.  It has both RAID1 and RAID10 capabilities provided by LVM commands.  *man lvmraid* has more details.  Switching into and from RAID1 is possible.  Switching into and from RAID10 is not possible, due to the physical requirements for RAID10 - doing so would end up with RAID01, which isn't good.

While I haven't tested this, I've read articles that LVM RAID1 is nearly the same performance (~ 3%) as mdadm RAID1.  Setting up LVM with the OS disks has been relatively easy on Ubuntu for some time. If RAID1 is desired, then moving from non-RAID to RAID1 for that storage would be relatively easy with little risks.  Hummmm. I've been meaning to swap an NVMe drive into a system currently running on a SATA SSD. It uses LVM. I'd bet that 3% difference would be unimportant going from SATA --> NVMe.  Of course, there is always the **pvmove** command too. I've used that before with in-use LVM PVs/VGs/LVs. It worked perfectly, but it did take some time.  This time around, I'm leaning towards the **lvconvert** method to create a RAID1 mirror (adding the new SSD) and let that run for some time as the data gets synchronized, then another lvconvert to remove the older SATA SSD from the RAID1 set.  This 970 EVO won't install itself. ;)

LVM allows "snapshots" to be created, which is how to get a quiesed backup.  Snapshots are handy for other reasons too.  **Snapshots DO NOT replace backups.**  If the data isn't copied to other physical storage, it isn't a backup. 

Snapshots can be really handy if a risky update is planned. Create a snapshot, do the update. If it doesn't workout well, just revert back to the snapshot and drop all new blocks. Snapshots are nearly instant because they just mark used blocks as frozen, cannot be changed.  Changes all do into new blocks.  It is like having a backup that is handy for a few hours, provided the disk doesn't fail. That's very useful.  But keeping snapshots around forever will lead to running out of new blocks for updates and new files.

---

### Post by LHammonds on 2021-03-26
There is a lot of good info here for you to chew on.

Regarding backups, there are a lot of different ways/designs of doing it but keep the overall view in your head simple.

I think in terms of the 3-2-1 rule where you have at least 3 different backups on 2 different media with 1 of them offsite.

The easy scenario is:
 - Your internal disk drive fails. Local files and local backup is lost.
 + Recovery can happen if backup is on a 2nd disk (with separate partition) or external drive or remote external computer.

Another scenario is:
 - Your PSU gets fried and also fries all devices it is providing power to.  Internal and external USB-connected drives are dead.
 + Recovery can happen if backup is on a non-connected external drive or remote external computer

Another scenario is:
 - Your location is hit with a fire or flood or tornado and destroyed the PC and nearby equipment.
 + Recovery can only happen if backup is at a remote location (and you are hopefully alive and well).

With the various scenarios of failure in mind and how fast you need to recovery from a failure, this is why you hear about physical servers being setup with 2 fairly small physical drives mirrored for just the operating system (OS) so it can boot and access the system/tools even if an OS drive fails and other, larger drives being placed in a RAID 5 or 10 for data that can stay online even if a drive fails.

How a server is designed if being installed on bare-metal is typically VERY different from how it is designed when being installed inside a virtual machine (VM).  The tutorials on my site are all based on installing inside and managing from a virtual environment so when you see things like "add a virtual disk to the LVM" it is not necessarily a bad thing for that scenario if the underlying physical hardware is robust...but doing the same for a physical hard drive on a bare-metal install would be a risky situation as already mentioned by others.

LHammonds

---

