---
title: "I finally get the hype about rsync"
date: 2006-07-05
forum: The Cafe
---

### Post by aysiu on 2006-07-05
I've been backing up data for years now.

When I was in Windows, I did it by burning CDs... *lots* of CDs.

Finally, my wife and I invested in an external hard drive--what a life saver. I could back up 30 or 40 GB of data without having to burn 50 CDs. How did I back stuff up? Copy and paste. Sure, it took a long time, but that seemed fine.

Later, after moving on to Ubuntu, I still did the copy and paste for quite a while.

I toyed with a few GUI programs for backing up, but they always seemed convoluted to me, for some reason.

Then, I tried just .tarring my files with a script that I saved to /usr/local/bin and  called *backupfiles*. I liked the script. It was fun, but it still took a hell of a lot of time to copy all those files.

Finally, I read [an article about *rsync*.](http://www.whatpc.co.uk/personal-computer-world/features/2159601/linux-risk?page=2) I'd read numerous times on these forums that *rsync* was great... usually accompanied by vague instructions like > Try rsync

I have to say I *really* despise the acronym RTFM (read the f'in manual)--not so much because of its rudeness but because of its presumptuousness and false assumptions... namely that reading the manual actually helps new users.

I did ```
man rsync
``` and my eyes glazed over. "Yeah... so..? How do I use it?" The article in the news explained it all quite nicely, even to a semi-beginner like me.

So I used *rsync* with the *-av* options: > rsync -av /old/directory /backup/directory and it took quite a while, but when I did it again, only my Firefox profile (which I had modified slightly since) was backed up.

The beauty of *rsync* is its being a single command that does not require root privileges, preserves links, and does differential/incremental backups. I was so won over by *rsync* that I even converted my wife over to it to use on her Mac Powerbook.

One thing that I found out the hard way, though--don't use *rsync* on FAT32. It's got to be Ext3 or HFS+.

---

### Post by Iandefor on 2006-07-05
That actually sounds useful. My only question: it synchronizes changes in directory contents, sure, but what about file contents? Does it check for file consistency as well?

---

### Post by aysiu on 2006-07-05
Well, as I understand it--and obviously there *rsync* experts out there who may know better--it compares modification dates and file names (and possibly file sizes?) and then copies over the file if it's been changed since...

... so, theoretically, if the file contents have been changed, so has the modification date, right?

---

### Post by Iandefor on 2006-07-05
[quote=aysiu]Well, as I understand it--and obviously there *rsync* experts out there who may know better--it compares modification dates and file names (and possibly file sizes?) and then copies over the file if it's been changed since...

... so, theoretically, if the file contents have been changed, so has the modification date, right?[/quote] Yup. I didn't see that if it was in the article.

---

### Post by aysiu on 2006-07-05
No, that may not be in the article, but *rsync* appears to copy files that have been modified, so I'm assuming it goes by modification date, as *grep*-ing the contents of each file and comparing the two would take forever.

---

### Post by prizrak on 2006-07-05
I guess the real question would be, does it check whether the synching was successful.

---

### Post by prizrak on 2006-07-05
[QUOTE=aysiu]No, that may not be in the article, but *rsync* appears to copy files that have been modified, so I'm assuming it goes by modification date, as *grep*-ing the contents of each file and comparing the two would take forever.[/QUOTE]
And not always possible.

---

### Post by aysiu on 2006-07-05
[QUOTE=prizrak]I guess the real question would be, does it check whether the synching was successful.[/QUOTE]
I'm not sure what you mean--whether the files actually copied... or just put empty placeholders?

---

### Post by Iandefor on 2006-07-05
[quote=aysiu]I'm not sure what you mean--whether the files actually copied... or just put empty placeholders?[/quote] I think he means checking if the transfer actually copied the files bit-for-bit successfully. Sort of like how you should check the md5 checksum of iso's you download.

---

### Post by Polygon on 2006-07-05
[QUOTE=Iandefor]That actually sounds useful. My only question: it synchronizes changes in directory contents, sure, but what about file contents? Does it check for file consistency as well?[/QUOTE]

thats what i was thinking as well, like if you have a text file named "thingstodo" and you have like "wash the dishes". then you use rsync and that file gets backed up to some directory. But if you add more to that text file, like "take out the trash", will rsync know that the file was edited and backup and overwrite the previous file that got backed up, or will it not back up the newly edited file at all because it already exists in the backup directory?

otherwise, this looks like a useful program. i will have to check this out.

and why didnt you use dvds before you discovered rsync... you could of backed up a lot more for a lot less that way, but external drives i agree are the best solution :D

---

### Post by kabus on 2006-07-05
I prefer rdiff-backup. 
It can store multiple versions of a file using very little extra space because it only saves changes. 
Here's an article about it :

[http://arstechnica.com/articles/columns/linux/linux-20060202.ars/2](http://arstechnica.com/articles/columns/linux/linux-20060202.ars/2)

---

### Post by caldevil on 2006-07-05
For full system backup I use sbackup developed in last googel summer of code program. For home directory backup I use rdiff-backup automatically scheduled every week. For mp3s backup from fat32 partition I use grsync (gui for rsync) and I do it manually once in a while.

---

### Post by aysiu on 2006-07-05
Thanks for the recommendation, kabus. Maybe in a few months I'll post a thread called > I finally get the hype about rdiff-backup In the meantime, I'm going to enjoy my newfound friend *rsync*.

---

### Post by OffHand on 2006-07-05
grsync worked really well for me. it's the gnome gui for rsync.

btw: I use it to copy files to my FAT32 disk.

---

### Post by aysiu on 2006-07-05
I have *grsync* installed, too, actually, but I don't use it. Does it have a verbose mode? In other words, does it list what files it's copying as it's copying them?

---

### Post by OffHand on 2006-07-05
[QUOTE=aysiu]I have *grsync* installed, too, actually, but I don't use it. Does it have a verbose mode? In other words, does it list what files it's copying as it's copying them?[/QUOTE]
yes it does

---

### Post by pchr on 2006-07-05
I recently discovered this also, for sending my Music and Photo directories to an external USB hard disc.  I'm interested though, what do you mean by
> One thing that I found out the hard way, though--don't use rsync on FAT32. It's got to be Ext3 or HFS+.
I ask because my USB HD is using FAT32 (I want to be able to plug it into windows PCs) and I have noticed that a lot of folders seem to copy over even if I haven't made any changes at all!  In fact I used the Size Only flag to stop the contents of these directories from being copied over, but the name of the folder STILL gets mentioned in verbose mode :confused: 

Having said all that it does get the basic job done :grin: 

I also got Grsync for a graphical front end, which works ok.

EDIT : Geez, that's been mentioned 4 posts ago while I was writing this!

---

### Post by prizrak on 2006-07-05
[QUOTE=pchr]I recently discovered this also, for sending my Music and Photo directories to an external USB hard disc.  I'm interested though, what do you mean by

I ask because my USB HD is using FAT32 (I want to be able to plug it into windows PCs) and I have noticed that a lot of folders seem to copy over even if I haven't made any changes at all!  In fact I used the Size Only flag to stop the contents of these directories from being copied over, but the name of the folder STILL gets mentioned in verbose mode :confused: 

Having said all that it does get the basic job done :grin: 

I also got Grsync for a graphical front end, which works ok.

EDIT : Geez, that's been mentioned 4 posts ago while I was writing this![/QUOTE]
There are Ext3 drivers for Windows so you might want to look into that unless it's not only your machine that you want it to be compatible with.
> I think he means checking if the transfer actually copied the files bit-for-bit successfully. Sort of like how you should check the md5 checksum of iso's you download.
That is exactly what I meant.

---

### Post by aysiu on 2006-07-05
subsonic_shadow, it's good to hear that *grsync* is verbose. Maybe I'll start using that. I kind of like the command-line, though. I've having a bit of trouble getting RSyncX to work on my wife's Mac OS X, though, so she'll be stuck with the command-line for a while. [QUOTE=pchr]I recently discovered this also, for sending my Music and Photo directories to an external USB hard disc.  I'm interested though, what do you mean by

I ask because my USB HD is using FAT32 (I want to be able to plug it into windows PCs) and I have noticed that a lot of folders seem to copy over even if I haven't made any changes at all!  In fact I used the Size Only flag to stop the contents of these directories from being copied over, but the name of the folder STILL gets mentioned in verbose mode :confused: [/QUOTE] Well, that's basically the problem I ran into. I used *rsync* to back up my wife's files on her (then-FAT32) external hard drive, but when I ran it again, it wanted to copy everything all over again, even though there were no changes made.

Once we formatted her drive to HFS+, it worked the way it was supposed to.

---

### Post by Polygon on 2006-07-05
where can you get these ext3 drivers for windows? i googled it but all i see is ext2 drivers for windows...

---

### Post by aysiu on 2006-07-05
[QUOTE=Polygon]where can you get these ext3 drivers for windows? i googled it but all i see is ext2 drivers for windows...[/QUOTE]
[http://www.fs-driver.org](http://www.fs-driver.org) is what you want. It says "Ext3," but it works on Ext3 (I know from personal experience).

---

### Post by Polygon on 2006-07-05
[QUOTE=aysiu][http://www.fs-driver.org](http://www.fs-driver.org) is what you want. It says "Ext3," but it works on Ext3 (I know from personal experience).[/QUOTE]

you mean it says "ext2" but it does work on ext3, right?

thanks i will get to work on this :D

---

### Post by aysiu on 2006-07-05
I'm speaking from experience--it works on Ext3, but I don't know if Ext3 and Ext2 are that different. From Wikipedia: > The ext3 file system adds, over its predecessor:

    * A journal
    * Tree-based directory indexes for directories spanning multiple blocks
    * Online filesystem resizing

Without these, any ext3 file system is also a valid ext2 file system. This has allowed well-tested and mature file system maintenance utilities for maintaining and repairing ext2 file systems to also be used with ext3 without major changes. The ext2 and ext3 file systems share the same standard set of utilities, e2fsprogs, which includes a fsck tool. The close relationship also makes conversion between the two file systems (both forward to ext3 and backward to ext2) straightforward.

---

### Post by OffHand on 2006-07-05
[QUOTE=aysiu]subsonic_shadow, it's good to hear that *grsync* is verbose. Maybe I'll start using that. I kind of like the command-line, though. [/QUOTE]
It's an front-end so essentially it can do what rsync does if it is programmed into the GUI. Maybe you should just start it and look at the options given. But I always say: whatever floats your boat  ;)

---

### Post by vayu on 2006-07-05
[QUOTE=aysiu]
One thing that I found out the hard way, though--don't use *rsync* on FAT32. It's got to be Ext3 or HFS+.[/QUOTE]

Aysiu, exactly what happened when you used it on FAT32?  Do you think there's any chance it was a glitch?

EDIT: Never mind, you answered my question while I was typing it.

---

### Post by aysiu on 2006-07-05
[QUOTE=vayu]Aysiu, exactly what happened when you used it on FAT32?  Do you think there's any chance it was a glitch?

EDIT: Never mind, you answered my question while I was typing it.[/QUOTE]
Well, it appeared to work the first time--it copied all the files over.
But when I ran it the second time, it copied them all over again.

The way *rsync* works, it's supposed to copy only what files have been changed or added since the last time it was run.

For FAT32, it kept copying *everything*, not just what was changed.

Once we formatted my wife's drive to HFS+, it worked fine. I also tested it on a FAT32 USB key and locally on her HFS+ hard drive, and the results were consistent.

**Edit**: A little web research shows I'm not the only one who's found this (maybe I should have done a little web research beforehand):

[http://linuxfromscratch.org/pipermail/blfs-support/2005-November/057705.html](http://linuxfromscratch.org/pipermail/blfs-support/2005-November/057705.html) > At every boot of linux (and at every remount of my fat32 partition put_files copies some files from my ext3 partition to my fat32 partition even when they are not changed. [http://chakravyuh.blogspot.com/2005/09/fat32-woes.html](http://chakravyuh.blogspot.com/2005/09/fat32-woes.html) > FAT32 does not play well with rsync, which is a big pain when I am trying to do a mass backup to an external drive. Thankfully, some good folks have developed FullSync. FullSync even supports synchronization over SFTP and SMB btw :). Rsync workarounds are listed here.

---

### Post by prizrak on 2006-07-05
[QUOTE=aysiu]I'm speaking from experience--it works on Ext3, but I don't know if Ext3 and Ext2 are that different. From Wikipedia:[/QUOTE]
There is very little difference between the two. Anything that can handle Ext2 will work with Ext3 that is the beauty of our wonderful open formats ;)

---

### Post by blkish on 2006-07-05
the 'rsnapshot' package provides a very nice (and easy) way to manage snapshot-style backups with rsync, such as those available with high-end storage systems.

poor-man's netapp. recommended.

blkish

---

### Post by jordilin on 2006-07-26
Aysiu, when you say
> One thing that I found out the hard way, though--don't use rsync on FAT32. It's got to be Ext3 or HFS+.
What did you find out about FAT32 and using rsync? I posted a problem in:
[http://www.ubuntuforums.org/showthread.php?p=1294850#post1294850](http://www.ubuntuforums.org/showthread.php?p=1294850#post1294850)
I have a FAT32 external hard drive and when I switch off/on the harddrive and doing a rsync again, rsync copies files already copied and not modified. What's the answer about this issue.

---

### Post by jordilin on 2006-07-26
> **jordilin said:**
> Aysiu, when you say

What did you find out about FAT32 and using rsync? I posted a problem in:
[http://www.ubuntuforums.org/showthread.php?p=1294850#post1294850](http://www.ubuntuforums.org/showthread.php?p=1294850#post1294850)
I have a FAT32 external hard drive and when I switch off/on the harddrive and doing a rsync again, rsync copies files already copied and not modified. What's the answer about this issue.

Ups, you have already answered this question in some posts before:
[http://www.ubuntuforums.org/showpost.php?p=1218110&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1218110&postcount=26)

---

### Post by Mtnear on 2006-08-10
@ aysiu - I read the article that you linked to from your original post, and it was exactly what I've been looking for.  A nice, simple text to get me started with *rsync*.  I'm looking forward to trying this out, and I'll be giving *grsync* a try as well.

One other question though, I'd like to buy a USB enclosure for an old WD hard drive that I'm not using in order to use it as external backup drive.  Would you have any advice on what kind of USB enclosure / setup to use with Dapper?

Thanks.

---

### Post by aysiu on 2006-08-10
Unfortunately, I don't know much about enclosures. My external hard drive is a self-contained external hard drive.

---

### Post by ciscosurfer on 2006-08-13
Check out **unison** and **unison-gtk** (a front-end if that's something you'd like).  It, too, is a file synchronizer and even uses *rsync* as its base.  The difference, however, is in its implementation.  You're asking yourself, "Why should I try it?"  Because Unison synchronizes in two directions at once, while regular *rsync* goes only in one direction.  In addition, it's adaptive and multi-platform friendly.  You can get it in the repos (easiest way) or grab it from the [creator's page]("http://www.cis.upenn.edu/%7Ebcpierce/unison/").  I've thoroughly enjoyed "being in unison" for awhile now. ;)

---

### Post by aysiu on 2006-08-13
Synchronizing in two directions sounds dangerous. I don't want any risk of me being stupid and accidentally erasing a file. Thanks for the suggestion, though.

---

### Post by Sammi on 2006-08-13
> **Mtnear said:**
> One other question though, I'd like to buy a USB enclosure for an old WD hard drive that I'm not using in order to use it as external backup drive.  Would you have any advice on what kind of USB enclosure / setup to use with Dapper?

Thanks.

The way I understand it a "mass storage device" is a "mass storage device" <period>

They all work the same.

So if you put a random hard-drive in a random hard-drive case with a USB port, it should function like a "mass storage device" and those are supported in the modern Linux kernel, and therefor in most modern Linux distributions like for example Ubuntu.

But please don't take my word for it, as I'm just a random Windows intermediate and Ubuntu noob. I feel kind of confident in this matter though.

On the question of which file system to use: Ext3 is the standard Linux system. You can find windows drivers for it and it is a very stable and capable system too. It also handles rsync better that FAT32 as Aysio has explained.

But if you are thinking about using your hard in many different computers. Specifically windows computers that you don't own, then it will be extra work and a hassle to get permition to install the Ext3 drivers on them. In this situation using FAT32 will be easier IMHO, as it is windows native.

---

### Post by ciscosurfer on 2006-08-14
@aysiu
I think you'll understand better if you [check the homepage]("http://www.cis.upenn.edu/%7Ebcpierce/unison/").

---

### Post by aysiu on 2006-08-14
> **ciscosurfer said:**
> @aysiu
I think you'll understand better if you [check the homepage]("http://www.cis.upenn.edu/%7Ebcpierce/unison/").
If I'm understanding it correctly, it warns you when there are conflicting versions...?

---

### Post by ciscosurfer on 2006-08-14
> **aysiu said:**
> If I'm understanding it correctly, it warns you when there are conflicting versions...?
Yes, this is the way I understand it as well, that conflicting updates are detected and displayed.  And in my experience, they are. :D

I've used it for 2 months and love it.

---

### Post by ubuntu_demon on 2006-08-14
This thread gave me the idea of this blog post :

Examples of the power of the CLI
[http://ubuntudemon.wordpress.com/2006/08/14/examples-of-the-power-of-the-cli/](http://ubuntudemon.wordpress.com/2006/08/14/examples-of-the-power-of-the-cli/)

---

### Post by aysiu on 2006-08-14
That sounds pretty powerful. I think I'll stick with *rsync*, though. I don't ever modify files on my external hard drive, so one-way backups are fine with me.

---

### Post by gkiller on 2006-08-15
People who are using rsync should also have a look at **dirvish** ([http://www.dirvish.org/]("http://www.dirvish.org/") or "apt-get install dirvish"). It is using rsync as the base, but introduces more features on top of that.

I have configured it so that it takes a snapshot of my important files every day, but does not overwrite the old snapshots. Unchanged files are hardlinked from the old snapshot to the new, and only modified files are really copied.

The beauty in that is, that you always have several version of the files backed up, but it does not take up much more space than one single backup. Also, if you want to restore a directory from a given snapshot, you just go to that directory in your backup and copy it over, without need of collecting the desired files from several snapshots.

You can tell dirvish how long you want to keep a snapshot, complex rules are also possible: keep the normal backup for 15 days, but the backup made every monday for 3 months. And the backup made on the 1st of every month keep for a year. Different rules for different directories are also possible.

dirvish runs as a cronjob (have a look at anacron if your PC is not running 24/7), makes once a day (or whatever you configure your cronjob to) a new snapshot and looks for old snapshots to delete.

Because of rsync the backup takes no more than a few seconds if not many files have changed, even with several GB of data in the original folder. Because of the hardlinking each new snapshots takes only a few MB if no files are modified, so there is no harm in having a new snapshot every day and keeping the snapshot for several weeks or months, since every unique file is only existing once physically on the hard drive.

For German speaking users there is an excellent article by a magazine on dirvish: [http://www.heise.de/kiosk/archiv/ct/2006/7/212](http://www.heise.de/kiosk/archiv/ct/2006/7/212)

---

### Post by franganghi on 2007-04-25
NO! Fantastic... i was searching THIS tool since feb!
Thanks.

---

### Post by kowal on 2007-05-09
From [http://www.samba.org/rsync/FAQ.html](http://www.samba.org/rsync/FAQ.html)

> copies every file
Another common cause involves sending files to an Microsoft filesystem: if the file's modified time is an odd value but the receiving filesystem can only even values, then rsync will re-transfer too many files. You can avoid this by specifying the --modify-window=1 option.


Works right with Fat32! ^^

---

### Post by beercz on 2007-05-09
I love rsync - a superb tool that I use an awful lot.

For backups I use [rsnapshot]("http://rsnapshot.org"), which uses rsync.

I it takes regular snaphots of your data, and rather than copy over unmodified files over and over again, it creates hard links to the same files on the backup server, and copies over changed files only.  Thus it is very quick and very efficient.

I shedule my backups using cron to initiate a backup and output to a log file.

All my backups are now fully automated, regular (daily in fact), reliable and quick.

Bliss!!

---

### Post by mcarni on 2008-05-11
sorry for the silly question from a a linux newbie...

It is only 5 months I've been on Ubuntu, and the wound caused by a combination of a fatal Windows crash and a non optimized backup is still sore. (lost plenty of pictures...and music...)
I'm trying to learn from my mistakes, so I now do regular backups of my Ubuntu and I burn plenty of DVD's (:)...)
I used also to copy the backup DVDon my wife's Windows Vista laptop, just in case....
Until when I found out that I have full access to it through samba.
So I started copying the backup files from Ubuntu to Vista...(everything went fine...apart from the fact I can't transfer big files through wifi because it somehow goes in timeout...but using a "crossover" cable was the solution)

I thought that combining samba and rsync (...or grsync...you know since I'm a noob I still like GUI's...) could have helped me, but I guess there is something I'm missing. I read the manual...and the previous posts... :)
I tested grsync with two local folders and everything went fine, the problems started when I tried to look for the folder on the Vista computer.

this is supposed to be the destination folder as I see with Nautilus
smb://toshiba/E/BACK-UP_SU_TRISTAN

but when I try grsync with it, it doesn't work, I tried several combinations, including the using my wife's computer user@toshiba before the address but still I can't get it...

I'm sure it is something silly that I forgot...

does anyone have any idea?

thank you so much

M

---

### Post by madjr on 2008-05-11
anyone proposed this at brainstorm?

---

### Post by kevdog on 2008-05-11
Another +1 for unison.  Its definitely the bomb.  You can make it a one way sync program just like rsync if you want.  A little bit more overhead with this program, but a lot more powerful!!

---

### Post by p_quarles on 2008-05-11
> **mcarni said:**
> sorry for the silly question from a a linux newbie...
No need to be sorry, but you may want to create your own thread about this. This is a very old thread that was dedicated more to discussion of the advantages of rsync vs other backup methods, and not so much how to use it. Since your new question is on the last page of this thread, people are unlikely to see it. 

In any case, I would strongly recommend that you invest in a dedicated, external storage device or server, rather than backing up your data either to DVD or to another computer that is being used as a workstation. This way, you would be able to create separate NTFS and ext3 partitions for backups of those respective filesystems. This will be a lot more convenient in the long-run, and cheaper than DVDs in the not-so-long-run.

---

### Post by urukrama on 2008-05-11
> **kevdog said:**
> Another +1 for unison.  Its definitely the bomb.  You can make it a one way sync program just like rsync if you want.  A little bit more overhead with this program, but a lot more powerful!!

I used to use Unison as well, until I discovered the great sync tools in Krusader, the KDE twin-pane file manager (That file manager is really impressive! I keep finding new features in it...)

---

### Post by fjf on 2008-05-11
I have been looking at grsync and I do not see an option to exclude some folders withing the one to be synchronized.  Can it be done or do I have to look into unison or some other?.

---

### Post by kevdog on 2008-05-11
Ill have to look into Krusader -- does this also use rsync?

---

### Post by hvacr on 2008-05-11
Looks good, to bad it cannot see my NAS drives.

I take that back, it seems it does.

---

### Post by mcarni on 2008-05-12
@ p_quarles

I think I found a thread that was more pertinent and also more recent..

I will try to convince my wife that buying an external hardisk is a need...will see if she signs the approval form....:) 
just kidding, I will definitively buy one...better to be on the safe side....

thanks

M

---

### Post by Paqman on 2008-05-12
> **aysiu said:**
> 
I have to say I *really* despise the acronym RTFM (read the f'in manual)--not so much because of its rudeness but because of its presumptuousness and false assumptions... namely that reading the manual actually helps new users.


Me too. It'd be far more productive to point people towards grsync. Personally I really can't be bothered wading through pages of options when I can just check a few boxes and go.

---

### Post by bobbocanfly on 2008-05-12
This thread made me replace my crappy backup script with a new rsync one and i am so glad i read this thread. I knocked up a simple script (unmount my terabyte drive as its fairly difficult to back that up onto and 80gb disk, run rsync, remount big disk) and the only problems i have had were with my crappy scripting skills.

---

### Post by ghindo on 2008-05-12
Great thread.  I was a lot like ayisu at the beginning of the thread, in regards to how I backed my stuff up.  This thread taught me a lot, and now I'm using gsync to backup to my external hard drive! :)

Two questions, though:
[LIST]
[*]Why is the version of rsync in the repos almost two years old?
[*]Does rsync sync up what I've deleted, too?
[/LIST]

---

### Post by _sAm_ on 2008-05-14
I have tried rsync now just to see what it can do, from folder "A" to folder "B".

If I add text to a textfile in folder A, rsync will see it and update the file on folder B.

If I add words in a OOo odt file rsync will notice and update the file in folder B. 

But, if I change music tags within mp3/flac files in folder A(with Easytag), rsync will not see it. I guess the same are true for pictures(if you tag them with digikam/f-spot and so on). 

Are there any backuptools that can see those changes?

---

### Post by pt123 on 2008-05-14
I love rsync so much I have nearly formatted all of my Fat32/Ntfs drives to ext3.

Sam - rsync is powerful, it can do updates based on dates of the files and checksums. 

It can also keep older versions of the files in another folder.

You need to read the man pages


```

rsync -r -v -c --stats --progress /media/data /media/backup/data/ --backup --backup-dir="/media/backup/originals/data/"  --delete-after 

```

---

### Post by hyper_ch on 2008-05-14
> **ghindo said:**
> [*]Why is the version of rsync in the repos almost two years old?
Is there any reason to get a newer version?

> **ghindo said:**
> [*]Does rsync sync up what I've deleted, too?
Have a look at the switches for rsync... you can set it to delete files that exist no longer in the ORG or you can set it to not delete those files...

---

### Post by _sAm_ on 2008-05-14
> **pt123 said:**
> I love rsync so much I have nearly formatted all of my Fat32/Ntfs drives to ext3.

Sam - rsync is powerful, it can do updates based on dates of the files and checksums. 

It can also keep older versions of the files in another folder.

You need to read the man pages


```

rsync -r -v -c --stats --progress /media/data /media/backup/data/ --backup --backup-dir="/media/backup/originals/data/"  --delete-after 

```
Have read and learned from the man pages here; [http://www.linuxmanpages.com/man1/rsync.1.php](http://www.linuxmanpages.com/man1/rsync.1.php)  
And... it does!! Amazing - works just like I wanted it to. Thanks for your tip pt123:)

---

### Post by Ovinomacner on 2008-05-14
I have not used rsync but have found a command that suits my needs well.  I use cp with -Rup as arguments to backup my home directory to another harddrive.  This plus crontab gives me incremental backups daily without much fuss.

cp -Rup /home /data

---

### Post by maniacmusician on 2008-05-14
> **_sAm_ said:**
> I have tried rsync now just to see what it can do, from folder "A" to folder "B".

If I add text to a textfile in folder A, rsync will see it and update the file on folder B.

If I add words in a OOo odt file rsync will notice and update the file in folder B. 

But, if I change music tags within mp3/flac files in folder A(with Easytag), rsync will not see it. I guess the same are true for pictures(if you tag them with digikam/f-spot and so on). 

Are there any backuptools that can see those changes?
have you tried rdiff-backup as mentioned by previous posters? its name implies that it takes the actual diff of files to determine whether they've been changed, so it might work. 

[This is the article]("http://arstechnica.com/articles/columns/linux/linux-20060202.ars/2") that was linked to earlier. Good luck, and let us know.

---

### Post by 50words on 2008-05-14
Okay, my first stab at using rsync was pretty awesome. I used grsync, though.

There are two things I need to do, however.

1) There are some files I want rsync to ignore. I know to use --exclude, but how do I list multiple files?

2) I want to sync a directory that has contents only when a TrueCrypt container is mounted. How do I prevent rsync from deleting the destination directory (I need to use delete on destination) when the source or destination directory is empty?

---

### Post by ghindo on 2008-05-14
> **hyper_ch said:**
> Is there any reason to get a newer version?Rsync has hit a major release - 3.0.  The version in the repos has not reflected that.

---

### Post by maniacmusician on 2008-05-14
> **ghindo said:**
> Rsync has hit a major release - 3.0.  The version in the repos has not reflected that.
I'm hoping it will be in Intrepid, and be brought over in the mass merge from debian testing. If it's not planned, someone should submit a bug report asking for the package, as it's a pretty nice and for some people, very important and useful one.

---

### Post by pt123 on 2008-05-14
> **_sAm_ said:**
> Amazing - works just like I wanted it to. Thanks for your tip pt123:)

Great to hear that.

---

### Post by hyper_ch on 2008-05-15
> **50words said:**
> 1) There are some files I want rsync to ignore. I know to use --exclude, but how do I list multiple files?
--exclude-from=/path/to/exclusion-list

> **50words said:**
> 2) I want to sync a directory that has contents only when a TrueCrypt container is mounted. How do I prevent rsync from deleting the destination directory (I need to use delete on destination) when the source or destination directory is empty?
I guess you'd run rsync twice.... once with deletion on destination (but exclude that TC container) and once without deletion (and only include that TC container)

---

### Post by oscar_19 on 2008-05-15
how to configure rsync to sync two computers.
example: If I create a file in the first pc, rsync automatically put the file in the other pc.

I need tour help.
Thanks

---

### Post by 50words on 2008-05-15
> **hyper_ch said:**
> --exclude-from=/path/to/exclusion-list

What does this mean? How do I put it to use?

---

### Post by maniacmusician on 2008-05-15
> **50words said:**
> What does this mean? How do I put it to use?
I think exclusion-list may be a text file with a list of directories to exclude from the backup. Not sure, but that was my interpretation of it.

---

### Post by HermanAB on 2008-05-15
"how to configure rsync to sync two computers.
example: If I create a file in the first pc, rsync automatically put the file in the other pc."

Read the rsync man page.  There are complete examples in it.

---

### Post by 50words on 2008-05-15
In a typical /home directory, what files would you recommend excluding when backing up?

What about when syncing the /home directory between two different computers?

---

### Post by 50words on 2008-05-15
Okay, I am using Grsync, since I prefer GUIs.

First, syncing over SSH. To sync with another computer over SSH using Grsync, enter IP:/path/ as the destination, like so:

```
192.168.0.10:/home/50words/
```

But, in order to get SSH to work, you have to click on the Advanced Options tab, and enter the following in the additional commands field:

```
-e ssh
```

Now, in order to exclude files, enter --exclude and the text file name in which you will list your files or directories to exclude in the same additional commands field. For example, here is my path to my exclusion file:

```
--exclude-from=/home/50words/rsync-exclude.txt
```

In that text file, you just identify the files or directories you want excluded. Wildcards work. Remember that rsync will navigate relative to the directory in which it starts (the directory you identified as the source directory). Here is an example of the contents of an exclusion file:

```
.mozilla/firefox/*/Cache
.beagle
```

And so on. The exclude file starts in the location you specified for the source. If you include the full pathname (/home/50words/) it will go to the path you started at, and look for the excluded files further down (/home/50words/home/50words).

Hope that is helpful for others like me.

---

### Post by maniacmusician on 2008-05-17
> **50words said:**
> In a typical /home directory, what files would you recommend excluding when backing up?

What about when syncing the /home directory between two different computers?
For that particular purpose, I usually have a folder inside ~/ that I put all my actual data in, and I keep it separate from all the config files that I want more fine control over the backups of.

I typically retain only some of the program settings from release to release, like firefox sessions, electricsheep data, etc. Stuff that would be more of a pain to replace...and this is also the stuff that I back up regularly. 

I usually do clean installs (I keep a separate /home partition) because I find that the upgrade features still aren't as smooth as I would like, and I find it much more of a hassle to have to fix things than to simply restore them from scratch. So I'll save good looking themes that I've made, a small list of FF extensions, a list of applications I use regularly, and tweaks, etc. 

But yeah, out of just the things that I have in ~/, I exclude everything apart from the following; .kde, .emerald, .fretsonfire, .mozilla (just for the hell of it -- I do like the idea of excluding the cache), .neverball, .sheep, .ssh (very important), .VirtualBox. and .bashrc (critical if you use aliases regularly)

So basically, they're just things that are cumulative and hard to replace. Those sheep took months of running in the background to collect. Virtual Box is where I do important testing of cutting edge software.

---

### Post by Bou on 2008-05-21
Hi,

I've tried using rsync to backup my data. It seems to work fine, except for this:

> rsync: readlink "/home/david/.gvfs" failed: Transport endpoint is not connected (107)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]


Then it stops and, although new files seem to be backed up, deleted files don't get deleted in the destination.

Now that I check it it seems that there is no .gvfs file or folder in my home, but I cannot create one either because "it is being used".

Weird. Do you guys have any clue?

---

### Post by cacycleworks on 2008-05-21
> **maniacmusician said:**
> For that particular purpose, I usually have a folder inside ~/ that I put all my actual data in, and I keep it separate from all the config files that I want more fine control over the backups of.

I typically retain only some of the program settings from release to release, like firefox sessions, electricsheep data, etc. Stuff that would be more of a pain to replace...and this is also the stuff that I back up regularly. 

I usually do clean installs (I keep a separate /home partition) because I find that the upgrade features still aren't as smooth as I would like, and I find it much more of a hassle to have to fix things than to simply restore them from scratch. So I'll save good looking themes that I've made, a small list of FF extensions, a list of applications I use regularly, and tweaks, etc. 


+1 about fresh install over upgrades ... I'm a kubuntu freak and I find that keeping ~/.kde/* is almost 100% stable and also makes upgrades nearly instantaneous. I also like to backup /etc/* as a lot of my personal tweaks are in there.

Bigtime thanks to aysiu for starting it. :-) I'll start it tonight when I leave work and let it churn, baby churn.

:) Chris

---

### Post by oscar_19 on 2008-05-27
I have problems with rsync. I sync one server to other pc but in some files rsync said to me in verbose mode permission denied (13) and rsync cannot copy and open these files. The other files can sync.
Do you know how to solve this problem. I need to copy these files.
If I put chmod 777 in the files rsync make the sync if not it says permission dennied 13.

There are any option in rsync to avoid this problem because I have to make an automatic sync of / ubuntu in other pc.

secert file of rsync I put root:root .

which files and folders do you ommited when sync the /

---

### Post by 50words on 2008-05-27
While I like rsync fine for backups, I just discovered Unison for truly syncing two computers.

I have two computers that I use regularly, but I want to keep a copy of my business files on both. It is a lot easier to use Unison than to run rysync twice every time. Plus, the Unison GUI is better than Grsync.

---

### Post by BDNiner on 2008-05-27
Rsync is amazing. I use it at work to backup about 30 remote location to our colo. It takes about 6 hours since every night we backup about 2GBs per location. but this is from locations all around the country. 

My first task at my job was to figure out rsync and get the solution working. We were using a tape backup system before and could not consistently get people change tapes every day and use the right tapes. 

It is great for sys admin work since it is very light weight and using mail send i got my scripts to send an e-mail with the error report when the process completes.

---

### Post by Anon Customer on 2008-05-28
I'm getting a similar error as Bou:

> rsync: readlink "/home/$USER/.gvfs" failed: **Permission denied (13)**
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

Anyone have any ideas?

---

### Post by BDNiner on 2008-05-28
Are you running the rsync process as root? .gvfs i believe is related to the new gnome virtual file system. you may not be able backup that directory unless you have root permissions. 

I have only used rsync to backup windows servers, and netware servers. so I am not sure how this relates to linux.

---

### Post by Anon Customer on 2008-05-30
Hmm, running as sudo and not both give the same errors. Looks like .gvfs is very odd:
[https://answers.launchpad.net/ubuntu/+question/34333](https://answers.launchpad.net/ubuntu/+question/34333)
[http://ubuntuforums.org/showthread.php?t=781805](http://ubuntuforums.org/showthread.php?t=781805)

From another thread: "You can't do anything to the .gvfs directory because it is currently mounted by the gvfs-fuse-deamon. Type in sudo mount and you will see it in the list. Don't worry about that one."

So for now I've added ".gvfs" to my exclude list which seems to work.

Edit:
And here is the thread that would have told me that. Dangit.
[http://ubuntuforums.org/showthread.php?t=791693&highlight=.gvfs&page=2](http://ubuntuforums.org/showthread.php?t=791693&highlight=.gvfs&page=2)

---

### Post by IgnacioGuerra on 2008-06-11
hi, i have a question about Rsync

i want to backup my Home directory every night (automatically) but the problem im finding is that it bakup and update all the files, but if i erase a file, it will keep backuped file (it will not sync with my home). i know that the main purpose of rsync is to backup and keep all the files (not to keep in sync), but i have my Download folder in my home folder, so when i download something, it will be backuped, then, i move the file to (for example) the music directory where i copy all the downloaded music once its downloaded, so i will have the file in the music folder and in the download folder since rsync will not sync the folder, it will just update the files.

is there some way i can use rsync just to have a copy of my home folder like it was the day before?
other usefull thing will be to exclude some specific folders inside the folder i selected to be backuped.

thanks in advance!

---

### Post by weresheep on 2008-06-11
Hello,

I'm not sure I understand what you are asking. Do you want rsync to delete files in the backup location that have been deleted from the source? If that is the case, you can use the "--delete" option. If you use...

```
rsync -av --delete source/ destination/
```

then the destination will be an exact copy of the source. Delete a file from 'source' then rsync will delete it from 'destination'.

Another great argument you can pass to rsync is "-n". This is a dry run mode and rsync will print out (assuming you also use -v) every file it will sync/delete without actually doing the syncing. Great for checking that backup script :)

To exclude a file, directory or something else from being sync'd use the "--exclude" argument. For example...

```
rsync -av --delete --exclude=music/bad source/ destination/
```

You can specify more than one "--exclude" on the command line.

I use rsync all the time to synchronise my home directory between two computers, and it works perfectly. However there are many subtleties and it took me quite some time to get my script working exactly how I wanted it. My advice is to take your time and test on dummy data.

Hope that helps.

-weresheep

---

### Post by graabein on 2008-09-24
I'm going to backup photos, documents and settings from home directories on my Ubuntu install, but I've got two Windows installs in the LAN also.

How do I backup from Windows XP computers with FAT32 and NTFS onto my Ubuntu ext3 file server? 

Do I have to share the backup directory with Samba and do it Windows style?

---

### Post by ukripper on 2008-09-24
> **aysiu said:**
> 
One thing that I found out the hard way, though--don't use *rsync* on FAT32. It's got to be Ext3 or HFS+.

Works great on ntfs drive too without problem. Being using it since 1 1/2 years now.

---

### Post by kevdog on 2008-09-24
rsync can run over ssh, so if your different types of computers can talk over ssh (Windows, MAC, Linux), you should be able to sync using rsync (or another applied variant).  If you need an ssh server on windows, I would suggest using the cygwin project.  If you know anything about setting up a ssh daemon on windows, the process is nearly the same (as far as the configuration file), however there are just a few more steps required to make it run as a Windows service in the background.

---

### Post by ukripper on 2008-09-24
> **kevdog said:**
>  If you need an ssh server on windows, I would suggest using the cygwin project. 

+1

> **graabein said:**
> I'm going to backup photos, documents and settings from home directories on my Ubuntu install, but I've got two Windows installs in the LAN also.

How do I backup from Windows XP computers with FAT32 and NTFS onto my Ubuntu ext3 file server? 

Do I have to share the backup directory with Samba and do it Windows style?


this link may help you using rsync on windows [http://www.trueblade.com/knowledge/using-rsync-and-cygwin-to-sync-files-from-a-linux-server-to-a-windows-notebook-pc](http://www.trueblade.com/knowledge/using-rsync-and-cygwin-to-sync-files-from-a-linux-server-to-a-windows-notebook-pc)

---

### Post by kpatz on 2008-09-24
Use the **-x** or **--one-file-system** option on rsync to eliminate the error when it tries to copy the .gvfs directory.

You can also use this option when backing up an entire filesystem or directory structure that has other filesystems mounted to it without crossing into those other filesystems.

---

### Post by SP3NGL3R on 2010-09-02
i've been using RSYNC for some time now on my (2nd) work computer, and have just discovered a GUI for it on my home computer.  check it out, it's called simply GRSYNC:
[https://help.ubuntu.com/community/rsync]("https://help.ubuntu.com/community/rsync")

i have HIGH hopes for this ;)

---

### Post by KdotJ on 2010-09-02
This looks like god stuff... I wrote a program that backs up selected directories. But it checks if the current file has been backed up before, and if so, it checks if the file to be backed up is newer than the one that had been backed up previously.

But this has a GUI and all kinds of other options available so I hardly ever use it myself, I made it for my computer-n00b father. I'm going to check out rsync me thinks...

---

### Post by cra1g321 on 2010-09-02
any backing up i do i usually use deja-dup. Might try rsync sumtime

---

### Post by AlexanderDGreat on 2010-09-06
Before backing up I usually take these 5 simple steps.

1. What to backup.
2. Where to put them.
3. Give 5 situations WHY you need a backup. *critical*
4. How do you want to restore it?
5. Choose a backup up strategy.

---

### Post by toupeiro on 2010-09-06
rsync is epic.  I've done trans-atlantic rsync jobs and it just works.

---

