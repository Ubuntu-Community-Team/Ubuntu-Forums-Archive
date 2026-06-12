---
title: "Replacing lower-capacity disks in Ubuntu Server with LVM without data loss"
date: 2023-06-13
forum: Server Platforms
---

### Post by soportetowertravel on 2023-06-13
Hello everyone,

I have a computer running Ubuntu Server 20.04 with 5 mechanical disks of different sizes. I have combined their storage using LVM (Logical Volume Manager). Additionally, I'm using UrbackUp to back up data from other computers. Unfortunately, my motherboard can't support more than 5 disks.


I'm wondering if there's a way to replace the lower-capacity disks without losing any data. I'm asking because I'm not entirely familiar with how LVM works. Could someone please provide guidance or instructions on how to accomplish this?




This is the output of an: lsblk
[IMG]https://i.ibb.co/N6VwNtq/Captura-de-pantalla-2023-06-13-173409.png[/IMG]

And this is: vgdisplay
[IMG]https://i.ibb.co/hK7kHsH/Captura-de-pantalla-2023-06-13-173318.png[/IMG]


Thank you in advance for your help!

---

### Post by MAFoElffen on 2023-06-13
Yes.

If you would have used the 'Forums Search" facility for the keywords "lvm replace disks" the most recent find from that would have been my post, which I just answered a few days ago in detail: [https://ubuntuforums.org/showthread.php?t=2487682&p=14146750#post14146750](https://ubuntuforums.org/showthread.php?t=2487682&p=14146750#post14146750)

I did the example on Ubuntu Server 22.04.2 LTS... All the commands to do that are there for non-root drives.

For the root drive, I did this in 2014: [https://ubuntuforums.org/showthread.php?t=2487682&p=14146750#post14146750](https://ubuntuforums.org/showthread.php?t=2487682&p=14146750#post14146750) --- Basically... What you need to do is create the root disk with an EFI (for ESP, type ef00), BOOT (for ext4, type 8300), and ROOT Partition (LVM_data, 8e00) to set the framework foundation for the root disk. The attach it to the machine.

Then prep partition 3 as a PV, and move the data from your first disk, off the old root drive, onto it. The rsync the EFI and BOOT partitions over the the new drive. Once done, then you can remove the root drive and boot from that drive...

I would strongly recommend that you do some other things prior to any of that...

First, I would do a good backup to use as a fallback. Things happen when you don't plan for them.

Second, if you were one of my customers (and I would charge them for consulting), I would have a talk to you about isolating and segmenting your system into manageable LVM partitions. From what you posted, you have all your eggs in one basket. One single LVM VG partition (ubuntu-vg) and everything inside it, in a single LV (ubuntu-lv). It probably started one as a canned default install...

These are some of my rules of thumb for LVM. First, I always create GPT partition tables with LVM Partitions, instead of letting LVM take the full disks. Using LVM without partitions is asking for troubles down the road. Next is that I usually setup at least 4 Volume groups, for root, swap, home, data. 

I create a root VG to install the system to. Then the system can be repaired, upgraded, migrated, etc, without affecting the other things that are more important to us, that the other can have snapshots taken, and backups made more easily because we have a places for them to reside. I create other VG's, which I mount into that system. If you lay it out that way, the the other places (VG's) can be exported and imported into a new system. What an LVM export does, is to remove the machine ID from the LVM metadata, so that it can be imported / migrated to a new machine.

The default install of LVM lets your LV's take 100% of your Volume groups. Tweak that yourself, to keep LV's at 'less than' 80% of the VG. plan to leave space free for snap shots and other things. Altogether, LVM runs best if it uses less than 80% of your total space. This takes some planning.

That said, you could do some finagling to do that and move things around... online / live... Which will work just fine and is possible with a very high percentage of success... or migrate your system into a new, fresh (empty) foundation, and restore the data from your backups. Doing it this way (migration), you would also have your old disks, untouched, as another fallback.

I know I gave you two options to decide on. Both are possible. It is your decision on which path to take.

Your original install (with LVM2) was probably when you first started using LVM2, and then learned more about it along the way... Growing your system in time. Before you start the next steps, you have time to get a plan together, to do a few simple things to make things easier on yourself,  to be able to learn and grow further down your path. LVM2 has many features that most people have only scratched the surface of.

---

### Post by TheFu on 2023-06-14
TL;DR, but I'm sure MAFoElffen's post is brilliant!

Use **pvmove**.

