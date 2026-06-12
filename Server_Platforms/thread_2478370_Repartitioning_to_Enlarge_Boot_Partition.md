---
title: "Repartitioning to Enlarge Boot Partition"
date: 2022-08-24
forum: Server Platforms
---

### Post by SAH62 on 2022-08-24
I installed Ubuntu on a Dell 2950 a few years ago, and accepted default settings when partitioning the hard drives. I recently ran into an issue with lack of space on /boot when I first tried to upgrade to 22.04 LTS. I went through the process of removing and purging old kernels, only to find that I still didn't have enough space. The only way I could complete the upgrade was to change the compression scheme to "xz" and run update-initramfs. That worked, but I don't want to run into this problem again in the future so I'm wondering if I can enlarge the boot partition.

Here's what I see using df and fdisk:

```
$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
tmpfs                        3.2G  1.1M  3.2G   1% /run
/dev/mapper/impala--vg-root  371G   35G  317G  10% /
tmpfs                         16G     0   16G   0% /dev/shm
tmpfs                        5.0M     0  5.0M   0% /run/lock
/dev/sdb1                    228M   71M  146M  33% /boot
/dev/sda1                    3.6T   48G  3.4T   2% /media/mybook
tmpfs                        3.2G     0  3.2G   0% /run/user/1000
$

```

```

$ sudo fdisk -l
[sudo] password for sah62:
Disk /dev/sda: 3.64 TiB, 4000752599040 bytes, 976746240 sectors
Disk model: My Book 1230
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xdb4bf07b


Device     Boot Start       End   Sectors  Size Id Type
/dev/sda1         256 976746239 976745984  3.6T 83 Linux


Disk /dev/sdb: 408.38 GiB, 438489317376 bytes, 856424448 sectors
Disk model: PERC 6/i
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0004f28c


Device     Boot  Start       End   Sectors   Size Id Type
/dev/sdb1  *      2048    499711    497664   243M 83 Linux
/dev/sdb2       501758 856422399 855920642 408.1G  5 Extended
/dev/sdb5       501760 856422399 855920640 408.1G 8e Linux LVM


Disk /dev/mapper/impala--vg-root: 376.11 GiB, 403844366336 bytes, 788758528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/impala--vg-swap_1: 31.99 GiB, 34351349760 bytes, 67092480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
$

```

Looking at /dev/sdb, it appears that I have 408.1G available on device /dev/sdb2 that isn't being used, correct? Is it possible to enlarge /dev/sdb1 to take advantage of this space? If so, how?

---

### Post by TheFu on 2022-08-24
So, you are kinda screwed.  Here's the important part of the output:
```
Device     Boot  Start       End   Sectors   Size Id Type
/dev/sdb1  *      2048    499711    497664   243M 83 Linux
/dev/sdb2       501758 856422399 855920642 408.1G  5 Extended
/dev/sdb5       501760 856422399 855920640 408.1G 8e Linux LVM
```

You cannot enlarge anything. /boot needs to be outside LVM, so any space inside the control of LVM isn't possible to use.  The partition(s) holding LVM PVs, VGs, and LVs, can't be reduced without destroying all the LVM stuff inside.

If it were me, I'd get a new HDD/SSD, carefully partition everything BEFORE doing the install to get the partitions and LVs how I like, then during the install, "do something else" when storage options are provided so that those existing partitions and LVs can be hooked up to mount points as needed.  Also, be certain to use GPT, not MSDOS/MBR partition tables.

For a desktop, something like this is my partition plan when using LVM:
```
# Part  mount           part_type       fs_type size
1       /boot/efi       EFI             fat32   50MB (dual+boot needs more)
2       /boot           LINUX           ext2    600MB
3       LVM             LVM             na      Remaining storage
 root   /               LV              ext4    35GB
 home   /home           LV              ext4    40GB
 var    /var            LV              ext4    1GB
 swap   swap            LV/SWAP         swap    4.1GB
```

