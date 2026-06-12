---
title: "Very slow access to ext3 volume with ext2Fsd on XP/Trusty Tahr dual boot laptop"
date: 2014-05-09
forum: Server Platforms
---

### Post by Cbhihe on 2014-05-09
Config [Dual boot: XP SP3 + Trusty Tahr, on Intel(R)Core 2 Duo - T9300 at 2500GHz - 64 bit enabled, SATA 200 GB internal drive, 4 GB RAM].
         + additional 4GB FAT32 SD card  

I re-(re-(re-installed)) a dual boot, always preserving the NTFS partition with the XP OS. I had my share of problems.

First I repartitioned a FAT32 partition to make room for Ubuntu and to reserve an Ext4 volume to be shared between Lx (as /home) and Win XP (as D:\). 
After a short test drive, Ubuntu was fine in its own space on the drive ... So I installed Ext2Fsd in Win XP and realized, after configuration of volume labels and all, that Win XP had difficulties to read and write on Ext4.  In fact it cannot write at all...  

So I repartitioned from scratch with GParted (latest version) from my live CD for Trusty Tahr and made the shared volume Ext3 after 2 more re-installs. (1st re-install failed when reconfiguring GRUB2, for some obscure reason, leaving me no choice but to abort - nice that it gave me that possibility).
 
After second re-install, I went to work directly on XP, moving profiles to be shared onto D:\ (/home) and more. I could read and write at the cost of extreme slowness. For instance opening an AOO *.odt file on D:\ would be a rather long second or two or three, no, four (!) in starting. (that's the delay between double-click on the icon and something beginning to happen). Completely unusual. 

So unusual in fact that everything stops during that "rather long second". 
Looking at processes and events with System Explorer, I can see that CPU usage shoots to 100% systematically and w/o interruption and a number of warning event are logged with ID (50), namely related to Ext2Fsd. I went on to check the error status based on the hex code of these events: The last word was 0xC0000123: meaning "STATUS_FILE_DELETED".
From MS, 0xC0000123 stands for: "An I/O request other than close was performed on a file after it was deleted, which can only happen to a request that did not complete before the last handle was closed via NtClose." Thx very much.

Opening an .odt file, working on it and saving it in D.\ was just the beginning.
What happens with Firefox and Thunderbird was worse.
Their respective profile folders were moved to D:\ (formatted as Ext3) , to be shared with instances of the same apps under Lx.  
Both apps seem to hog CPU time like crazy, every time they do anything, such as opening a new browsing tab or receiving an email message. RAM usage remains stable but swapping  increases dramatically. Moving profiles back to C:\ (NTFS) suppressed the problem.

Where the problem lies is clear. How I can fix this ? 
*(... of course I can start again a fourth time with a clean slate ...)*

sorry. post way too long.

---

### Post by sudodus on 2014-05-10
I don't know any better tool than  Ext2Fsd for reading ext file systems in Windows. If it does not work well enough for you, I suggest that you re-think your concept.

In a dual boot computer,

- Windows runs in a partition with the NTFS file system, usually C:
- Linux runs in a partition with the ext4 file system, maybe /dev/sda5 (if installed in a logical partition inside an extended partition)
- Linux has a swap partition, maybe /dev/sda6.

***I suggest that you create a data partition with with the NTFS file system***, usually D: in Windows, and /dev/sdb7 in linux.

There are good built-in tools to read the NTFS file system from linux, so it is a good location for files that should be available from both operating systems.

---

### Post by Cbhihe on 2014-05-10
@sudodus
(nice username!)
Txs for yr input.  :-)

FAT-nn
I need journaling > FAT is out. 
NTFS 
 .. does have basic journaling and ACL for windows. 
 .. ignores Lx permissions on files and folders, laying all files bare and open to whomever has access to the Win OS boot. 
NTFS-3g
  .. heeds Lx permissions 
  .. infamous for its caching support and for its encryption capability. 
  .. fares very not-well when dealing with fragmented files (i.e. CPU shoots to 100% and yr productivity to 0%), something that is bound to happen on data volumes being unknowingly abused by Win users...  
Correct me if I am wrong. If I am right, however, a lot of misleading reports on the net should pulled or revised. Nihil nove sub sole.

Initially NTFS vs FAT32 vs Ext-n  were options I weighed as so many did in this community. I finally decided going for Ext3 on my shared volume D:\  (/home under Lx).
I surmise (have yet to confirm it) that the problem in my post (extreme slowness + high journaling + 100% CPU use when accessing D:\ from Windows) may have been partly related to an inconsistency in my partitioning the extended volume within which Lx resides on my internal drive. Like so:

Boot sector --  /dev/sda2    -   Ext4
swap -- /dev/sda3
Extended partition -- dev/sda4     - Ext4
       boot block -- /dev/sda5        - Ext4
       /  (root)  -- /dev/sda6,          - Ext4
      /home (or D:\)  --  /dev/sda7 - Ext3 
     /var  -- /dev/sda8                  - Ex3
Free space

I believe that perhaps having an extended vol. w/ Ext4 format, while logical partitions in it show Ext3, was inconsistent for read/write access from Windows (with a little help from its friend Ext2Fsd). The best way to check is probably to reformat all the non XP vol and start again fresh. I have just done that (4th time and counting) and will report back here shortly.

[Note: I work on a laptop that's networked part of the time and a standalone most of it. So you may wonder why the scare about a Win logonite accessing my /home/[user]/ directory without regards for permission set under Lx.... It's because I'm learning Lx under the constraint of wanting to put it in production in a very mixed networked environment. I must prepare for that and for sharing volumes that are cross platform encrypted (at client level at least). If it were for me I would have wiped the whole shenanigan clean to start with. There would be no more XP hogging precious real estate on my drive ... and right now I would be in a sunny place with white sand, a board and in the near background the noise of breaking waves.. in a hurry, dude.]

---

### Post by sudodus on 2014-05-10
If you connect to an ext file system via the network (not internally in the computer), there is no problem (and no need of Ext2Fsd). It would make no difference if you use ext2, ext3 or ext4 (I suggest ext4 because it is the most advanced system and very well debugged by now).

- Normally other people would connect from other computers (and not running Windows XP in your computer). Then you should install services like ssh or samba (and make your computer into a server in the local area network). If you want to connect to the internet, you must be aware of the security risks. I am no expert, but there are several people at the Ubuntu Forums who know a lot about servers. If you wish, I can move this thread to the forum about servers

[Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339")             

- Windows XP has passed end of life and should not be used when the computer is connected to the internet, because it will not receive any more security updates.

---

### Post by Cbhihe on 2014-05-11
@sudodus
Thanks a bunch both for the pointers about samba and ssh and the offer to transfer the post to the server forum.
Samba and the rest are definitely on my plate (I bought a printed primer to Samba .. to read on the beach ... about 6 months ago), but I will get to that later.

Here is what I observe:
My new Ubuntu v14.04 config for my internal drive is:

Window system     -- /dev/sda1 - NTFS 53 GB
Boot sector          -- /dev/sda2 - Ext3   0.5GB
swap -- /dev/sda3    7.8GB
Extended partition -- /dev/sda4 - Ext3
/                        -- /dev/sda5 - Ext3  19GB
/home (also D:\)   -- /dev/sda6 - Ext3  99 GB
/var                    -- /dev/sda7 - Ex3   11 GB

and although I still have high CPU usage during a rather brutal disk read-write stress test, xp has chirped on for the last 9 hours, with:
 - only 3 delay-write failures (all associated with Firefox's profiles.ini file being on an Ext3 partition.)
 - 1 cold reboot because I caused something funny to occur to Windows Explorer during one of the tests. 
 - slightly larger response times on the part of Moz-Fx.
 - swap journaling between 12 and 17% (it went up steadily with each passing hour and finished at 17%)
   ( prior to that, I disabled my disk caching from the MS syst admin console ) 
 
My home made stress test consists in copying back and forth, simultaneously or not, 32GB of data of all types, 
-- first between the internal NTFS C:\ partition and the internal Ext3 /home,
-- secondly between an external FAT32 and the same Ext3 /home partition.

I am reasonably satisfied, not by the transfer rates I saw, but by how stable Win OS seems to be under the circumstances.
In any case it is much better than when my extended partition was Ext4 and the logical partitions inside it Ext3.

One thing surprises me though... 
- Why does 32GB o data on FAT32 actually occupies 32 on NTFS but ***36+GB*** in Ext3 ? 
***- Has anybody experience with that sort of "overhead" ?***

---

### Post by sudodus on 2014-05-11
Journaling is used by ext3 and ext4 as well as by NTFS, and it needs some space (proportional to the drive space). FAT32 and ext2 have no journaling.

---

### Post by sudodus on 2014-05-12
Moved from 'Absolute Beginners' to 'Server Platforms'

---