I've been burned by using LVM to concatenate/stripe data across multiple disks that weren't in RAID10 mode (don't use RAID01 mode!).  Be careful with doing this again.  After losing 80% of my data, I stopped doing that.

You do know that you can add a PCIe HBA to the system and connect more SATA/SAS HDDs to it.  Or get an external eSATA HBA and connect an external array with 1-5 HDDs to a single eSATA-pm slot.  Just be certain the PM (Port Multiplier) card is compatible with your OS and your system.  Also, just because there are 2 eSATA ports on the back of an HBA, that doesn't mean both can be used concurrently, making 10 extra disks available.  I've been burned by this.

---

### Post by soportetowertravel on 2023-06-16
Thank you very much for your responses. Now I will see how I can apply it. I still consider myself somewhat of a novice in Linux. The computer with the 5 disks was just a personal project, a hobby in my free time, which later caught the boss's attention and basically became official. I'm just a support guy, but I guess that's how you learn, by trial and error.
Thanks again, I'll figure out the best way forward and I'll let you know when I succeed.

---

### Post by TheFu on 2023-06-16
**Update:** This post was because I was confused and thought there were (5) 4TB disks, not a few disks making up a total of 4TB.  The answer changes drastically based on the amount of storage.

**Nothing below this line was changed. **Left for people with more storage:

For the amount of storage you have, I strongly recommend ZFS in a RAIDz or RAIDz2 configuration.

You should get some formal training --- at the company's expense.  Get that added to your annual improvement plan.  This training could be classes or going to conferences.  It is good for you AND them.

Trial and error is fine for virtual machine testing, but not on production systems.

---

### Post by darkod on 2023-06-16
But isn't ZFS a little overkill for a server with only 4TB of data? That can barely be called storage server.

I like ZFS as a product but for someone that doesn't already know it, for only 4TB of data and a server that currently doesn't even seem to have raid, I would prefer a less complex solution. Another thing I don't like with ZFS (but this is for my home server, not a production server in a company business), is the "requirement" to use same size disks. Or to lose part of the bigger disks if they are not the same. For home server and disks bought at different times, this can be an issue. Just as an example, after recent HW update I now have 2x 2TB NVMe, 3x 3TB SATA and 1x 4TB SATA in my server. Hence ZFS was out of the question. And I moved to snapraid because it allows me to use different size disks and it does cover my home server requirements (IMHO). Plus using snapraid sort of renders LVM obsolete depending on your use case. So maybe that is something that you can consider too.

First you need to think on the high level plan. You said the server only has connections for 5x disks. Unless you implement some new PCIe-SATA adapter as mentioned above, that means you can't even add one more disk without disconnecting one of the current 5x disks.

So, the plan will be very different depending if you can add adapter card and new disk(s) without disconnecting any of the current disks. Migrating LVM in such case is very easy. If you decide to also implement raid like mdadm that is another step that you would need to include in your planning.

PS. I forgot to add something very important related to snapraid. In my use case my data is fairly static which is good for snapraid. But for storage server with high frequency of data change etc, it is not really recommended to use snapraid.

Then there are other things to take into account. I see you use only one single big LV. In such case, you don't really use the full potential of LVM. You had LVM useful for adding more disks (depending how many there were at the start), but now that you used all 5x SATA ports, that is as far as you go without adding new SATA card. So if you plan to continue using LVM just as one big LV, you might as well replace it with simple mdadm raid6. That gives you double parity, and one big data volume. I would actually do for example 5x 64GB (or another size) mdadm raid1 for system volume, and then the rest 5x mdadm raid6 for the data partition, etc. All this assuming you have only 5x disks in the future too. Because the number of disks depends not only on free SATA ports, but also on case space to install the HDDs.

---

### Post by TheFu on 2023-06-16
> **darkod said:**
> But isn't ZFS a little overkill for a server with only 4TB of data? That can barely be called storage server.

Ah ... you are correct.  I looked too fast and saw 5x4.1TB disks ... and thought it was concatenated storage ... so 20TB.
For just 4TB or even 8TB, in a business setting, I'd do it very different.

For 8TB in a business, I'd setup a RAID1 with 2x8TB disks (mdadm) and buy a 3rd disk for backups.  I'd create a partition of a specific size for mdadm's use, to make it easy to use different disks with slightly different sized later.  And I'd make the RAID array the PV for LVM.

I don't like RAID5 on large disks.  Ran a RAID5 array for about 7 yrs.  Performance sucked.

I'd use HDDs with 5 yr warranties - which basically means WD-Black line or WD-Gold DC drives.  WD thinks these will last very long, but it depends on your budget and the environment for the setup.  I'd avoid Seagate, due to some bad experiences. Others here either don't remember or didn't have the same bad problems with some Seagate models over the decades.  What I do remember is that Seagate management fought a recall for over a year on some terrible design flaws, back with 1TB was the largest size HDDs available.  I don't trust Seagate management.  There was an overheating issue in the mid-1990s - another poor design. Fortunately, my employer was able to pressure them into replacing about 2000 drives in our location after we had so many failures.  But this is me. Others have different experiences and things that will run them away from any specific vendor.

Anyway, there aren't many real choices remaining for spinning rust anymore. Toshiba, WD (HGST too), Seagate and 1 fairly unknown brand ... which I can't find now.

---

### Post by MAFoElffen on 2023-06-17
Curious... Then what would you call this?
```

root@Mikes-B460M:/home/mafoelffen# lsblk -o name,mountpoint,size,label,fstype,type -e7
NAME        MOUNTPOINT   SIZE LABEL    FSTYPE     TYPE
sda                      1.8T                     disk
&#9492;&#9472;sda1                   1.8T datapool zfs_member part
sdb                      1.8T                     disk
&#9492;&#9472;sdb1                   1.8T datapool zfs_member part
sdc                      1.8T                     disk
&#9492;&#9472;sdc1                   1.8T datapool zfs_member part
sdd                    476.9G                     disk
&#9500;&#9472;sdd1                    16M          ext4       part
&#9500;&#9472;sdd2                 476.3G          ntfs       part
&#9492;&#9472;sdd3                   607M          ntfs       part
sde                      1.8T                     disk
&#9492;&#9472;sde1                   1.8T datapool zfs_member part
sdf                      1.8T                     disk
&#9492;&#9472;sdf1                   1.8T datapool zfs_member part
nvme1n1                  1.8T                     disk
&#9492;&#9472;nvme1n1p1              1.8T kpool    zfs_member part
nvme2n1                  1.8T                     disk
&#9492;&#9472;nvme2n1p1              1.8T kpool    zfs_member part
nvme0n1                  1.8T                     disk
&#9492;&#9472;nvme0n1p1              1.8T kpool    zfs_member part
nvme3n1                  1.8T                     disk
&#9492;&#9472;nvme3n1p1              1.8T kpool    zfs_member part
nvme4n1                931.5G                     disk
&#9500;&#9472;nvme4n1p1 /boot/efi    512M          vfat       part
&#9500;&#9472;nvme4n1p2 [SWAP]         2G          swap       part
&#9500;&#9472;nvme4n1p3                2G bpool    zfs_member part
&#9492;&#9472;nvme4n1p4              927G rpool    zfs_member part
nvme6n1                  1.8T                     disk
&#9492;&#9472;nvme6n1p1             1000G datapool zfs_member part
nvme5n1                  1.8T datapool zfs_member disk
&#9500;&#9472;nvme5n1p1              1.3T          zfs_member part
&#9492;&#9472;nvme5n1p2               10G datapool zfs_member part
root@Mikes-B460M:/home/mafoelffen# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              438M  1.32G       96K  /boot
bpool/BOOT                                         436M  1.32G       96K  none
bpool/BOOT/ubuntu_2cwpns                           436M  1.32G      436M  /boot
datapool                                           819G  3.92T      307K  /data
datapool/DATA                                      819G  3.92T      307K  none
datapool/DATA/ubuntu_2cwpns                        819G  3.92T     10.0G  /data
datapool/DATA/ubuntu_2cwpns/ISO                    377G  3.92T      377G  /data/ISO
datapool/DATA/ubuntu_2cwpns/KVM-VM                 432G  3.92T      432G  /data/KVM-VM
kpool                                             1.55T  1.86T      279K  /KVM_Pool
kpool/KVM                                         1.55T  1.86T      279K  none
kpool/KVM/ubuntu_2cwpns                           1.55T  1.86T     1.55T  /KVM_Pool
rpool                                             19.5G   872G       96K  /
rpool/ROOT                                        14.3G   872G       96K  none
rpool/ROOT/ubuntu_2cwpns                          14.3G   872G     7.28G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   872G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   872G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   872G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      7.00G   872G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   872G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  6.79G   872G     6.64G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   872G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    188K   872G      188K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt               109M   872G      109M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             48.4M   872G     48.4M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   215M   872G      215M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   872G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.49M   872G     1.49M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   872G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   872G       96K  /var/www
rpool/USERDATA                                    5.23G   872G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  5.23G   872G     5.23G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        2.17M   872G     2.17M  /root
root@Mikes-B460M:/home/mafoelffen# zpool list
NAME       SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool     1.88G   439M  1.45G        -         -     0%    22%  1.00x    ONLINE  -
datapool  9.09T  1.50T  7.59T        -         -     1%    16%  1.00x    ONLINE  -
kpool     7.27T  3.20T  4.06T        -         -     0%    44%  1.00x    ONLINE  -
rpool      920G  19.5G   900G        -         -     1%     2%  1.00x    ONLINE  -
root@Mikes-B460M:/home/mafoelffen# zpool status -v
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:00 with 0 errors on Sun Jun 11 00:24:01 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    bpool                                   ONLINE       0     0     0
      0196ab45-3ee2-894e-b725-39560409109f  ONLINE       0     0     0

errors: No known data errors

  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 00:13:57 with 0 errors on Sat Jun 17 03:54:12 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

  pool: kpool
 state: ONLINE
  scan: scrub repaired 0B in 00:06:07 with 0 errors on Sun Jun 11 00:30:08 2023
config:

    NAME                                 STATE     READ WRITE CKSUM
    kpool                                ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1  ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1  ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1  ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:14 with 0 errors on Sun Jun 11 00:24:16 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   ONLINE       0     0     0
      ae13efaa-d1cf-ec40-86a6-2883f0e07102  ONLINE       0     0     0

errors: No known data errors

```
This server is in a micro ATX case. I have 3 drive bay slots empty.

Write speed sustained is in the GiB/s ranges. Integrity is sound. Expected life of current SSD's are over 10 years. Most RAID's are of same size partitons. But you can always add vdevs of differing sizes to a pool, just as you can with PV's to LVM2 VG's.

I can do online scrubs, resilvers, snapshots, move data, etc... On a live filesystem.

But then again, I have been using ZFS since 2015...

As you both know, I never let mdadm, LVM2, ZFS, or BTRFS take a full raw disk. I put them inside of respective partitions. In years doing this, Whenever I did that (used raw disks without a partition table), I got burnt. Different sized disk of the same brand, make and model, were not the same size. Random writes did weird things in unconfined spaces... ETC. But if I put them in a controlled contained space... None of those problems came up.

When it comes down to it, file managers add value. Whether mdadm, LVM2, ZFS, BTRFS. etc. Why not learn and use them? Most people only scratch the surface of what they use. If they knew about them, they would be using more of the capabilities of them.

EDIT:
I do a lot of backups. I used to be very narrowly focused with believing that I needed hardware RAID, then software RAID (mdadm). I was pushing using mdadm for a long time. I learned, later, with both, that in recovering degraded RAID arrays, that instead of fixing a degraded RAID that it was much faster just to build a new array, assemble and restore. Run my transaction log and be right back up. I still use forms of RAID now, not for integrity, but rather for speed and throughput.

Server is uptime. In a disaster, how much time will it take to get back up and running. Before that, more important, how came I prevent that disaster, and just stay up. Enter LVM2 and ZFS. I can adapt to various changing situations, and stay up. If a disaster occurs, I can get back up quickly. Both are flexible and adaptable. I don't think either is overkill. You only have to use what you need. 

As for RAID internal in LVM2 and RAIDz in ZFS... I fell that ZFS has the advantage. Both are easy to define and get up... ZFS has better monitoring, and tools to get them back up if there are problems. ZFS RAIDz has rekindled my use of and faith in RAID arrays, in a way that I can see value in how it recovers, repairs and is just 'trustable' as heck. And even if I do break something, which I do pushing things past their limits (and which I do a lot, on purpose, on a regular basis), it still runs above 1.5GiB/s throughput in a degraded state... I said to myself, this is more like it. This is fun and exciting again. This is how it should be... That is just my experience with that.

Right?

---

### Post by TheFu on 2023-06-17
> **MAFoElffen said:**
> 
As you booth know, I never let mdadm, LVM2, ZFS, or BTRFS take a full raw disk. I put them inside of respective partitions.
 In years doing this, Whenever I did that (used raw disks without a partition table), I got burnt. Different sized disk of the same brand, make and model, were not the same size. Random writes did weird things in unconfined spaces... ETC. But if I put them in a controlled contained space... None of those problems came up.

I do the same.  Well, except I don't use BTRFS.  I'm waiting for a 1 disk system to need an upgrade to try it for a few months. I just don't have any of those to spare today.

> **MAFoElffen said:**
> 
When it comes down to it, _file managers_ add value. Whether mdadm, LVM2, ZFS, BTRFS. etc. Why not learn and use them? Most people only scratch the surface of what they use. If they knew about them, they would be usig more of the capabilities of them.

I suspect you mean volume managers, not file managers?

For very simple needs like Linux containers or tiny VMs, I won't use a volume manager, but for anything where I just might need something complex in the future, I do.  Of course, the host system for both of those **will definitely be using a volume manager**, even if it has just 1 storage device with 512GB of space.

---

### Post by MAFoElffen on 2023-06-17
Yes, thanx, Volume Manager. Jeeze. (I'm a little loopy when I get home from work at 2am in the morning.)

With ZFS and ZFS RAID-Z, you can switch out a vdev at a time with larger disks, and set with autoexpand=on, it will grow the pool. On RAIDZ, this will do it on the last vdev getting resilvered. 

There is a new RAID-Z expansion feature, that I think they have been working on for over 10 years. It finally went live last year. I haven't tried it out yet. Where you can add another vdev to the RAID-Z array, and it will expand the RAID-Z array. accordingly. There are a few commands to run , for it to recognize the extra space if it doesn't recognize that right-off. It has a ZFS sort of caveat. When you add a vdev to a ZFS pool or RAID-Z array, it doesn't balance out the data that is already written there, unless you "rewrite it". So either by deleting and restoring from a backup, or... people have come up with scripts to rewrite files in-place, one, by one, until everything is rewritten to the filesystem.

This is not something I have even considered with LVM2. I just added more PV's to the VG. LVM2 is just easier to work with for a lot of it's features. Changing the size of LVM2 RAID is easy, fast and painless. LVM2 and ZFS assemble arrays in very little time, compared to mdadm. You can declare and be ready to use in less than a minute. Resilvering a ZFS 10TB RAIDz-2 pool takes me about 15 minutes.

mdadm, I love that you can add a disks, grow, and convert a RAID array type. I think that mdadm is the only one where you can convert RAID types (in-place) without having to just start over. It's a feature, but the time spent to actually do that, it is faster just to destroy the array and start over as a new array, then restore your data. Remember when I was working on mdadm-gui? mdadm just has soooo many command line options and flags, for just one base command. I still have to look at the man page to find it's many obscure options.

Each has it's own things it does better, and not.

---

### Post by TheFu on 2023-06-17
Ever run into HP-AutoRAID boxes?  They'd automatically configure for the greatest protection of all data based on the disks inside.  They were dying off before I'd even learned about them.  Removed a few  AutoRAIDs from service (as a systems architect, not actually touching anything).  The replacement was a SAN connection into EMC frames across the street in a new DC.

I can't believe there isn't a wikipedia page just for AutoRAID!

---

### Post by darkod on 2023-06-18
This is a great discussion but I think we scared off the OP. :)

---

### Post by soportetowertravel on 2023-06-22
> **darkod said:**
> This is a great discussion but I think we scared off the OP. :)

