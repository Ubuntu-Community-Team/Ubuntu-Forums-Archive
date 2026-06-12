---
title: "Opinions about Partitioning Options"
date: 2020-11-17
forum: Ubuntu, Linux and OS Chat
---

### Post by helen314 on 2020-11-17
Just asking for an opinion.
If one uses "gpt"  which no longer limits partitioning by not using "logical"  nor "extended " partitions - how does LVM "improve" anything?
(Having few issues with implementing RAID, I won't even try to add LVM into the equation )

---

### Post by Tadaen_Sylvermane on 2020-11-19
I put lvm on any installation I do because it makes it easy to adjust size of partition as needed (increase while live). create new ones on the fly, snapshots... lots of reasons. I don't use many of the features because my systems generally only have a single disk for the os. I think there is a way you can move an entire volume from one drive to another while the system is running. i believe this includes root. Good way to upgrade to an ssd from a spinner.

---

### Post by wmcl on 2020-11-29
LVM all the way, with quite a number of volumes for more flexibility (space allocation as needed, mount flags, different filesystem configuration to optimize for the type of usage):


[LIST]
[*]/ (of course)
[*]swap
[*]/home
[*]/usr (potentially another volume for /usr/local, if needed)
[*]/opt (if needed)
[*]/var (sometimes another one for /var/log and /var/cache, depending on the system's main use, also, on systems where a lot of storage inside the /var hierarchy is s used by individual programs, I'll allocate a seperate volume for those, for example /var/lib/mysql or /var/www)
[*]/srv (on systems using this hierarchy)
[*]/tmp (mounted noexec, nodev and nosuid for security reasons, on systems with enough RAM, I prefer to put it in the ramdisk, though, so no LVM volume)
[/LIST]

I mostly use LVM for more flexible storage space allocation and rarely make use of the more advanced features.

---

### Post by poorguy on 2020-11-30
In my early days of using Linux and learning Linux I used to partition my hard drive although other than learning never found any use for it so these days I place the DVD in the tray and let the installer do what it does better than I and never had any problems.

I've become lazy in my old age. :D

---

### Post by Shibblet on 2020-12-02
With Kubuntu, I only make a /(root) partition, and a /home partition.  The /(root) is 32gb, and the /home is the remaining part of the SSD... -10% for SSD usage (Samsung's Suggestion.)

---

### Post by TheFu on 2020-12-02
I use LVM for all the added flexibility that GPT doesn't address at all.  On a system with LVM install, check out the commands available. To see those, 
```
pv{tab}{tab}
vg{tab}{tab}
lv{tab}{tab}
```

LVM provides striping, cloning, moving, resizing, conversions from 1 type to another.  Say you want to have a 100% clone of a system, but don't want to power it off.  Add a mirror to the LVs you want cloned, then break that mirror and pull the drives.  

I've used pvmove to migrate a running system from a 250G to a 500G SSD.

LVM snapshots are part of my daily backup processes. I can't imaging doing those without that capability. DBMS doesn't need to to touched during backups. It keeps running, just like any n-tiered server does, while the backups are happening. No worries about getting open, corrupted, files thanks to LVM snapshots.

GPT doesn't address any of those.  What GPT does is remove extended partitions, increase the size of supported HDDs, and provide a backup partition table at the opposite end of the storage medium. All great things, but not really related to what LVM does.  

If you want to compare LVM with other tools, look as ZFS.  Then there are things to consider, since both solutions have competing capabilities.  LVM just has much more proven time on Linux systems than ZFS.  Some day, I fully expect ZFS to be the primary solution for LVM and file system needs on Linux, but I don't feel we are there, yet.  ZFS for data areas, if you are just starting out, would be smart. But ZFS for the boot areas - not quite ready.

IMHO.

---

### Post by VMC on 2020-12-02
> **poorguy said:**
> In my early days of using Linux and learning Linux I used to partition my hard drive although other than learning never found any use for it so these days I place the DVD in the tray and let the installer do what it does better than I and never had any problems.

I've become lazy in my old age. :D
I'm with you. Too old to change now(me thinks). I've used EXT3, and then EXT4 and never changed. One partitions to rule them all "/". Use fsarchiver from time to time. Important Home stuff I save elsewhere.

I've heard great things about LVM. In fact, I think Fedora now sets LVM as default install. I wonder though, with all the power, is there side effects; more processes, less speed, etc.

edit: I found this bench mark between the two, ext4 & lvm with ext4
[https://www.phoronix.com/scan.php?page=article&item=fedora_15_lvm&num=1](https://www.phoronix.com/scan.php?page=article&item=fedora_15_lvm&num=1)
Interesting

---

### Post by TheFu on 2020-12-02
Formatting ext4 on a partition vs formatting ext4 on an LV - night and day.  The LV is MUCH faster well over 5x faster.  
Nice link, but ext4 has changed drastically since 2011.  

I thought Redhat people were into XFS?  For enterprise setups in big corporations and universities, I've always seen LVM+XFS.

I know that ext4 + LVM integrate better. LVM can resize EXT4 file systems as part of the lvextend process by adding a -r option.  Saving 50% of the required commands is a wind, always.

---

### Post by rbmorse on 2020-12-03
What about LVM + F2FS?  Is that a valid combination?

---

### Post by VMC on 2020-12-03
Reading the comments on my supplied link, some think for home user, LVM installed is overkill. Servers and the like understood. I rarely re-adjust my partitions size.
I was planing to install Fedora Mate. If I do then I will surely install LVM as a test.

---

### Post by TheFu on 2020-12-03
> **rbmorse said:**
> What about LVM + F2FS?  Is that a valid combination?

I don't think it can be used for booting today, but it will definitely work for data. I've not tried it for /home/ or /usr/.

Pretty much any file system can be used with LVM, through you probably wouldn't use btrfs or zfs with it.  I must admit to using ZFS inside an LVM LV because the setup scripts for LXD basically demand it. I'm sure there's a way to use LVM directly with LXD, but at the time, it was beyond my LXD skill and it hasn't been important to fix yet.

Remember, everything is a file (unless it is a process), so if you can make a file of the needed size (fallocate or dd or cp or 50 other ways), then you can treat that like a storage block device, if you like.

---

### Post by DuckHook on 2020-12-03
> **VMC said:**
> …some think for home user, LVM installed is overkill…
It does involve added complexity. Where it's been useful for me is on the partition holding my standard release. Standard releases and their updates have gummed up my system on more than one occasion. It's nice to be able to roll back to a good snapshot.

---

### Post by Tadaen_Sylvermane on 2020-12-05
One thing I didn't think to mention is for installations / upgrades themselves. At the moment I have a 250gb ssd in my desktop. I keep 175gb for my data, 2gb for swap, and 30g for root.  I've personally had little to no success with upgrading Ubuntu between versions. I bypass by just doing a chroot installation on a fresh LV. Get it all configured, then it's a reboot and done. My machine is also fully usable during the time I'm building the chroot as it's nothing more than command line action. Once I've got a successful transfer and everything is good I dump the previous root volume.

Also allows me to revert with a simple reboot as well if something is wrong or I forgot something. Almost idiot proof really, something I desperately need.

---

