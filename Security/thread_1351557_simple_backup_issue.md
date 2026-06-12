---
title: "simple backup issue"
date: 2009-12-10
forum: Security
---

### Post by onthenarrowpath on 2009-12-10
Well maybe I'm just running into open doors, but after my experience, simple backup has a severe drawback: It tries to create .tgz-files larger than 4 giga. This should ring some bells, because they are too large to be handled, which means that any backups you do are completely useless when they overgo a certain size. 

Maybe I just got something completely wrong, but if not, people should know about that. And if I did, I would like to know about it ;-)

---

### Post by Bucky Ball on 2009-12-10
Too large to be handled if you are trying to save onto a FAT32 partition. Is that the case? If so, try an NTFS or EXT partition.

---

### Post by onthenarrowpath on 2009-12-11
So, you say, I should formate my external Hard drive to NTFS or EXT and then I should be able to deal with .tgzs larger than 4 giga (sorry for the persistence, but this time I want to get it right)?

---

### Post by Cheesemill on 2009-12-11
> **onthenarrowpath said:**
> So, you say, I should formate my external Hard drive to NTFS or EXT and then I should be able to deal with .tgzs larger than 4 giga (sorry for the persistence, but this time I want to get it right)?

Yes :)

---

### Post by cariboo on 2009-12-11
Have a look [here]("http://www.genie-soft.com/asp/community/KnowledgeArticle.asp?KBID=113") for fat32 file system limitations.

---

### Post by onthenarrowpath on 2009-12-14
Thanks a lot for your help, Bucky Ball, Cheesemill and cariboo 907. I guess I know everything now to make my backup worth its name!

---

### Post by RayArdia on 2011-10-05
I've had similar problems. When I read from the .tgz files I get an error indicating that the backed up files are incomplete.
How do I find out what format my Phillips external hard drive is using, and then re-format?
Apologies for dumbo question.
Ray

---

### Post by Bucky Ball on 2011-10-05
> **RayArdia said:**
> 
How do I find out what format my Phillips external hard drive is using, and then re-format?
Ray

Open System>Administration>Gparted and have a look. To reformat, back it up, unmount it by right clicking on the external drive's partition then reformat it.

---

### Post by RayArdia on 2011-10-05
Thanks Bucky Ball, but can't find Gparted under System/Admin. Can you please point me in the right direction?

---

### Post by cariboo on 2011-10-06
> **RayArdia said:**
> Thanks Bucky Ball, but can't find Gparted under System/Admin. Can you please point me in the right direction?

Gparted isn't installed by default, so you'll have to use your favorite method to install it. ANother way to check how your external drive is formatted is to use:

```
sudo fdisk -l
```

in a terminal, the output should look something like this:

```
sudo fdisk -l
[sudo] password for cariboo: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa8aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   256002047   127641600    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00016e1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    20482047    10240000   83  Linux
/dev/sdb2        20482048    24578047     2048000   82  Linux swap / Solaris
/dev/sdb3        24578048   488396799   231909376   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a951a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048    20482047    10240000   83  Linux
/dev/sdc2        20482048    24578047     2048000   82  Linux swap / Solaris
/dev/sdc3        24578048   312580095   144001024   83  Linux
```

In my case /dev/sdc is an external drive, that is formatted as an EXT file system

---

### Post by RayArdia on 2011-10-07
Many thanks Bucky Ball, I think I now have a backup in progress in background! We'll see!
Ray

---

### Post by RayArdia on 2011-10-07
Thank you. Now have disc formatted as a single partition 320GB. Started Simple Backup and get this response:-
 
A backup run is initiated in the background. Process id is: 9498

But nothing seems to be happening - how do I find out what's going on/down?
Ray

---

### Post by Bucky Ball on 2011-10-07
Yea, good question! I would imagine it is doing a backup and all depending how much it's backing up could take hours. I would leave the machine on until it is not indicating a backup in progress.

I have pondered your question in the past ...

---

### Post by RayArdia on 2011-10-07
So there's no way of checking the progress of process 9498?
Ray

---

### Post by RayArdia on 2011-10-07
Backup has clearly happened as there is a file /media/Phillips/2011-10-07_20.17.17.613232.ray-laptop.inc on the drive.
However when I try to read it I am told:-
You do not have the permissions necessary to view the contents of "2011-10-07_20.17.17.613232.ray-laptop.inc".
Why is this, since I created the file by backing it up from my Home directory!
How can I change the ownership of the drive and the files in it?

---

### Post by RayArdia on 2011-10-08
So sorry to have posted the above question - a little reading of Absolute Beginners pointed me towards 'chow' etc.
Have now changed permissions and can access files.
Ray

---

### Post by RayArdia on 2011-10-08
Oose!ops, I meant 'chown', of course!
Ray

---

