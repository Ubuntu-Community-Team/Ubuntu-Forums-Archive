---
title: "Choice of Root File System"
date: 2020-07-25
forum: Ubuntu, Linux and OS Chat
---

### Post by Graham1 on 2020-07-25
Hi All

With Canonical suggesting ZFS as a file system for Ubuntu, I'm curious as to what file system you will (or are) using on your root partition.

:)

---

### Post by ajgreeny on 2020-07-25
As I have almost no knowledge of zfs I will certainly be sticking with ext4 on all systems that I need to run exactly as I expect; I do not have time to deal with unexpected things happening on a working install.

I do expect to have a look at it, either using Vbox, if that is OK with zfs, or probably better, using a small testing system in dual boot on a laptop I use less than my main machine.

---

### Post by Frogs Hair on 2020-07-28
With all announcements regarding changes in Ubuntu I wait and see. I remember rumblings about Wayland being default too. It  seems 20.10 may include improved support for zfs. I use ext4 and after a little research I find no clear consensus on what file system is the best option.

---

### Post by mastablasta on 2020-07-29
ext4 for the root. BTRFS can be used well on /home

---

### Post by Graham1 on 2020-07-30
Wow, I'm surprised I'm the only person using a non ext4 partition as root. Having read reports of btrfs being a lot slower than ext4, I haven't noticed much difference tbh. To those running ext4, what is your recovery (or backup) procedure? Having tried zfs in boxes, recovery doesn't seem as good (when using timeshift with btrfs) but still early days I guess. 

:)

---

### Post by deadflowr on 2020-07-30
> To those running ext4, what is your recovery (or backup) procedure?
deja dup, always to external hard drives.

---

### Post by poorguy on 2020-07-30
I choose other because I don't care what partition is used.

I'll use whatever the default installer sets up at the time of install OOTB.

I used to set up all the different partitions for root and home and swap etc I don't remember anymore.

Nowadays I just insert the DVD and let it do the rest and always have good results OOTB with default partitions.

So whatever new partitions Ubuntu or other Linux distros I use want to create and use I'm cool with as long as it works.


Life Is Good. ):P

---

### Post by Graham1 on 2020-07-30
> **deadflowr said:**
> deja dup, always to external hard drives.

I've started using deja dup for backing up my home directory (int. ssd > int. sata). Does deja dup create incremental backups? Can this be used to restore the OS in the event of a system crash? (no gui). 

:)

---

### Post by Graham1 on 2020-07-30
> **poorguy said:**
> I choose other because I don't care what partition is used.

I'll use whatever the default installer sets up at the time of install OOTB.

I used to set up all the different partitions for root and home and swap etc I don't remember anymore.

Nowadays I just insert the DVD and let it do the rest and always have good results OOTB with default partitions.

So whatever new partitions Ubuntu or other distros I use what to create and use I'm cool with as long as it works I don't care.


Life Is Good. ):P

I used to go with the defaults but since becoming more confident with Linux, have started using different setups. For root, btrfs as it allows me to instantly restore the OS in case of a bad update or user error. Previously used Clonezilla but using TImeshift works well for me (gui or terminal). Home is on a ext4 partition and if I have had to (or chosen to) install the OS again, configuration is still in contact. Swap is on a separate partition as the swapfile doesn't seem to be recognised under btrfs.

:)

---

### Post by poorguy on 2020-07-30
> **Graham1 said:**
> I used to go with the defaults but since becoming more confident with Linux, have started using different setups. For root, btrfs as it allows me to instantly restore the OS in case of a bad update or user error. 


I don't recall having many issues from updates that broke my distro where a reinstall was necessary.
I usually created the problems I've had which broke my distro and I had to reinstall it.

> **Graham1 said:**
> 
Previously used Clonezilla but using TImeshift works well for me (gui or terminal). Home is on a ext4 partition and if I have had to (or chosen to) install the OS again, configuration is still in contact. 

:)

I just back up important files / folders to usb thumb drives as as needed.

---

### Post by TheFu on 2020-07-30
I loaded ZFS using the "experimental" install with 20.04.  Things were too different. Patching created a snapshot before continuing that I didn't request.  Who's gonna remember to remove that snapshot and all the others before other patching days?

