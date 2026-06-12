---
title: "Server partitioning scheme"
date: 2010-04-30
forum: Server Platforms
---

### Post by Tommetje on 2010-04-30
Hey all

I've already seen a lot of posts on this subject but I never find an answer. So let's try this again because I know many people want answers on this subject.

_**RAID Configurations**_

First things first: RAID configuration. I know none is best and it all depends on what you want to use it for, but I seem to have found the general rules here:

- RAID0: for everything OS related. On Windows servers, this is quite simple, just install the OS on a RAID0 device. On Linux, I'm not so sure, which folders are considered the "OS"? Assuming we create partitions for the following folders: **/ **(root), **/boot**, **/usr**, **/home**, and **/var**, only the **/** (root), and **/usr** are "OS"?

- RAID5: for all data which gets written to a lot, meaning **/home** and **/var**.

- RAID10: According to the **MySQL Administrator's Bible** from Wiley, RAID10 is by far the best for you MySQL databases. I'm guessing RAID5 is the second best (only guessing here?)

_**Filesystems**_

I mostly read the differences in file systems don't really matter much, as long as you don't pick ext2, that is. In **Pro Ubuntu Server Administration** by Apress, I find the following table on page 7:
[FONT=Courier New]
/boot   100MB   ext2      primary   RAID1
/       20GB    ext3      LVM       RAID1
/var    5GB     XFS       LVM       RAID1
/tmp    1GB     ReiserFS  LVM       RAID1
/srv    50GB    XFS       LVM       RAID5
/home   50GB    XFS       LVM       RAID5

[/FONT]So, what do we notice here? First of all, the author clearly does make a difference between all the different file systems which pops up the question "who do we need to believe"? Furthermore, do we use **/srv** or **/usr** for installing the services our server provides?

_**Fstab Configuration**_

[This post]("http://ubuntuforums.org/showthread.php?t=1102204") raises an issue with the fstab configuration scheme suggested somewhere. No one ever responded to it though. I'm hoping some one will provide me with some inside on this?

_**Questions**_

So, what do I want to know?

[LIST=1]
[*]Which folders should get a seperate partition, based on server roles.
[*]Which folders can best be put on which RAID-configuration? I think I've got it about right in this post, but I would like some confirmation or corrections if I'm wrong somewhere.
[*]Filesystems: don't bother? Maybe ReiserFS for **/var** on a mailserver because of the many small files? When using bigger files, better take XFS than ext3?
[*]Any thoughts on best fstab configuration options for mounting the partitions (see linked thread without response).
[/LIST]
-Tom

---

### Post by windependence on 2010-04-30
You're asking a lot here, especially about things with so many variables.

Let me address what I know for sure without variables.

Putting your OS on a RAID 0 volume is SUICIDE. You take two or more drives and stripe them for speed only with RAID 0. There is NO fault tolerance in RAID 0, so if ANY of your drives fail, you are down hard. Most enterprises that I have worked for (IBM, Mattel) use RAID 1 for the OS and RAID 5 for the data if the server is not going to be connected to a SAN or virtualized.

-Tim

---

### Post by Tommetje on 2010-04-30
Thanks for confirming some of the things I already thought/knew. Which directories of Linux do you consider OS and which ones do you consider data? (directories like /usr, /var, /boot, /etc, /srv, ...).

- Tom

---

### Post by isaacjgs on 2010-05-17
I'm glad someone addressed the TYPE of file system formats to go with when mounting to different directories under /. However, I'd like to decide between ext2, ext3 and ext4 only due to their reliability. I know that when I looked in Mike Sobell's "Practical Guide to Ubuntu Linux (8.04 and 8.10)" that ext2 was best for the /boot and /usr partitions. However, he didn't make a specific recommendation for the other ones, like for /, /home, /opt, /tmp, and /var. I looked in the 10.04 installation guide, and I looked here: 