For a server with lots and lots of RAM, I'd probably make the swap LV 500MB.  Having some swap is important.  /var may need to be resized larger, eventually.  Thanks to LVM, that is 5 seconds and 1 command.  Extending LVs is trivial. Making them smaller is difficult, so only allocate the storage needed for 3 months at a time.   I bet you'll never need the root LV to be larger.  Leave as much unused VG space as you can.  This will be used for snapshots and backup snapshot storage. That makes having perfect backups possible.

Would be good to see the output from 
```
sudo pvs
sudo vgs
sudo lvs
```
to see any funkiness in the LVM setup too.

BTW, a Dell 2950 is REALLY, REALLY, old. The power use alone would pay for a 3x-6x faster Ryzen 5xxx system.  Also, the Ryzen would be quieter, besides saving $10/month (or more) on the power bill.

---

### Post by SAH62 on 2022-08-25
Well, that's not what I was hoping to hear. It's too bad those defaults could lead to a problem like this. Here's the other output you asked to see:

```

$ sudo pvs
  PV         VG        Fmt  Attr PSize   PFree
  /dev/sdb5  impala-vg lvm2 a--  408.13g 32.00m
$ sudo vgs
  VG        #PV #LV #SN Attr   VSize   VFree
  impala-vg   1   2   0 wz--n- 408.13g 32.00m
$ sudo lvs
  LV     VG        Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   impala-vg -wi-ao---- <376.11g
  swap_1 impala-vg -wi-ao----   31.99g
$

```

---

### Post by TheFu on 2022-08-25
> **SAH62 said:**
> Well, that's not what I was hoping to hear. It's too bad those defaults could lead to a problem like this. Here's the other output you asked to see:

```

$ sudo pvs
  PV         VG        Fmt  Attr PSize   PFree
  /dev/sdb5  impala-vg lvm2 a--  408.13g 32.00m
$ sudo vgs
  VG        #PV #LV #SN Attr   VSize   VFree
  impala-vg   1   2   0 wz--n- 408.13g 32.00m
$ sudo lvs
  LV     VG        Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   impala-vg -wi-ao---- <376.11g
  swap_1 impala-vg -wi-ao----   31.99g
$

```

32G of swap?!!!!   Are you a hosting provider who hates their customers?
The defaults for the size of /boot/ have increased over the last decade.  I suspect this partitioning was setup using defaults before 2015.  I think the new default /boot/ size is 1G, which I find offensively large, but that's me.

BTW, I have a /boot/ on one of my systems what probably started with 14.04 server ... and /boot is too small for me too.  
```
$ dft
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/sda2                                   ext2  237M  185M   40M  83% /boot
/dev/mapper/istar--vg-root                  ext4  101G   60G   37G  62% /
/dev/mapper/istar--8TB--B-jellyfin_varlib   ext4   89G  6.9G   77G   9% /var/lib/jellyfin
/dev/mapper/istar--8TB--B-plex_varlib       ext4   89G   40G   44G  48% /var/lib/plexmediaserver
```

I removed some things to protect the guilty. ;)  Normally, I'd have the 'root' LV at around 20G (for the time this was installed), but Plex media server metadata and DB files blew through that amount quickly, so I used LVM to extend it.  Eventually, there wasn't any more room on the 4TB drive and I created new LVs on a different disk to be mounted for jellyfin and plex DBs + metadata crap.  Both media centers have the exact same media files under management, but Jellyfin is much more efficient.

