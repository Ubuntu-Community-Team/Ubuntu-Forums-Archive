---
title: "Best File System for High Traffic SMTP/POP server"
date: 2007-03-31
forum: Server Platforms
---

### Post by ryujin_ssdt on 2007-03-31
I would like to benchmark what is the best file system (XFS, EXT3/4, ReiserFS) to use for a high traffic Postfix/Courier server. I had a QMail server with Maildir storage format on a EXT3 partition with plenty of space. Unfortunately the partition ran out of inodes and the server started to fail delivering emails even thought I had plenty of free space and Qmail sometimes took hours to deliver an email.

Apart of the inode problem and qmail long queues I would also like to know which File System has better read/write performance when managing large amounts of emails (i.e. fast read/write of small files) and which one is more scalable (i.e. can grow to large amounts of space to handle thousands of users).

What software/tests shall I use to benchmark file systems and see which one is more better for my setup (i.e. Postfix-SMTP/Courier-POP + lots of emails per sec). The ability to scale is a must as my users will be allowed to create unlimited folders and keep all emails on the server forever. 

Any advice is appreciated..
Ryujin

---

### Post by kidders on 2007-04-01
Hi there and welcome,

Unfortunately, as far as I know, the answers to the performance and scalability questions *may* be different. :-( ReiserFS claims to handle small files exceptionally well, and (if they're _very_ small) it can be very efficient in terms of disk space consumption. On the other hand, XFS is supposed to be an industrial-strength, highly scalable filesystem, with astronomical upper limits in terms of file counts, sizes, and so on. The other thing to note about XFS is that it's (comparatively speaking) very RAM-hungry. Depending on your point of view, that could be very good, or very bad. Hehe.

There are lots and lots of benchmarks out there that compare these (and often some others, like JFS, for instance) against Ext2/3. I don't recall ever coming across one specifically relevant to your situation though, so be careful whose numbers you believe.

When it comes to actually using them, the two major things to note about ReiserFS and XFS is (a) that their approach to filesystem integrity protection is quite different, and (b) that running them over RAID (which I presume you will be doing) requires careful consideration, to avoid taking a performance hit.

Just to get an initial idea of how the various mainstream filesystem choices compare, it's worth taking a look at a comparison of their design limitations ... workable block sizes, max file counts, RAID-friendliness, max partition sizes, etc. (Wikipedia should be able to help you with that kind of cursory comparison.) *Then* worry about the benchmarks.

Incidentally, I can't help wondering whether (on a filesystem as wildly busy as yours) fragmentation will become a performance killer after a while. Do you suppose fragmentation resistance should be a criterion in your choice of filesystem?

---

### Post by ryujin_ssdt on 2007-04-01
Thanks for your reply,

I have seen several such file systems bechmarks but they simply test specific characteristics of the file system itself and no consideration is given to the application on top.

How can I do my own benchmarks?? simply install a postfix server over one of the file systems and send it lots of emails with a benchmarking software (i.e. postal) and see how much traffic it can handle, then repeat with next file system?

I haven't found yet such a benchmark which I find strange as the selection of the file system greatly depend on the application it will be used for isn't it?

So far from what I have read XFS is the way to go....  but I would like to hear about experiences using XFS for a mail server.  As I said in my previous post EXT3 failed me and my boss had an excuse to migrate  our server to Windows and sadly enough  NTFS has no problems at all handling our traffic. I want to prove that linux can handle it too.

thanks

---

### Post by kidders on 2007-04-01
Hey again,

If you had the time (and the inclination), you could do something like this:

[LIST]
[*]Create a basic Postfix configuration, and and expose its mailboxes over IMAP.
[*]Bombard the SMTP server with a large volume of messages from several sources.
[*]At the same time, log in and out continuously over IMAP.
[/LIST]

You'd be interested in things like:
[LIST]
[*]Average CPU usage, and average CPU waiting time.
[*]Processing delays, as reported in the Postfix logs.
[*]The number of times per second you can complete a login & one basic operation over IMAP.
[*]Delivery queue lengths.
[/LIST]

If it were me, I would leave the test running for a while before taking any measurements. Also, since this is a filesystem test, you might like to spend some time writing out a few tens of thousands of junk files first, just so you're not starting the test with a clean slate. Also, I would avoid using RAID during the test if possible, unless of course you are familiar with filesystem performance optimisation over RAID, and know how to squeeze the best performance out of each one.

Sending large message volumes, or performing basic IMAP operations over and over can be done via telnet, with simple bash scripts. If you wanted to, you could try to encourage filesystem fragmentation by using message deletions as the IMAP operations you perform. Some simple regular expression pattern matching on your postfix logs would give you a good idea of average/peak delivery times, and so on.


I agree that XFS is probably the way to go ... and don't worry ... anything Windows can handle, Linux can hehe. :-P

---

### Post by Brazen on 2007-04-01
> **ryujin_ssdt said:**
> Thanks for your reply,

I have seen several such file systems bechmarks but they simply test specific characteristics of the file system itself and no consideration is given to the application on top.

How can I do my own benchmarks?? simply install a postfix server over one of the file systems and send it lots of emails with a benchmarking software (i.e. postal) and see how much traffic it can handle, then repeat with next file system?

I haven't found yet such a benchmark which I find strange as the selection of the file system greatly depend on the application it will be used for isn't it?

So far from what I have read XFS is the way to go....  but I would like to hear about experiences using XFS for a mail server.  As I said in my previous post EXT3 failed me and my boss had an excuse to migrate  our server to Windows and sadly enough  NTFS has no problems at all handling our traffic. I want to prove that linux can handle it too.

thanks

The maximum number of inodes can be set on an ext3 partition at creation time.  I'm not sure what the default is, but it can be set much higher than what ntfs can handle.

Anyway, I prefer XFS and use it wherever I can.  It is one of the best performing journaled file systems and it's maximums on everything is multiples of what ntfs or ext3 can do.  It is also the oldest of the journaled file systems and very mature and stable.

You may be able to get a little better performance out of some of the other file systems, but XFS is very dependable.  I would especially stay away from ReiserFS; it has a notorious tendency to eat your data.

---

### Post by kidders on 2007-04-01
> **Brazen said:**
> I would especially stay away from ReiserFS; it has a notorious tendency to eat your data.Yeah, whether it's described as "stable" seems to depend on who you talk to hehe.

---

### Post by ryujin_ssdt on 2007-04-02
Well after reading more, and I mean a lot more I got a conclusion.... the winner is XFS.

**Problem Review**

My mail server failed me when my maildir's ext3 partition ran out of inodes. This caused me a lot of trouble as frustrated clients complained to my boss and this finally lead to a migration to Windows 2003 server.

Now I need to install a new server (Postfix) again using Maildirs for storage and I wanted to know what File System is best suited for this task in order to make it scalable.

After a lot of research (googling) I concluded that the best option is XFS.

**Why XFS?**

- Journaled file system perfect to avoid fsck on boot that is bad for a server. Especially for one with large disks.
- Very mature and with lots of features that may be useful in the future like
  extended attributes and per file access control lists.
- Support for online defragmentation that allows to check/defrag the partition
  without unmounting it. This is desirable on a 24/day 365/day server.
- Nice backup utitlities (xfsdump et. al.) that again are very necessary for a server
  environment. They also support the extended attributes of inodes.
- Support for massively large files and partitions that allow for very scalable   
  systems. Especially nice for databases and file servers.
- Very fast read/write performance (sequential and random) when compared to other 
  file systems especially for very large file sizes. Only slow when deleting large i   
  number of small files.
- Dynamic inode allocation allowing for large number of files/directories limited only 
  by the actual disk space and not a pre allocated inode space.
- Support for quotas that is a must in a multi-user environment (again think servers).

**But XFS is very slow deleting large amounts of small files!!. **

Well I haven't found yet a situation were I needed to actually delete a lot of small files from a mail server. Also after reading this [post]("http://everything2.com/index.pl?node_id=1479435") it seems that it is possible to tweak XFS to perform better than ext3 when deleting files.

**But XFS only logs meta data on the journal so you will loose data on a crash**

Well the only File System that is known to be robust to system crashes and power outages is ext3 in journaling or ordered mode. All other file systems log only meta data that is faster. Also if you are setting a server you also have disaster recovery plans don't you?? like a nice backup plan and more than one independent power source.

**But reiserFS handles better small files like those of a maildir boxes.**

Maybe but the benckmarks show that XFS is not that far behind and still it can handle large file efficiently. Reiser is the worst performer when handling large files. Having a balance (something in between) is better than optimizing only to one extreme. 

**But what about JFS?? I heard it performs better than XFS with less CPU load and is more robust!!**

Yes I heard it too and some benchmarks show that JFS can be as good or better than XFS in read/write performance. JFS is relative new (in the linux camp) and  is not as mature nor has as many features as XFS. For example it does not support quotas or access control lists.

**So XFS is cool so I will install it on all my linux systems**

Hold your horses there... I said this was for a SMTP (Postfix) server deployment. I would not recomend using XFS or any metadata only journaling file system on a desktop computer, specially on a laptop that has more probability of power outages. The amount of complaints about  all KDE configuration files being zero-length or filled with zeros after a crash talk by themselves. XFS is not robust to crashes and power outages as ext3 is so I will stick with ext3 for my desktop installations and my laptop. 

Ext3 is the recomended default for most distros and with some tweaks it is possible to improve it's performance further (see [here]("http://www.suseforums.net/index.php?showtopic=29773") and [here]("http://forums.gentoo.org/viewtopic-t-488215.html")).


**Resources**

[http://bulma.net/impresion.phtml?nIdNoticia=1154]("http://bulma.net/impresion.phtml?nIdNoticia=1154")
[http://linuxgazette.net/122/piszcz.html]("http://linuxgazette.net/122/piszcz.html")
[http://www.debian-administration.org/articles/388]("http://www.debian-administration.org/articles/388")
[http://linux.inet.hr/first_benchmarks_of_the_ext4_file_system.html]("http://linux.inet.hr/first_benchmarks_of_the_ext4_file_system.html")
[http://www-128.ibm.com/developerworks/library/l-jfs.html]("http://www-128.ibm.com/developerworks/library/l-jfs.html")
[http://everything2.com/index.pl?node_id=1479435]("http://everything2.com/index.pl?node_id=1479435")
[http://www-128.ibm.com/developerworks/linux/library/l-fs8.html]("http://www-128.ibm.com/developerworks/linux/library/l-fs8.html")

---

### Post by ryujin_ssdt on 2007-04-03
> **kidders said:**
> Hey again,

If you had the time (and the inclination), you could do something like this:

[LIST]
[*]Create a basic Postfix configuration, and and expose its mailboxes over IMAP.
[*]Bombard the SMTP server with a large volume of messages from several sources.
[*]At the same time, log in and out continuously over IMAP.
[/LIST]

You'd be interested in things like:
[LIST]
[*]Average CPU usage, and average CPU waiting time.
[*]Processing delays, as reported in the Postfix logs.
[*]The number of times per second you can complete a login & one basic operation over IMAP.
[*]Delivery queue lengths.
[/LIST]

If it were me, I would leave the test running for a while before taking any measurements. Also, since this is a filesystem test, you might like to spend some time writing out a few tens of thousands of junk files first, just so you're not starting the test with a clean slate. Also, I would avoid using RAID during the test if possible, unless of course you are familiar with filesystem performance optimisation over RAID, and know how to squeeze the best performance out of each one.

Sending large message volumes, or performing basic IMAP operations over and over can be done via telnet, with simple bash scripts. If you wanted to, you could try to encourage filesystem fragmentation by using message deletions as the IMAP operations you perform. Some simple regular expression pattern matching on your postfix logs would give you a good idea of average/peak delivery times, and so on.


I agree that XFS is probably the way to go ... and don't worry ... anything Windows can handle, Linux can hehe. :-P

Ok I already got a clean Ubuntu Server (6.06 LTS) installation on a machine and I left 50GB free partition for testing. Now how should I proceed to install Postfix in a way that all the postfix files like configuration, maildirs, logfiles go on that partition.

Shall I chroot postfix to that directory?? if so are there any tutorials around on how to do that?

---

### Post by Brazen on 2007-04-03
> **ryujin_ssdt said:**
> Ok I already got a clean Ubuntu Server (6.06 LTS) installation on a machine and I left 50GB free partition for testing. Now how should I proceed to install Postfix in a way that all the postfix files like configuration, maildirs, logfiles go on that partition.

Shall I chroot postfix to that directory?? if so are there any tutorials around on how to do that?

you'll need to find out where all those directories are located and then symlink to where you have the partition mounted.  maildirs is possibly /var/lib/postfix; logfiles would be /var/log/postfix; and configuration would be /etc/postfix.

---

### Post by Rashkae on 2007-04-04
> **ryujin_ssdt said:**
> 

**But XFS only logs meta data on the journal so you will loose data on a crash**

Well the only File System that is known to be robust to system crashes and power outages is ext3 in journaling or ordered mode. All other file systems log only meta data that is faster. Also if you are setting a server you also have disaster recovery plans don't you?? like a nice backup plan and more than one independent power source. 

With XFS, it's a little more complicated.   XFS is the only journaled filesystem on linux, to my knowledge, that by default doesn't write data/meta data in an ordered mode.  (ReiserFS used to be like this, but they changed it to ordered in 2.6 series kernel).  This has the consequence of silently currupting your data by inserting NULLs in files where the meta data was updated but the data never flushed to disk.  As you say, however, on a server with a good power backup, this should be exceedingly rare.

> 
**But reiserFS handles better small files like those of a maildir boxes.**

Maybe but the benckmarks show that XFS is not that far behind and still it can handle large file efficiently. Reiser is the worst performer when handling large files. Having a balance (something in between) is better than optimizing only to one extreme. 


I don't know why people keep saying Reiser has good performance with lots of small files.  If you have a maidir folder with thousands of messages, trying to read that directory sequentially on a Reiser filesystem is painfully slow (you'll barely get more than 1MB throughput).  This is because the Reisuer BTree hashing algorithing is incapable, in a readdir operation, to read the files in the  order they were written to disk, so the hard drive head is seeking all over the place.  The only performance boost I've ever seen with Reiser and small files is the peerless lightning speed with which it deletes them

> 
**But what about JFS?? I heard it performs better than XFS with less CPU load and is more robust!!**

Yes I heard it too and some benchmarks show that JFS can be as good or better than XFS in read/write performance. JFS is relative new (in the linux camp) and  is not as mature nor has as many features as XFS. For example it does not support quotas or access control lists.


I'll have a pound of whatever your smoking mate.  Not only does JFS support ACL's, it can support hundreds (or was that thousands?) of ACL entries per file, wheras XFS and EXT3 are limited to just over 20.  I'm fairly certain quota support is in there as well.  JFS has had, to my knowlege, far fewer stability issues than XFS.  I'm honestly surprised it is not used more often.  And from my own testing, JFS handles maildir folders with 10000+ messages just fine, with similar perforance to XFS and Reiser4, without the headaches of those filesystems.  I don't disagree with your choice of XFS, but I think you're overlooking JFS unfairly.  It's also worth noting that JFS is actively supported by IBM, and is their filesystem of choice for their mainframe linux deployment.

---

### Post by ryujin_ssdt on 2007-04-04
Dear Rashkae 

Thanks for your comments. 

You are right I was unfair with JFS. This is mostly because it was the last file system I researched about and touched only the surface of what JFS really is. I simply read and repeated what others have said about it.

I am currently doing some benchmarks and they are looking good for XFS and JFS. To give you a little idea with Postfix installed on Ext3 or ReiserFS I get about 500~600 mails per minute and when using JFS or XFS I can get over 1100 mails per minute.

About the quota support in JFS it seems that it is not supported with the kernel version used by Ubuntu Server (2.6.15-28-server #1 SMP). If you read the man page for mount you will see in the JFS section:

[INDENT]     noquota / quota / usrquota / grpquota
              These options are accepted but ignored.
[/INDENT]

Reading some forums it seems there are problems with quota support on kernel versions 2.6.14 up to 2.6.17. See here for details : [http://www.mail-archive.com/jfs-discussion@lists.sourceforge.net/msg00634.html]("http://www.mail-archive.com/jfs-discussion@lists.sourceforge.net/msg00634.html")


Now I would like to ask what are the best options (at creation time and mount time) to use for JFS? Reading the mkfs.jfs help and the mount manual it seems JFS has little options to tweak. So far I only increase the journal log size and mount it with the noatime option. Are there any other tweaks to improve JFS??

---

### Post by ryujin_ssdt on 2007-04-06
I finished my benchmark tests and you can read about my results on my blog:

[http://piao-tech.blogspot.com/2007/04/file-system-benchmarks-for-postfix-mail.html](http://piao-tech.blogspot.com/2007/04/file-system-benchmarks-for-postfix-mail.html)

Any comments or tips on how to increase performance or to improve my test methodology are appreciated.

---

### Post by kidders on 2007-04-06
That blog entry is fascinating. It is worth pointing out though, that your results are probably skewed by issues other than your filesystem choices ... so, while the benchmarks are true to reality for you (which is what's important), they may not be reliable indicators for everyone.

For instance, XFS's & JFS's particularly poor performance over SMTP is curious. Since actual mail deletions are presumably performed asynchronously, I wouldn't have expected the wild performance differences you observed.

There is also some scope for quibbling over the specific filesystem optimisation parameters you chose at the outset.

Having said all that, there is no question that you've done some pretty fabulous work, and that is serves as an immensely useful "be-careful-or-this-might-happen-to-you" warning for certain configurations. It would be interesting to find out what effect the introduction of RAID would have on the benchmarks though (since most mail servers are unlikely to run without it). RAID often opens up some bottlenecks, while creating others, so I'm curious about which filesystems would switch places in your rankings.

In your blog, you mention some confusion over "%wa" CPU usage figures. The way you describe them is essentially correct. Although it's difficult to tell (since the wildly different SMTP & POP results are merged for CPU performance analysis purposes), it looks as though JFS I/O operations were taking an inordinately long time to complete.

As a user, at one time or another, of all of the tested filesystems, I'll certainly be mulling over your results for a while yet. I wonder what everyone else thinks.

---

### Post by ryujin_ssdt on 2007-04-06
Thanks for the comments, they give me motivation to keep trying things out. If I get some RAID hardware I will surely test again.

regards,

---

### Post by Rashkae on 2007-04-06
Wow, great work, thanks.  I just wanted to add a couple footnotes of my own observations.

EXT3 has serious, fatal and disastrous problems once a single directory gets large enough... If you have IMAP users who don't delete messages, it wont' be long before you have a direcotory with over 10,000 files and EXT3 just dies.  (To be more precise, trying to add or rename files in the directory will max out CPU and decrease performance of the whole system).  You can alleviate that by formatting  EXT3 with BTree directories, but then you'll run into performance issues similar to ReiserFS doing things like backups.

I know your testing is done, and your not likely to revisit it, but would have been nice if JFS had been tested with noatime and nodirtime like all the others.  These simple parameters can make a *big* difference on journaled filesystems, since all those metadata updates are.. well, journaled.

And lastly, just a note that hard drive throughput can vary by as much as 100% depending on what part of the disk is being read/written too.  For that reason, I consider it important when doing hard drive benchmarks to narrow the partition to something no bigger than 1.5x the space you will be using.  Otherwise, the results can vary greatly depending on how the FS allocates space. (A FS that writes as close to the start of the partition as possible might show a considerble performance benefit to one that tries to space out writes across the partition.) but this perforamnce 'edge' on a benchmark will not offer lasting benefits in a production environment.

---

