---
title: "enlarge root partition"
date: 2012-07-20
forum: Server Platforms
---

### Post by MitsuTomoe on 2012-07-20
Hi, I'm a newbie on Ubuntu, so sorry if my question seems stupid.
I've got a server with Ubuntu 12.04, with a 1 TB disk. There are 3 ext4 volumes : 10 GB, 990 GB, and 500 MB for swap. Here is df : ```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       9,8G  8,3G 1009M  90% /
/dev            994M  4,0K  994M   1% /dev
none            199M  256K  199M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            994M     0  994M   0% /run/shm
/dev/sda2       921G   17G  859G   2% /home

```
Problem is that 1st volume is nearly full . Postgres databases were installed there (in /etc/postgresql) . 
So I must enlarge partition or change postgres data directories. What's simplest and safest ? 
In an ideal world, I would like to create a volume reserved for postgres, is it difficult/dangerous ?
Thank you for your help

---

### Post by ian dobson on 2012-07-20
Hi,

I would move your Postgres databases to your second partition. Resizing root is possible but abit dangerous. If 500Mb is enough for your database and you have enough ram then why not get rid of swap and craate a database partition.

Also maybe have a look in /var/log to see what you can delete there, and maybe uninstall old kernels using apt-get with the purge option.

Regards
Ian Dobson

---

### Post by thnewguy on 2012-07-20
I think the safer approach would be to move your database. Maybe you could create a directory under your /home partition for it. That way you wouldn't have to resize anything, just change DB locations.

another way to go would be to add a second hard disk to your server. Put a big partition on the new disk and move your database to the new volume. That would keep your DB info separate from the rest of the system and avoid resizing too.

---

### Post by LHammonds on 2012-07-20
I would agree that the least problematic solution for now would be to move the location of your database under the /home file system since it has the most space available.

But no matter what you do, be sure you have a full and 100% verified backup of your system in case you need to restore.

Ideally, you would want to isolate your root partition from data that keeps on growing.  Whenever the root system fills up, the OS becomes unstable and may cause the system to lock up, fail to boot, etc.

If you have a chance to re-configure that server or create a new one, you might want to investigate into using Logical Volume Manager (LVM) and separate each of the main partitions into their own logical volume so you can manage growth and security much easier over time (including the root file system!).  For an example of what I am talking about, take a look at [how I setup my Ubuntu Servers]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191").  Even though I use them in virtual machines, the logical setup would be the same.  Managing Ubuntu installed on a physical server (e.g. bare-metal install) would require a bit more hands-on approach to managing the hardware...such as hardware or software RAID, NIC drivers, etc.

LHammonds

---