I'll be doing a fresh install of 20.04 on this system soon. I've already installed the new SSD,  partitioned, and setup the LVM:
```
$ sudo lvs
  LV              VG             Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  jellyfin_varlib istar-8TB-B    -wi-ao----   90.00g                                                    
  plex_varlib     istar-8TB-B    -wi-ao----   90.00g                                                    
  root            istar-vg       -wi-ao---- <102.27g                                                    # old
  swap_1          istar-vg       -wi-ao----   <3.61g                                                                 # old
  home            vg00           -wi-a-----   25.00g                                                    
  root            vg00           -wi-a-----   35.00g                                                    
  swap            vg00           -wi-a-----    4.10g                                                    
  var             vg00           -wi-a-----   35.00g 
```
vg00 is the new storage VG.
I also use LVs for virtual machine block storage. Libvirt and virt-manager know how to handle it in the GUI. /var is where KVM VMs end up, so having 20G there for toy VMs is sometimes handy.  It is also where LXD containers use storage. I have a few of those, but they are all under 2G in size and share from the same ZFS pool because I'm too stupid to figure out how to get LXD to use LVM instead.

The system above has about 40TB connected, BTW. About 50% is live and about 50% is for a delayed media rsync mirror.

There, that's most of my dirty laundry. ;)  I really need to do that fresh 20.04 install. I'm just worried that I won't be able to get netplan to do what I need for containers, VMs, and for all the different subnets this system connects.  It has 5 NIC ports and 2 are passthru for VM exclusive use (security).

---

### Post by SAH62 on 2022-08-25
Given that I have what I have, would it make sense to create a snapshot of the file system contents, repartition, and then restore the snapshot?

---

### Post by TheFu on 2022-08-25
> **SAH62 said:**
> Given that I have what I have, would it make sense to create a snapshot of the file system contents, repartition, and then restore the snapshot?

No. A snapshot would be lost.  Snapshots aren't backups. They just freeze blocks with LVM.  Partitions are lower level and requires wiping the LVM stuff if any thing besides "extending-right" happens, so the snapshot would be useless.  Plus, your system has both logical and extended partitions, making it just a bit uglier.  That's how we had to do things before GPT and it was the default for Ubuntu+LVM installs.   When the installer finally started creating GPT partitions on empty disks, I nearly cried, because it was 8 yrs after when it should have happened, IMHO.

What you could do, is to use your normal backup methods, which could/should include snapshots ... to get an unchanging file system to be copied from using the backup process.  Snapshots aren't backups. They are a tool to be used to make better backups.  

And a simple copy of the data isn't a backup.  Backups need to be versioned and contain all the metadata tied to each directory and file type.  Owner, group, ACLs, xattrs. Without those, we don't have a backup that can actually be restored.

---

### Post by SAH62 on 2022-08-25
So what would you suggest if, for example, I retired this server and replaced it with a newer one? I need to clone the contents of the file system on the existing server to the new server.

---

### Post by TheFu on 2022-08-25
It is about the storage, not the computing.

Regardless, your backup and restore processes should handle not just backups and restores to the same hardware, but restoring to completely different hardware. If not, I'd say you need better backup methods.

I've posted 50+ times about backup and restore methods in these forums.  This isn't something you'll pick up in an hour. Sorry.

The restore isn't tied to any underlying storage setup. If I like, I could use completely different file systems and volume management.  My restore process takes between 20 and 45 minutes to get the system back, excluding huge data.  Huge data takes whatever it takes, but most of my systems have less than 20G of OS+data, so restoring is under that 45 min time.  I've used my methods to migrated from release to release after failed OS upgrades too.  The method is very flexible, but the restore isn't 1-click either.  There are trade-offs.  Flexibility, quick backups, storage efficient versions and fast-enough restores are my key needs.  All systems have at least 90 days of daily backups (except large-huge media files). High risk systems have 180+ days of versioned backups.  Most high-risk systems don't have much or any data, fortunately.

I won't recommend much for you, since your needs and skills are not the same as mine.  Do some reading. Ask some questions, but know that I've only used about 5 different backup tools and wouldn't change from the 1 I use today without a really good reason.  There are proponents for each backup tool. They all have flaws, including rdiff-backup, my poison for backups and restores.  The trick is to find a poison you can tolerate. ;)

---