[https://help.ubuntu.com/10.04/installation-guide/i386/directory-tree.html](https://help.ubuntu.com/10.04/installation-guide/i386/directory-tree.html)

It does give guidelines as to the amounts of space needed for each of those partitions.

Then I looked here:

[https://help.ubuntu.com/10.04/installation-guide/i386/apcs03.html](https://help.ubuntu.com/10.04/installation-guide/i386/apcs03.html)

Now I am experiencing conflict. In Mark Sobell's book (p.37-39), he did say that ext2 was better used for the /boot and for the /usr partitions because their contents don't change much to justify an ext3 overhead. This implies that a directory like /var changes a lot and needs an ext3 partition (though he didn't explicitly say this).

But at the same time, I look here, [https://help.ubuntu.com/10.04/installation-guide/i386/apcs03.html](https://help.ubuntu.com/10.04/installation-guide/i386/apcs03.html) , and it says that if a partition is above 6 GB it should be ext3 because if it's set to ext2, file system checks can get lengthy.

But here, [https://help.ubuntu.com/10.04/installation-guide/i386/directory-tree.html](https://help.ubuntu.com/10.04/installation-guide/i386/directory-tree.html) , it says that /var should only be 2-3 GB.

Now, should I set /var to ext2 since the size is less than 6 GB, or should I set /var to ext3 because the data changes a lot? There was also another forum I read (I can't remember the address), that said that if you used a journaling file system for /var, that even if the logs inside of /var/logs were deleted, the journal would still have a copy of, say, password or password files, and that it would be more risky for a server environment.

Also for /usr, which I plan to make larger than 6 GB, should I set it to ext2 because the contents of it don't change much, or ext3 since the partition is larger than 6 GB?

I'd like to also know what ext-only file systems would be best for the rest of the other directories (/home, /opt, tmp, etc.)

By the way, I'm setting up a server (p2 400 mmx). I plan to set up all other directories (except for /home) on a single IDE 40 GB hard drive, with /home set up on a software RAID 1 pair of SATA 500 GB hard drives for use as file sharing. The SATA drives' cables are hooked up to a SATA II card. Thanks for any replies.

Currently on paper, my scheme is this:

/boot = 100 MB ext2
/ = 3 GB ext2
(swap) = 3 GB
/home = ext3 or ext4 (depending on which is better, though I might try ext4)
/opt = 4 GB ext2
/tmp = 3 GB (ext2 or ext3? Maybe ext2 since it is less than 6 GB)
/usr = Will take up the rest of the space on the IDE hard drive (ext2 or ext3? Maybe ext3, since it is larger than 6 GB)
/usr/local = 4 GB ext2
/var = 3 GB (ext2 or ext3? This is the one I have the most trouble deciding. If less than 6 GB, than ext2 is what I'm thinking but then again the data changes a lot, so maybe ext3)
/var/log = 1 GB ext2

---

### Post by Tommetje on 2010-05-17
First of all, why do you only want to use ext file systems? What's wrong with XFS or ReiserFS? (I can guess why you don't want to use Reiser, but XFS?)
 
Furthermore, why use 3GB for your root partition if you create different partitions for almost all folders that store data (/var, /usr and /home).
 
It's interesting that it says above 6GB definetaly ext3, thus below 6GB you can use ext2. I would personally always go for ext3 except for the /boot partiition but it might be good thinking about using ext2 on other partitions too.
 
For ext4, I've read somewhere that it's best not used yet for servers since it's too new of a filesystem, which sounds logical to me.
 
So once again, your interesting post just gave us more questions than answers.
 
PS: using no RAID for the OS and RAID1 for data? Are you lacking sufficient HDDs or are you on a budget? I thought it was best putting your OS (static) on RAID1 (fast readable) and putting your data (variable) on RAID5 (better write).

---

### Post by isaacjgs on 2010-05-17
Dear Tom,
 
Thank you very much for your timely response. Indeed, I am following this post and I am doing research. From what I read, ext2 is still a very trusty filesystem (as said here: [http://linux.derkeiler.com/Mailing-Lists/Debian/2008-01/msg01808.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-01/msg01808.html)), indeed best used for hard drives 6 GB and less. Any hard drive greater than 6 GB means that the filesystem checks on ext2 take more time than the same with ext3.
 
You were wondering why I chose to stay away from XFS and Reiser. Well, during the Ubuntu Installs about a year or so ago, maybe a little more, I found that the install program said that I should only choose ReiserFS or XFS only if I know what I am doing. Reports from other people here [http://lwn.net/Articles/181343/](http://lwn.net/Articles/181343/) who tried these file systems said that I could end up with file corruption if I chose XFS or Reiser. Ext2 and ext3 have received very extensive testing, especially ext3. 
 
Now I have a couple of questions for you: Would it be better to have ext2 for /usr since the file contents don't change much, or have it set to /ext3, since the partition for that directory is greater than 6 GB?
 
Also, would it be better to use ext2 on /var, since it is less than 6 GB, or ext3, since the file contents of the directory change very often?
 
By the way, I still haven't found the website that said that ext3 being used on /var, if password files and stuff were deleted, that the journal may still have them, and can pose a security risk to servers. I think it was an ArchLinux Forum, but I'm not sure. Wish I bookmarked it. I'll be hunting for it too.
 
I now have chosen ext3 for the data pair.
 
By the way, you mentioned XFS for large files and ReiserFS for small ones. ext2 would work perfectly for both, but then again, maybe I'm just inexperienced.
 
~Isaac~
 
P.S. As for your question about giving / 3 GBs, it was because there was a time when I only gave it 1 GB. The installer refused to install, and so I had to use GParted all over again. I gave it 2 GBs, and it didn't complain. I probably could settle for 2 GB for /, but I am merely just trying to overestimate the space needed for the partition, although 3 GB for / is most likely overkill.
 
As for RAIDing the 500 GB SATA pair for /home only and using only one hard drive for the OS, yes I am somewhat on a budget, and it's a simpler setup for me. Not that I'm not willing to try RAIDing the OS drive itself, but it's just a more simple setup for me. All I'm concerned is the data, and less so the operating system. If the operating system goes bad, no worries. I just reinstall. However, if one of the data disks goes bad, all I need to do is swap one of them out. I don't have any experience replacing a single data hard disk that goes bad, when /home is that mount point of the single data disk. Maybe you can teach me something about it.
 
By the way, I am highly interested in finding out the differences between all the different file systems, side-by-side.

---

### Post by wkulecz on 2010-05-20
My opinion.

Hard drives are cheap. Other than a swap partition somewhere, one partition per drive is less pain in the long run.  Automatically backing up (from a cron daily job) to duplicated drives (or larger drives so two+ can go to one for backup) with rsync has saved my butt on more than one occasion.

XFS and raid5 don't go together well unless things have changed greatly since 6.06 -- I lost all data on an XFS raid5 when one of the drives dropped out from a loose power cable :(  I rebuilt it, reformatted ext3 and restored from my Rsync backup.  Haven't noticed  any performance issues going from XFs to ext3, but I'd hesitate to generalize my specific experience with what in effect is a "media server".

I've since given up on raid altogether, but say three 1 GB drives in a raid5 or two 1GB in a raid1 array automatically rsynced to a 2GB drive is what I'd do if my file server was a lot more dynamic.  Unfortunately you hit a point where if its dynamic enough you can never have a 100% backup, I'd go with raid1 and as much backup to a third drive as I could schedule in this case.

---

### Post by isaacjgs on 2010-06-14
Wow, read this: [http://blog.2ndquadrant.com/en/2010/04/the-return-of-xfs-on-linux.html](http://blog.2ndquadrant.com/en/2010/04/the-return-of-xfs-on-linux.html)

Gives the latest news on XFS.

---

### Post by isaacjgs on 2010-09-07
> **Tommetje said:**
> 
_**Filesystems**_
 
I mostly read the differences in file systems don't really matter much, as long as you don't pick ext2, that is. In **Pro Ubuntu Server Administration** by Apress, I find the following table on page 7:
 
[FONT=Courier New]/boot 100MB ext2 primary RAID1[/FONT]
[FONT=Courier New]/ 20GB ext3 LVM RAID1[/FONT]
[FONT=Courier New]/var 5GB XFS LVM RAID1[/FONT]
[FONT=Courier New]/tmp 1GB ReiserFS LVM RAID1[/FONT]
[FONT=Courier New]/srv 50GB XFS LVM RAID5[/FONT]
[FONT=Courier New]/home 50GB XFS LVM RAID5[/FONT]
 
So, what do we notice here? First of all, the author clearly does make a difference between all the different file systems which pops up the question "who do we need to believe"? Furthermore, do we use **/srv** or **/usr** for installing the services our server provides?
 
_**Fstab Configuration**_
 
[This post]("http://ubuntuforums.org/showthread.php?t=1102204") raises an issue with the fstab configuration scheme suggested somewhere. No one ever responded to it though. I'm hoping some one will provide me with some inside on this?
 
_**Questions**_
 
So, what do I want to know?

[LIST=1]
[*]Which folders should get a seperate partition, based on server roles.
[*]Which folders can best be put on which RAID-configuration? I think I've got it about right in this post, but I would like some confirmation or corrections if I'm wrong somewhere.
[*]Filesystems: don't bother? Maybe ReiserFS for **/var** on a mailserver because of the many small files? When using bigger files, better take XFS than ext3?
[*]Any thoughts on best fstab configuration options for mounting the partitions (see linked thread without response).
[/LIST]-Tom
 
Actually, in depends on what you have set up the server to do, for what /var will be used for. An XFS partition theoretically would be best for /var if the server is not set up to be a mail server. (This will cause all its subdirectories to be in the XFS filesystem for /var.) But if you set it up to be a mail server, make for /var an XFS partition, and for the sub-folder, /var/mail, make a ReiserFS partition for that sub-folder. (I read here [https://help.ubuntu.com/10.04/installation-guide/i386/apcs03.html](https://help.ubuntu.com/10.04/installation-guide/i386/apcs03.html) that if the server is a mail server, it would be a good idea to make a separate partition for /var/mail.)
 
So basically, if the server is not a mail server, use XFS for all of /var (and its subdirectories will end up on the same partition). But if the server will also be used as a mail server, make for /var an XFS partition, but with /var/mail being the exception here---therefore, make for /var/mail a ReiserFS partition. That way, all folders under /var will be in the XFS partition, except for /var/mail, which will be on the ReiserFS partition.
 
~Isaac~

---