Just a little scared... I am still reading the discussion to learn more :) Thanks.

---

### Post by MAFoElffen on 2023-06-22
Please do not be scared. LOL. I know there is a whole lot of information there. We all would love for you to succeed in what you want to do. LVM2 has been around for a long time, and is tried and true. It is very flexible in what it does and what it can do.

As with anything, you have some level of risk, which you accept a certain level of risk. All 3 of us will agree---> As with any file system or volume manager on any OS, have good backups. There is no replacement for that step. Always nice to have a fallback to go to if things go bad.

I learn mostly by diving in, getting my hands dirty, and doing things. It's the journey in learning new things, and gaining experience. We all started from "some" type of beginnings.

---

### Post by TheFu on 2023-06-23
If you are using LVM and just need to migrate each disk to a larger one, then using **pvmove** is the way.  You can do that while the system is live, 1 disk at a time.  

Of course, you'll need to have storage connections for as many extra disks as you will be using **pvmove** on concurrently. With only 1 spare device port, you'll do it 1 at a time and pull the old disk out, replace a new empty disk for the 2nd pvmove command and repeat.

pvmove handles the connection to VGs and LVs for us.  It really is THAT simple.

An please don't post images of text.  Select/paste wrapped in forum code tags would be much better. Then we can copy/paste relevant parts.

When I want an overview of LVM there are 4 commands I use:
```
lsblk -e 7 -o name,type,size,FSAVAIL,FSUSE%,fstype,mountpoint
sudo lvs
sudo vgs
sudo pvs
```
Those provide all the information needed 99% of the time with LVM.  Of course, only you know how many extra SAS/SATA ports the system has.

---