BTRFS has had negative problems for use under for VMs for 10+ yrs.  Something bad seems to happen with CoW file systems run on CoW file systems.  [https://wiki.debian.org/Btrfs#Warnings](https://wiki.debian.org/Btrfs#Warnings)  The KVM guys have/had warnings too.  Redhat deprecated BTRFS ... but now Fedora is bringing it back?  I'm so confused.  Let me know when it doesn't lie to **du** and **df** commands.

ext4 for the root LV.  ext2 for the /boot partition.
f2fs for any portable flash media that doesn't need to be used in cameras or other limited devices.
zfs for some data and where the project maintainers REALLY, REALLY, make it suck if you don't use ZFS - I'm looking at the LXD guys.  Thinking about ZFS zpools more as directories that can be limited/expanded is a different way of thinking for many people.  Hopefully, LVM users have it down.  Don't think ZFS on Linux supports shrinking a zpools, which is a major fail in my book. That's why ext4 and not xfs is used.

---

### Post by guiverc on 2020-07-30
I use 'ext' as I think I know it the best.

I've used ZFS in BSD (now default), BTRFS (default with opensuse), and numerous others, but as a desktop user my needs are few, my hardware is old so lightness matters, but whatever works is fine with me. 

 Most my own installs are with *something-else* (or *manual partitioning*) so I can select whatever I want anyway, so defaults won't impact me personally anyway.

---

### Post by lammert-nijhof on 2020-08-05
I boot from ZFS and that works perfectly. However I advice to purge the crappy Ubuntu snapshot add-on "zsys". 

I boot and use ZFS and Ubuntu on desktop and laptop! My 2003 Pentium 4 HT Backup Server with IDE disks boots and uses ZFS with FreeBSD. Since more than a year I backup my ~50 VBox VMs (~500GB) from desktop to backup server using 1 Gbps Ethernet. The backup "send | ssh receive" takes 30 - 45 minutes dependent on the size of the updates to the VMs. The backup runs at 200 Mbps, because the 32-bits CPU is running at 95% on one of its two threads. Despite the ancient hardware the backup is efficient, because all data is stored & send lz4 compressed and only the changed records are sent (not the changed files as with rsync).

---

### Post by TheFu on 2020-08-06
> **lammert-nijhof said:**
>  only the changed records are sent (not the changed files as with rsync).

rsync over the network should only send changed blocks in the files, not an entire file.  But with a CPU from the early 2000s, that may not be so fast.
You have GigE ISP connection, but not a 64-bit computer? Just seems odd when they are $70 from off-lease vendors. Or does the govt there have 1x tariffs for computing equipment? I've seen that some places in the world.  Buy a $200 GPU and have to pay $200 in import taxes too.

---

### Post by zebra2 on 2020-08-06
As soon as >2.2T hard drives are standard this file system quandary should be decided.  Probably won't be EXT4 or NTFS. Right now I'm using EXT4 and NTFS. If it works don't fix it.  Also running Groovy, Wayland and Gnome 3.36.4 on three Laptops.  Never had it better than this.

---

### Post by aaronrv2008 on 2020-08-08
I chose XFS! It's by far my favourite :)

---

### Post by TheFu on 2020-08-08
> **aaronrv2008 said:**
> I chose XFS! It's by far my favourite :)

Perhaps there are technical reasons WHY you like XFS?

XFS has many things to like and a few things to dislike.  

The "Like" list is long:
[LIST]
[*]Supports huge sizes of file systems.
[*]Usually the fastest file system, but not always
[*]Rock solid. I've not heard of any data loss issues not caused by foolish admins or users, unlike "other" popular file systems, cough. XFS came from SGI and has been used at least 25 yrs.
[/LIST]

The "Dislike" list is short:[LIST]
[*]Cannot reduce the size of XFS file systems. Must create a new FS of the size you need, then move the data over and delete the older, larger, FS.
[*]LVM2 doesn't have built-in support for resizing XFS filesystems like it does for ext2/3/4.
[/LIST]

EXT4 has been getting faster and faster over the years and supports reducing the file system size. EXT4 is supported by LVM2 commands, so when we extend or reduce an LV, just adding the -r option will do the same with the file system. No separate command needed.

I really like file systems. After all, computing is all about the data, not the computer. A file system keeps our data safe - or it should - as the #1 purpose.  All the other things are secondary.  Anyone can make a file system that's really fast, but loses data. Admins don't really like that.

---

### Post by kevdog on 2020-08-09
I really like ZFS as I've been using it with FreeNAS and BSD for a few years and most recently with my Arch installs over the last year.  ZFS and specifically ZOL has come a long way in the last year or two -- I think on Arch the ZFS kernel patching is still out of tree but I think with Ubuntu ZFS is in tree.  I haven't tried it yet with Ubuntu as I'm just running basic ext4 installs. I've really done a big swaparoo the last several years, going from running various Linux distros on bare metal to pretty much all my linux installs now run virtualized.  I really like the virtualization and I really like the idea of dedicating one linux virtual installation to primarily one task.  I've even tried to go lighter with such servers running them as docker containers, however not all the servers seem capable of being run in a container (well they probably could be but I'm really not a docker expert and just starting to build my own images from alpine).  

My ZFS experience on linux has been great, however I don't think ZFS is actually meant to be run from within a virtualized installation.  I think ZFS wants access to the underlying hardware (as they say many many times in the BSD forums).  I've run a virtualized Arch ZFS on root FS on top of a ZFS file system as a test case.  I'm not sure the implications of doing this but it does seem to work -- possibly it would blow up if it were much more complex.

I like managing snapshots with ZFS through a utility known as zsnapzend.  It's pretty automated and it seems the author still actively develops the program and is accessible. I believe I found this backup utility mentioned on the Arch Wiki, however possibly it was somewhere else.  It doesn't have a GUI (which is a downside), however with my virtualized Linux servers I pretty much administer them all through an ssh terminal so it fits my work pattern nicely.  

I've been testing backup strategies and they all seem to work -- meaning I've done backup with every method.
For block level backup -- 
The VMs themselves are snapshoted every 6 hours and I believe I keep a copy of the snapshots for 2 weeks.
For each VM running ZFS, the home datasets, and etc datasets are snapshotted to another ZFS implementation

For file level backup -- I've been testing and running borg for a number of years.  I chose borg over some others in that its a delta backup strategy,  multiple backups can be retained, backups can be kept for a period of time and then scrubbed automatically, and all the backups are kept encrypted.  Vorta is a good frontend for this program that provides a nice GUI and the maintainer of the project is pretty accessible via github.  I've submitted a few bugs and they were addressed in a timely manner.

---

