---
title: "Howto: Backup and restore your system!"
date: 2005-10-24
forum: Tutorials
---

### Post by A-star on 2005-10-24
This is a repost from a guide originally made by Heliode for backing up and restoring your system found [here](http://ubuntuforums.org/showthread.php?t=35087)
I changed it so that it works in breezy (thanks to  [this](http://www.ubuntuforums.org/showthread.php?t=70566) thread where I found the solution).

Most of you have probably used Windows before you started using Ubuntu. During that time you might have needed to backup and restore your system. For Windows you would need proprietary software for which you would have to reboot your machine and boot into a special environment in which you could perform the backing-up/restoring (programs like Norton Ghost).
During that time you might have wondered why it wasn't possible to just add the whole c:\ to a big zip-file. This is impossible because in Windows, there are lots of files you can't copy or overwrite while they are being used, and therefore you needed specialized software to handle this.

Well, I'm here to tell you that those things, just like rebooting, are Windows CrazyThings (tm). There's no need to use programs like Ghost to create backups of your Ubuntu system (or any Linux system, for that matter). In fact; using Ghost might be a very bad idea if you are using anything but ext2. Ext3, the default Ubuntu partition, is seen by Ghost as a damaged ext2 partition and does a very good job at screwing up your data.

**1: Backing-up**

"What should I use to backup my system then?" might you ask. Easy; the same thing you use to backup/compress everything else; TAR. Unlike Windows, Linux doesn't restrict root access to anything, so you can just throw every single file on a partition in a TAR file!

To do this, become root with
```
sudo su
```
and go to the root of your filesystem (we use this in our example, but you can go anywhere you want your backup to end up, including remote or removable drives.)
```
cd /
```
Now, below is the full command I would use to make a backup of my system:
```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```
Now, lets explain this a little bit.
The 'tar' part is, obviously, the program we're going to use.

'cvpfz' are the options we give to tar, like 'create archive' (obviously),
'preserve permissions'(to keep the same permissions on everything the same), and 'gzip' to keep the size down.

Next, the name the archive is going to get. backup.tgz in our example.

Next comes the root of the directory we want to backup. Since we want to backup everything; /

Now come the directories we want to exclude. We don't want to backup everything since some dirs aren't very useful to include. Also make sure you don't include the file itself, or else you'll get weird results.
You might also not want to include the /mnt folder if you have other partitions mounted there or you'll end up backing those up too. Also make sure you don't have anything mounted in /media (i.e. don't have any cd's or removable media mounted). Either that or exclude /media.

EDIT : kvidell suggests below we also exclude the /dev directory. I have other evidence that says it is very unwise to do so though.

Well, if the command agrees with you, hit enter (or return, whatever) and sit back&relax. This might take a while.

Afterwards you'll have a file called backup.tgz in the root of your filessytem, which is probably pretty large. Now you can burn it to DVD or move it to another machine, whatever you like!

EDIT2:
At the end of the process you might get a message along the lines of 'tar: Error exit delayed from previous errors' or something, but in most cases you can just ignore that.

Alternatively, you can use Bzip2 to compress your backup. This means higher compression but lower speed. If compression is important to you, just substitute the 'z' in the command with 'j', and give the backup the right extension.
That would make the command look like this:
```
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /
```

**2: Restoring**

Warning: Please, for goodness sake, be careful here. If you don't understand what you are doing here you might end up overwriting stuff that is important to you, so please take care!

Well, we'll just continue with our example from the previous chapter; the file backup.tgz in the root of the partition.

Once again, make sure you are root and that you and the backup file are in the root of the filesystem.

One of the beautiful things of Linux is that This'll work even on a running system; no need to screw around with boot-cd's or anything. Of course, if you've rendered your system unbootable you might have no choice but to use a live-cd, but the results are the same. You can even remove every single file of a Linux system while it is running with one command. I'm not giving you that command though!

Well, back on-topic.
This is the command that I would use:
```
tar xvpzf backup.tgz -C /
```
Or if you used bz2;
```
tar xvpjf backup.tar.bz2 -C /
```
WARNING: this will overwrite every single file on your partition with the one in the archive!

Just hit enter/return/your brother/whatever and watch the fireworks. Again, this might take a while. When it is done, you have a fully restored Ubuntu system! Just make sure that, before you do anything else, you re-create the directories you excluded:
```
mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
etc...
```
And when you reboot, everything should be the way it was when you made the backup!

---

### Post by bionnaki on 2005-10-24
thanks!

---

### Post by bionnaki on 2005-10-24
I just realized an entire system backup from / would be about 26 gigs. I'd like to have everything on DVD-R, so what do you think would be the best way to divide the backup? thanks again!

---

### Post by BLTicklemonster on 2005-10-24
[QUOTE=bionnaki]I just realized an entire system backup from / would be about 26 gigs. I'd like to have everything on DVD-R, so what do you think would be the best way to divide the backup? thanks again![/QUOTE]

     "

---

### Post by matthew on 2005-10-24
[quote=bionnaki]I just realized an entire system backup from / would be about 26 gigs. I'd like to have everything on DVD-R, so what do you think would be the best way to divide the backup? thanks again![/quote]

One thing I do is backup a lot of my data separately. I have my mp3's (almost 10GB worth) in a directory called /music which I backup separately from /videos which is separate from /files-text which is separate from /files-spreadsheet and so on. It would take a little longer to do the backup and restore, but then you can put just one file type on a DVD (or multiple dvd's...just do A-L in one and M-Z on another and so on).

Then I do a system backup excluding all those data files/directories.

---

### Post by bionnaki on 2005-10-24
yeah, I guess that makes sense. thanks man

---

### Post by zigford on 2005-10-25
[QUOTE=bionnaki]I just realized an entire system backup from / would be about 26 gigs. I'd like to have everything on DVD-R, so what do you think would be the best way to divide the backup? thanks again![/QUOTE]

If you want a better backup system, check this thread out:
[http://www.ubuntuforums.org/showthread.php?t=80790](http://www.ubuntuforums.org/showthread.php?t=80790)

It is a script I wrote that helps you cut out the things you don't want to backup.  You can set it to automatically exclude files from your backup the exceed a specified amount.

---

### Post by bionnaki on 2005-10-25
thanks.

I just used the bz2 compression & it cut down the size considerably. I'll just keep the entire / backup on my external harddrive.

---

### Post by _Pete_ on 2005-10-26
[QUOTE=bionnaki]I just realized an entire system backup from / would be about 26 gigs. I'd like to have everything on DVD-R, so what do you think would be the best way to divide the backup? thanks again![/QUOTE]

There's a utility called split which you can use to split files to specified size.

---

### Post by DDM on 2005-10-26
My tips for backing up:

It's easiest to have your media (movies, music) in a separate partition. Mine is in a FAT32 partition just in case I have to venture into Windoze for a few mins.
I have had problems with the method described here, especially when switching filesystems. Now I use Knoppix DVD with partimage. Very easy stuff, never proven me wrong.

And when choosing bz2 vs gzip compression, in my experience bz2 takes about 3 times as long as gzip, and only gives an extra 5-10% when compressing my ubuntu partition. But then again, if you have the extra time, then go for it.

---

### Post by bacchus_3 on 2005-10-26
one quick question though...I would just want to change the partitioning system of my ubuntu system from the normal  to LVM...would this guide be a good approach (with some little tinkering, I guess). or this shouldn't be it.

I wouldn't want to reinstall everything now that I have a working LAMP system and it takes a lot of time configuring everything.

---

### Post by bionnaki on 2005-10-27
[QUOTE=_Pete_]There's a utility called split which you can use to split files to specified size.[/QUOTE]

what's it called?
I dont see it in the repos...

---

### Post by geofff on 2005-10-28
I am trying to retrieve one file (my evolution Inbox) from backup with:

tar xvpfz /media/cdrom1/backup.tgz/<file address> -C /<address of target directory>

I get "Cannot open. Not a directory". 

Can anyone tell me the right code. Thanks

---

### Post by beercz on 2005-10-28
How about doing incremental backups using rsync?  You can do it over secure connections too.

Here's a good guide:
[http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/")

rsync hompage:
[http://samba.anu.edu.au/rsync/]("http://samba.anu.edu.au/rsync/")

---

### Post by majed on 2005-10-28
[QUOTE=geofff]I am trying to retrieve one file (my evolution Inbox) from backup with:

tar xvpfz /media/cdrom1/backup.tgz/<file address> -C /<address of target directory>

I get "Cannot open. Not a directory". 

Can anyone tell me the right code. Thanks[/QUOTE]

The command should be like this:

```
tar xvpfz /media/cdrom1/backup.tgz /<address of target directory>/<file name> -C /<address of target directory>

```

Notice the space after your backup file :)

---

### Post by kakashi on 2005-10-29
another easy way is if you have knoppix you can you partimage on knoppix.
its very good and you can automatically have it split the backup into any size files.
also you can run partimage from ubuntu but can't backup / as it needs unmounted partition.

---

### Post by CapnCook on 2005-10-30
tar doesn't work here, kubuntu 5.10. tar will include all exclude directories and files. any other way, I have checked into rsync but I didn't find any info on doing local backups.

---

### Post by Manu on 2005-10-30
Why don't use KDar?

---

### Post by geofff on 2005-11-01
[QUOTE=majed]The command should be like this:

```
tar xvpfz /media/cdrom1/backup.tgz /<address of target directory>/<file name> -C /<address of target directory>

```

Notice the space after your backup file :)[/QUOTE]

Thanks majed. That did it. Cheers

---

### Post by jrev on 2005-11-02
[QUOTE=DDM]My tips for backing up:

It's easiest to have your media (movies, music) in a separate partition. Mine is in a FAT32 partition just in case I have to venture into Windoze for a few mins.
I have had problems with the method described here, especially when switching filesystems. Now I use Knoppix DVD with partimage. Very easy stuff, never proven me wrong.

And when choosing bz2 vs gzip compression, in my experience bz2 takes about 3 times as long as gzip, and only gives an extra 5-10% when compressing my ubuntu partition. But then again, if you have the extra time, then go for it.[/QUOTE]

I would appreciate to know how you are using it ...I have been on the subject for weeks now if you are interested ?

---

### Post by bionnaki on 2005-11-02
in [this](http://www.ubuntuforums.org/showthread.php?t=85246) user frenkel suggests spliting up the backup. 

> I juse just tar and it rules!!
You can use it like this:
Boot with a livecd (any will do, Ubuntu livecd, Knoppix, Gentoo, it's your choice!)
Mount the partitions. (In this example /mnt/root is my Ubuntu install and /mnt/backup is my backup paritition).
Then run this:
# cd /mnt/root

For a normal tar:
# tar -cjvpf /mnt/backup/backup.tar.bz2 .
Or split it in chunks of 1024 MB, when backup up to FAT32 for example:
# tar -cjvp . | split -b 1024m - /mnt/backup/backup.tar.bz2.
This will create files like backup.tar.bz2.aa backup.tar.bz2.ab backup.tar.bz2.ac

Restoring can be done like this:
# cd /mnt/root
For a normal tar:
# tar -xjvpf /mnt/backup/backup.tar.bz2
For a splitted tar:
# cat /mnt/backup/backup.tar.bz2.?? | tar -xjvp

Good luck!!

Can anyone confirm this?
I'd like to split my backup to 4 gigs each
to fit onto dvd-r.

---

### Post by odin on 2005-11-03
Does anyone have any experience with g4u? I've read in some places it's a very good solution for backing up any system.It's just a bootable cd (or 2 floppies) and you can either make the copy to an ftp server or directly to another hd or other partition in your hd using different levels of compression with gzip.

I

---

### Post by sjpwong on 2005-11-07
[QUOTE=odin]Does anyone have any experience with g4u? I've read in some places it's a very good solution for backing up any system.It's just a bootable cd (or 2 floppies) and you can either make the copy to an ftp server or directly to another hd or other partition in your hd using different levels of compression with gzip.[/QUOTE]

It does work but can take a *very* long time to run as it reads every bit in a partition/drive.

I liked partimage but it seems to be broken in Breezy.

---

### Post by kakashi on 2005-11-10
[QUOTE=A-star] You can even remove every single file of a Linux system while it is running with one command. I'm not giving you that command though!
[/QUOTE]
perchance wold the command be 
```

cd /
sudo rm *

```

hmm i'll see if it is.

---

### Post by A-star on 2005-11-10
[QUOTE=kakashi]perchance wold the command be 
```

cd /
sudo rm *

```

hmm i'll see if it is.[/QUOTE]

Try if you want but don't blame me if you ost everything
:)

---

### Post by A-star on 2005-11-10
Double post

---

### Post by kakashi on 2005-11-13
i have added a backup command (only home) to to crontab so that it runs every morning. could somebody tell me how i can get make cron put the date on every backup name that i can have a couple of backups from everyday. 
i want this so that i can restore to previus setting as welll otherwise cron overwrites the prevuios backup.

---

### Post by GlennB on 2005-11-26
Hi,

[QUOTE=kakashi]could somebody tell me how i can get make cron put the date on every backup name that i can have a couple of backups from everyday. 
[/QUOTE]

I'm not very familiar with cron syntax, but you can get linux to add the date (in various formats) by using the date command. For example, to create an empty file called 

'backup_ (date in date-month-year format)' 

you could do this:

 touch backup_$(date +%d-%m-%Y)

creates a file called (e.g.) backup_26-11-2005.

If cron allows this kind of syntax, it should be straightforward to do what you need. Hope this is some help.

Regards,

Glenn.

---

### Post by Mr. Electric Wizard on 2005-11-27
What if I am restoring to a system that has a different Motherboard, Processor, and such.  
Can I just bring over my old hard drive (the one that I backed up) and load it up on the new hardware?
Can I expect to have my OS load up correctly?

---

### Post by kakashi on 2005-11-27
[QUOTE=Mr. Electric Wizard]What if I am restoring to a system that has a different Motherboard, Processor, and such.  
Can I just bring over my old hard drive (the one that I backed up) and load it up on the new hardware?
Can I expect to have my OS load up correctly?[/QUOTE]
you could backup only 
[code]
bin   etc      lib    opt   root  srv    sys  usr  home  media   sbin   tmp  var 
[code]

first install a server system. then run the command to restore.
i hope this helps although i have begun to have doubts about it. don't try it unless someody better than me comments.

---

### Post by z_diver on 2005-11-27
[QUOTE=Mr. Electric Wizard]What if I am restoring to a system that has a different Motherboard, Processor, and such.  
Can I just bring over my old hard drive (the one that I backed up) and load it up on the new hardware?
Can I expect to have my OS load up correctly?[/QUOTE]


How different of a processor?  I've had amazing success with Intel P3 installs just starting right up when plugged into a P4 machine.  I've never tried to get a P3 install going on an AMD though or even a P4 install moving to a Intel 64 bit machine.  If anyone else has tried this let us know how it worked.

btw, you are going to do this with a backup right?  I highly recommend this as that way you have little chance of data loss.  Also, if you want the drive to boot right up, you will need to have an MBR with grub or lilo which is a separate partition from / and your linux install. 

Chuck

---

### Post by petervk on 2005-11-28
[linux.com article on sbackup]("http://www.linux.com/article.pl?sid=05/11/22/2110251")

[SourceForge   Download Site]("http://sourceforge.net/project/showfiles.php?group_id=145360")

This is a really easy backup solution. I'd get the deb from sourceforge as the one in the repositiries is a version old.

---

### Post by Joeak on 2005-12-05
(shameless copy from the net.  modify tar to include split below)

Not tar per se, but you might be able to do this with 'split'.  You'll
have to reassemble the pieces afterwards:

    tar czvf - source | split -b 650m tarpiece-

...should create files tarpiece-aa tarpiece-ab tarpiece-ac...

To reassemble, copy to disk, then:

    cat tarpiece-* > file.tar.gz 

...will reassemble the tarfile.

---

### Post by viscount on 2005-12-14
Just a thought, but p7zip creates tighter archives that take up even less space
than bz2, anyone tried it yet?

---

### Post by Mguel on 2005-12-17
I'm not sure about something:

I have mounted /home on another partition than root.

I done the backup, without excluding /home since it was only 3 Mb, and I saw that /home was included in the backup (I believe it's something similar to what have happended if I wouldn't exclueded mounted partitions).

My question is: when I restore that backup which includes /home it will also restore/change my home files even though they are in another partition?. When restoring this backup I will loose the files I store on home on the future?

Will the command: ```
tar xvpfz backup.tgz -C /
``` only overwrite existing files in the backup, or will it also delete non existing files in the backup? (ie if on the root I create a folder "test folder", after making the backup, when I restore the old backup, will this folder be deleted? or it will be preserved since it's not present in the compressed backup?)

Thanks in advance,
Mguel

PS: I'm new to linux and it's still a bit confusing for me ;) Cheers
PSS: Shouldn't the /tmp folder be exclueded also?

---

### Post by viscount on 2005-12-18
[QUOTE=Mr. Electric Wizard]What if I am restoring to a system that has a different Motherboard, Processor, and such.  
Can I just bring over my old hard drive (the one that I backed up) and load it up on the new hardware?
Can I expect to have my OS load up correctly?[/QUOTE]

In general I think you should be pretty safe, as long as you are sticking
to similar cpus, ie ia32 processors, so switching from AMD to Intell should be safe.

This is because  most programs are compiled as generic i386.
If your backup includes a kernel and it is anything other than i386 then you may
have some trouble, although it is possible you will have no problems at all
because the kernel simply wont use extensions that it cant when you switch it to the
other system.

Another thing to be aware of, both systems will probably need to use the same
version of glibc, if you backup a program compiled with one version of glibc
then transfer it to another system running a different version of glibc it will
most likely not be able to run at all.

I guess you could sum this all up as: "depends, try and find out!" :)

---

### Post by viscount on 2005-12-18
[QUOTE=Mguel]I'm not sure about something:

My question is: when I restore that backup which includes /home it will also restore/change my home files even though they are in another partition?. When restoring this backup I will loose the files I store on home on the future?
[/QUOTE]

Yes. A backup is sort of like a snapshot of what your system looks like, and when
you restore the backup it changes EVERYTHING back to the way it was
at the time you made the backup.

If you dont want your home directory to be backed up I suggest that you include
"--exclude=/home" in your tar command.

Also, you should exclude the backup itself next time you make a backup other
wise eventually you will be making a backup copy of an old backup copy of an old backup copy... which is a bad thing.
"--exclude=/home/backups/mylastbackup.tar.bz2"

---

### Post by linuxden on 2006-01-18
Not sure how much of use this is but here is a shell script i use for my backup....

I know its really easy to do but here it is nonetheless... I back up all every week... makes things a  lot quicker....

---

### Post by Parkotron on 2006-01-20
All very interesting, but I think I'll stick with partimage.

---

### Post by linuxden on 2006-01-24
[QUOTE=Parkotron]All very interesting, but I think I'll stick with partimage.[/QUOTE]

Part image is great if your reeinstalling on an identical machine....

But the flexibilty of this method is great you could use it to upgrade hard disk for instance... Just one use of a immensely useful technique...!!

---

### Post by ephman on 2006-02-05
hi,

i was backing up my system, and had to stop it (long story).  so i killed the process, i then went and deleted the backup file.  but now i'm about 2gig short of space, eventhough i deleted the backp file.  any help would be really appreciated.

thanks for the bandwidth,
ephman

**EDIT:**
duh!!!  had to head over to roots trash and delete it from there.

---

### Post by hyperpsyched on 2006-02-14
So if i do not touch anything in the files that were excluded in the tarball I can tinker to my hearts content and if I do something newbie like then replacing the file structure with the tarred archive will get me back up and running?

Is there a danger that mucking about in a file that was not excluded in the original directions wil affect something in a file that was excluded in the original directions?

In other words, how safe is this and how idiot proofed is my computer if I start mucking around with config. files while trying to  learn what they do and how they function?

---

### Post by linuxden on 2006-02-15
Hyper,

You can rest assured that if you follow the above instructions, your computer will be restored to exactly the same state as it was on the day of the backup...!!! 

If you decided to change some hardware on your pc, then perhaps you will need to tinker a bit...(if you add a new HDD...)

But otherwise enjoy mucking about in the config...

Oh and rememeber to backup regularly, (having done one backup tends to lure you into a feeling of false security ie you only do the one backup every 6 months...)

Bye bye

---

### Post by kittcankitt on 2006-02-20
I followed the instructions in the first post on how to backup everything I wanted to (ie: excluding what was to be excluded) only I had to do so using a live cd.  I created the backup.tar in the root folder of where I had mounted my partition, /mnt/tmp.  Now as you can well guess, everytime I try to "un"tar my backup in my fresh server install (with no hardware changes) from the / folder everything extracts to /mnt/tmp/..........

I have tried extracting a single file using tar xvpfz backup.tgz /mnt/tmp/etc/apt/sources.list -C /etc/apt/  and many different variants all with the same results.  "tar: mnt/tmp/etc/apt/sources.list: Not found in archive"    Well, I know it is because when I first tried to extract before I knew what was going on some of the files were extracted to my /mnt/tmp and they are exactly as they were when I made the backup.  

So to some it all up, is there ANY way to get my backup to extract in the right place not having (ex: /bin extracted to /mnt/tmp/bin) right now that is what the original command in the first post gets me.   I tried tar xvpfz backup.tgz /mnt/tmp -C / and I get the error that /mnt/tmp: Not found in archive?  

Any help would be extremely appreciated at this point.   Thankx! kck

---

### Post by linuxden on 2006-02-21
could you move the "backup.tgz" file you are trying to untar to your / directory maybe that will work...

Let me know how that goes....

---

### Post by darrenrxm on 2006-02-21
This would be totally awesome if they could put into Automatrix. I really should suggest this to Arnie. But I have no idea if it is possible.

---

### Post by kittcankitt on 2006-02-21
I do have it in / . Right now I am slowly extracting folder by folder using a live cd and skipping past the /mnt and /tmp in a root nautilus/archivemanager and extracting it to the right destination.  All I did prior was renamed all the other folders _bak until I can see how this works.  This is obviously not the best solution but I haven't been able to get anything else to work and for that matter I'm not sure this will either.

Any other ideas?  I am still very open to suggestions!  Thanks kck

---

### Post by kittcankitt on 2006-02-21
Anyone?  I have quite a bit extracted now but I seem to be freezing up while trying to extract /usr (I imagine due to the size) and I can't get any further without perhaps going into /usr and start extracting individual or maybe groups of folders to their proper destination.  

On a personal note:  this really sucks!

---

### Post by linuxden on 2006-02-21
kittcankitt,

Can you right click on the backup.tgz file and select "extract here" ? If so by having placed your backup file in the root directory, you should be able to extract it...

I can imagine how frustrating it is to unpack file by file....

good luck

---

### Post by kittcankitt on 2006-02-21
No. You see when I try that, everything extracts to /mnt/tmp/.  It creates the /tmp in the already there /mnt.    To boot the problem I get now with my current "extraction process" is that I'm getting an error from archive manager that the file list being too long (actually, it's the first time I got the error and it was while extracting /usr and it took 122.04 mins to get that error!)  Very frustrating indeed!  lol

I know the cause of all this was by creating the tar in the /mnt/tmp dir. in the first place but I didn't have many options at that point as I was "live" and had mounted my / there.  Even to browse the backup.tgz now in archive manager,  it first presents me with /mnt the I double click my way to /mnt/tmp and voila!  my / and all subdirectories right where I need to be, sort of...

Thanks for trying to help me out here, by the way.  Kck

---

### Post by linuxden on 2006-02-22
Ok now am just offering this as a solution but not guaranteeing anything...(you have a backup so its not too bad if you mess up your machine....) LOL

Extract your backup.tgz file to /mnt/ you should now have a fictitious "root" filesystem in /mnt/ now 
```
sudo mv /mnt /
``` 
```
cd /
```
```
sudo mv mnt/* .
``` 

Dont forget the [SIZE="5"][COLOR="Magenta"] . [/COLOR][/SIZE] that should move all files in "/mnt/" to the current directory and overwrite existing files...

Let me know how that goes...

---

### Post by ardchoille on 2006-02-22
I use [PartImage]("http://www.partimage.org/") to back up my partitions. PartImage is available on the [System Rescue CD]("http://www.sysresccd.org/Main_Page") along with tons of other great tools.

Run partimage, tell partimage which partition to backup, fill in the blanks and in about 15 minutes partimage has your parition backed up. PartImage has a nice ui and is very easy to use. Restoring my root partition took about 10 minutes and I was back to the state my system was in at the last backup. PartImage is a Ghost/Drive-image clone for Linux.

---

### Post by Fred Doolie on 2006-02-23
Very excellent but I need to get something straight in my head.
Right now I have a dual-boot system; Win on hda1 and Ubuntu on HDA5
The ultimate goal is to remove Winblows some day soon.

Tell me if this is correct:
1) I do this backup tutorial here.
2) Copy the file onto my external USB drive
3) Boot up a live CD
4) Repartition the HDD removing Win and making it one big Ext3 partition.
5) untargz the file onto the new partition
6) Reinstall Grub fixing menu.lst as needed
and I'll have my exact same system with ALL the files?

Thanks

---

### Post by A-star on 2006-02-23
don't forget you have to edit the /etc/fstab file with the correct mappings to your filesystem.

but for the rest I don't see any other problem, but maybe someone else can correct me?

If you want to be really sure, I suggest that you try in a virtual machine (VMware server is a free download now)

---

### Post by fletch331360 on 2006-02-23
o.k. i backed it up from the directions in the first post now how do i find it to see what size it is and burn it?

i know it is not in my home dir.

thanks

---

### Post by A-star on 2006-02-23
in what folder where you when you executed the command?
if you literally followed the guide, it should be in the directory from where you executed the command.

---

### Post by fletch331360 on 2006-02-23
i was in my main terminal window which is "sean@dv1150:~$" . i realize this is a noob question but thats because i am curently one :) . trying to learn and change that but for now i get lost very easy.

thanks

---

### Post by martinbriscoe on 2006-02-23
Hello 

I want a backup system that just keeps a clone of 'my documents' on another HDD. Rather like the sync system to backup my pda data. Ideally Id like the copy to update automatically at a frequency of my choosing. And Id like it to have a GUI as I have been immersed in windows for so long I cant cope with a command line any more.

Ive looked at cpbk and mirrordir in ubuntu but they dont have a gui. Also seen mention of rsync also without a gui.

Does anyone know if the thing I am looking for exists?

Martin
Exeter

---

### Post by A-star on 2006-02-24
Take a look at the the tool "simple Backup", it has a gui and it easy to configure.

Kind regards
A-star

---

### Post by robert_pectol on 2006-02-24
[QUOTE=martinbriscoe]I want a backup system that just keeps a clone of 'my documents' on another HDD...[/QUOTE]
I know you mentioned wanting a nice gui interface for accomplishing this.  However, since it's such a simple thing to do with readily available command line tools, it's almost not worth the trouble to write a gui for it.  You could accomplish your requested task in a one-line cron job!  I'd recommend the use of rdiff-backup.  It employs rsync, rdiff, and ssh to provide complete mirroring of a file, dir, partition, etc.  It maintains version history and is very efficient across networks for those that want to maintain a backup on a remote server (or even a local fileserver for that matter).  Anyway, something like the following should do what you want:
```

rdiff-backup ~/Documents/ /path/to/backup/Documents

```
Just put that in your user's crontab and it'll automatically run at the intervals you specify.  Simple, quick, and effective!  You'll need to install rdiff-backup which is available in the repos (sudo apt-get install rdiff-backup).

You can restore from the backed up directory very easily.  Since it creates a mirror, you can directly copy the files/directories back to the original location using common commands like cp.  However, since rdiff-backup also keeps version history, you have the added benefit of being able to restore a particular version of the file/directory!  See the following page for more details and examples.  It also has examples of backing up/restoring to/from remote hosts:
[http://www.nongnu.org/rdiff-backup/examples.html](http://www.nongnu.org/rdiff-backup/examples.html)
Again, another simple one-line command in a script or at the command prompt could be used to restore your directory from the backup.  An example is:
```

rdiff-backup -r now --force /path/to/backup/Documents ~/Documents

```

Anyhow, I hope that helps you or someone else out there.

---

### Post by peppermint on 2006-02-26
[QUOTE=A-star]
Now, below is the full command I would use to make a backup of my system:
```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```
[/QUOTE]

Could this method be used to backup/restore a Windows installation without having it cry too much?

If it can, then my life has just been made easier, and most of my friends problems have been solved 8-)

---

### Post by linuxden on 2006-02-26
Nope unfortunately this only applies to UNIX... Becasue windows does not let you copy a lot of the configuration files...(they copyright there Files...)

I wasnt aware you could use TAR in windows... Or even get a terminal...(i know bout "dos", but really...)

---

### Post by peppermint on 2006-02-26
I didn't mean doing it on the windows installation through the command prompt. Instead i was thinking of using the Ubuntu live CD with an external drive.

Also if the files are copyright, Ive been breaking the law with every backup I've made :razz:

---

### Post by A-star on 2006-02-27
[QUOTE=peppermint]I didn't mean doing it on the windows installation through the command prompt. Instead i was thinking of using the Ubuntu live CD with an external drive.
[/QUOTE]
I can only say, try it and let us know.

---

### Post by linuxden on 2006-02-27
[QUOTE=peppermint]I didn't mean doing it on the windows installation through the command prompt. Instead i was thinking of using the Ubuntu live CD with an external drive.[/quote]

From your 1st post i was unaware you were going try using a "live cd"...

Dont know if it will work...

For sure it would be interesting to know if it works...

> Also if the files are copyright, Ive been breaking the law with every backup I've made :razz:

Am sure you like many of us here and in the world have broken 1 of the many clauses in M$ EULA at 1 point or another in our lives... (i dont condone the behaviour...)lmao
 
About my last post...: 

The "thought process" that was going on in my head didnt come out as planned... :oops:

If you were going to zip all files in windows partition to create a backup of your windows drive, it would not be possible becasue you do not have read permission on all files... Is what i was thinking of... God know how that copyright thing came out... lol

Good luck to you

---

### Post by peppermint on 2006-02-27
My fault, I should really try to be a little more specific when I post 

[QUOTE=A-star]I can only say, try it and let us know.[/QUOTE]

Okay, I'm making the backup now :wink:

---

### Post by mozkill on 2006-02-27
on the restore, does it restore the MBR ?   has anyone made a tool that does all this work?

---

### Post by linuxden on 2006-02-27
Mozkill,

No it will not restore the MBR... You will need to reeinstall it with a fresh install... and then, when you do the restore process it will restore grub settings by restoring menu.lst... 

Hope i am not too confusing...

---

### Post by peppermint on 2006-02-27
Im having trouble making the backup file.

I tried making the file with this command
```

cd /mnt/windows
tar cvpzf backup.tgz -exclude=/mnt/windows/backup.tgz /mnt/windows

```
But it only made files upto 4 gig then topped its self.

So i tried splitting the files, first with this command
```

tar -cjvp &#8211;exclude=/mnt/windows/backup . | split -b 512m - /mnt/windows/backup/backup.tgz.

```
but towards the end of the 10th file, it starts backing up backup.tgz.aa. How do I stop that from happerning?

---

### Post by matthew on 2006-02-27
[quote=peppermint]Im having trouble making the backup file.

I tried making the file with this command
```

cd /mnt/windows
tar cvpzf backup.tgz -exclude=/mnt/windows/backup.tgz /mnt/windows

``` But it only made files upto 4 gig then topped its self.

So i tried splitting the files, first with this command
```

tar -cjvp –exclude=/mnt/windows/backup . | split -b 512m - /mnt/windows/backup/backup.tgz.

``` but towards the end of the 10th file, it starts backing up backup.tgz.aa. How do I stop that from happerning?[/quote]What filesystem are you using? If you are making the backup on a fat32 partition or drive the filesize limit is 4 Gb.

---

### Post by linuxden on 2006-02-28
[QUOTE=peppermint]
but towards the end of the 10th file, it starts backing up backup.tgz.aa. How do I stop that from happerning?[/QUOTE]

You could add --exclude=/path/to/backup.tgz.*

That would stop you from backing up backup.tgz.aa backup.tgz.ab etc etc...

---

### Post by matthew on 2006-02-28
[quote=linuxden]You could add --exclude=/path/to/backup.tgz.*

That would stop you from backing up backup.tgz.aa backup.tgz.ab etc etc...[/quote]This is a better answer than mine...sorry, I misread the problem but linuxden read it right.

---

### Post by peppermint on 2006-02-28
Thanks mates, I forgot about wild cards. I'll try when I get home.

---

### Post by linuxden on 2006-02-28
Wildcards kick butt!!! 

they multiply the power of command line...

Hope it works out, let us know...

---

### Post by peppermint on 2006-02-28
Ive tried to back it up again and it still tried to backup the backup. This was the command

```

tar -cjvp -exclude=/mnt/windows/backup/backup.tgz.* . | split -b 512m - /mnt/windows/backup/backup.tgz.

```

You will notice the one dash behind exclude. I dont know if that will make any difference but ill try again tomorrow unless someone posts, saying that it wont change anything to have two dashes there.

---

### Post by matthew on 2006-02-28
[quote=peppermint]Ive tried to back it up again and it still tried to backup the backup. This was the command

```

tar -cjvp -exclude=/mnt/windows/backup/backup.tgz.* . | split -b 512m - /mnt/windows/backup/backup.tgz.

``` 
You will notice the one dash behind exclude. I dont know if that will make any difference but ill try again tomorrow unless someone posts, saying that it wont change anything to have two dashes there.[/quote]That is likely your problem. You do need two dashes.

---

### Post by peppermint on 2006-03-01
Okak, I've done it.

The command I used was
```

tar -cjvp . | split -b 512m - /mnt/windows/backup/backup.tgz. | .  --exclude=/mnt/windows/backup/ /mnt/windows

```

Putting the exclude before the split command stopped it from working.

Then to restore,
```

cat /mnt/windows/backup/backup.tgz.?? | tar -xjvp

```

At the end of the backup, I accidentally closed the terminal before it finished writing the last file. So at the end of the restoration it complained that the end of the file was met prematurely. Non the less, Windows still successfully started and allowed me to log in. The only noticeable difference was that a desktop.ini file opened after login, and the same file made itself an icon in the quick start bar.

---

### Post by linuxden on 2006-03-01
Cool!!
Glad to know the copyrighted files can be backed up... ;o) LMFAO!!! ;o)

---

### Post by ncappel1 on 2006-03-02
Using this command will backup an entire system, but what should we do if we only want to backup the things that have changed since the initial installation? My main concern are files I downloaded from synaptic, my internet connection isn't the fastest, it would take forever to download everything again! Is it too complex to do? would it really just be easier to backup everything?

---

### Post by robert_pectol on 2006-03-03
[QUOTE=ncappel1]Using this command will backup an entire system, but what should we do if we only want to backup the things that have changed since the initial installation? My main concern are files I downloaded from synaptic, my internet connection isn't the fastest, it would take forever to download everything again! Is it too complex to do? would it really just be easier to backup everything?[/QUOTE]
Use rdiff-backup!  Once you've made the first backup, subsequent backups will then only backup the changes that have occured since the last backup.  This makes it very fast and efficient, especially if you're backing up your system to a remote host located elsewhere.  See [http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/) for more info.  By the way, rdiff-backup is in the repos (sudo apt-get install rdiff-backup) for easy installation.  Hope that helps.

---

### Post by A-star on 2006-03-16
Should I submit the original post the Ubuntu Book initiative?
What do you guys think?

---

### Post by wishyjr on 2006-03-19
hey guys,

i've just used the commands from the original post, and its worked fine. Trouble is that once i burned my backup.tgz onto a dvd i wanted to get back the space used up by the.tgz file, so i deleted it. fine and dandy!

but, i've checked my HD space and everything indicates that the space is still being used up! not cool. any ideas?

i deleted it using nautilus (im a gnome user at the mo) as root. is that anythngi to do with it?

cheers.

---

### Post by peppermint on 2006-03-19
Empty the bin :P

---

### Post by wishyjr on 2006-03-19
LOL touche, but i already thought of that :)

ok, UPDATE:

figured it out, that i'd deleted it from my user profile but not from the roots. Quickest way to get rid was simply to load up nautilus as root then goto the wastebasket using the 'go' dropdown menu. i found it there along with a few other bits, got rid and now i have even more space than usual!! hooray for me!

might be worth a look if you think you've lost some space on your HD.

ta luvvies,

wishy

---

### Post by linuxden on 2006-03-20
A-star submit it for sure... Its the best tutorial in ubuntu forums for backingup... (that and Heliodes) ;o)

Got to go! Man I hate Moving!!!

---

### Post by shame on 2006-04-14
Hope someone can help me here.
I've used this method to do backup/restore many, many times.  Not just with ubuntu but with all other distros I've used and I've never EVER had a single problem... until now.
I backed up my ubuntu dapper install the same way as I always do, ready to move it from one ext3 partition to another ext3 one, checked and double checked the command and it ran without errors.
I did the same as I always do to restore it to the other partition, checked and double checked the command and it ran without errors.
I edited my suse (primary grub which chainloads the others) menu.lst so I could boot it and edited fstab to account for the partition change.
When I cam to boot up it stopped just before gdm appears saying there was some problem so I rebooted in verbose and everything is failing, saying it is a read-only filesystem.
I've done fsck on the partition and I've tried restoring it again to the same partition and yet again to a different partition.
The trouble is, after restoring it to the new partition I formatted the original one so I have no way of redoing it.
The only time I have heard of this is when someone I know restored his suse install (using this method) to an ext3 partition when the original was reiser but that isn't the case with me.
There is nothing wrong with the drive itself since I have other distros on it and they are working fine.

---

### Post by Aliby on 2006-04-18
This was a duplicate of the next post.
I really wanted to delete this message, but have no idea how to do so
**HELP**
:???:

---

### Post by Aliby on 2006-04-18
I am quite a newb, so tend to "break" the system relatively often. 
Break would mean anything that prevents me quickly logging in and checking email or writing a doc and printing etc. I have done this trying to change printer settings, installing the nvidia driver etc. I don't want to be without a working system so ...

So what I want to do it to duplicate a working installation and "playing" on the dulicate to improve it, while leaving the working install alone for normal useage. As the "playing" system becomes operable I want to copy the entire system over the "working" system so that I have the improved system available for normal useage again and can continue playing with new configs etc on the other.

I have two 20Gb partitions that I want to use for this. 
[LIST]
[*]How can I copy /duplicate the entire system? (I would want to do this relatively often)
[*]Is it worth creating a new HOME partition that both system mount? If so why and how big should I make it considering I would have 40G available for the three partitions. (Home, "working", "playing").
[/LIST]
:-k

---

### Post by kakashi on 2006-04-18
[QUOTE=Aliby]I am quite a newb, so tend to "break" the system relatively often. 
Break would mean anything that prevents me quickly logging in and checking email or writing a doc and printing etc. I have done this trying to change printer settings, installing the nvidia driver etc. I don't want to be without a working system so ...

So what I want to do it to duplicate a working installation and "playing" on the dulicate to improve it, while leaving the working install alone for normal useage. As the "playing" system becomes operable I want to copy the entire system over the "working" system so that I have the improved system available for normal useage again and can continue playing with new configs etc on the other.

I have two 20Gb partitions that I want to use for this. 
[LIST]
[*]How can I copy /duplicate the entire system? (I would want to do this relatively often)
[*]Is it worth creating a new HOME partition that both system mount? If so why and how big should I make it considering I would have 40G available for the three partitions. (Home, "working", "playing").
[/LIST]
:-k[/QUOTE]
make a home partition of about 5 gb
make 2x5 gb partions (the 2 roots).
make a 1gb swap partition. 
and make a single 35 gb partition for your storage and backups. 
i would advise lvm use but since your new lets not make it tooo complicated. 

ok now here what you should do (what i would do)
dl a copy of knoppix (dvd cd depends on you) burn it and keep it
knoppix will allow you to use your computer for email and internet even if your install and rotting in hell
now install and backup your system. partimage on knoppix does a far better job IMO (since it restores grub as well) but you can use whats here as well. 
any large files you dl always put in the storage partition. and always save your doc and fiel in home. 

you eill have toi learn to use grub. i recommend the gentoo handbook for that. its really good.

---

### Post by dannysauer on 2006-04-18
Sortry to bring this back from the dead, but...

[QUOTE=A-star]'cvpfz' are the options we give to tar, like 'create archive' (obviously),
'preserve permissions'(to keep the same permissions on everything the same), and 'gzip' to keep the size down.[/QUOTE]

It might be worthwhile to make sure that the "f" is the last one in this description.  The order fo the others is not important, but the "f" has to come last, just before the output filename.  It's right in the code snippet, but wrong in the description.

Create file, Verbose, Preserve permissions, gZip, output File

If creating archives, I'm partial to sticking a "W" in there as well, so it'll verify the backup.  Takes longer, but it also alerts you if something went awry.  I'd rather be alerted now rather than when I go to restore from the backup...

---

### Post by morequarky on 2006-05-05
Would the following work on my system?  I think so.  Just wanting to make sure.

"sudo su"
"tar cvpjWf /home/<username>/systembackup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/home/<username>/systembackup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/home/<username>/fat32 --exclude=/media /"

(recreating the system from the file)
sudo su
tar xvpjf /home/<username>/systembackup.tar.bz2 -C /
mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
mkdir home/<username>/fat32
mkdir media
(reboot ubuntu breezy)

---

### Post by giddy1945 on 2006-05-06
I now have the 'backup.tgz' copied to a 4.7G DVD.  It is one single 2.3G file.  Let's say that my harddrive fails beyond repair.  I go buy a new harddrive and install it.  What do I do with the disk?  Do I just plop it in as if it where the 'install' CD?  Do I use the 'live' CD?  Please respond like you would to someone who has used Linux for only five months.  As a matter of fact, I have only been into computers for five months.
Never used $oft and never will.

---

### Post by elemental666 on 2006-06-10
[QUOTE=giddy1945]As a matter of fact, I have only been into computers for five months.
Never used $oft and never will.[/QUOTE]

I just gotta give you kudos on that one.  ;)

---

### Post by pecos.wil on 2006-06-17
okay, i have 2 questions and if i missed these in the forum you may smack me upside the head.

i don't want to include my music folder, which i copied of the XP box that my wife and i share.  is this how i would exclude it? "--exclude=/home/<username>/My Music"

and is it possible to write the backup.tgz to a network address, such as on my XP box where i have a 160gig hard drive being used as a backup location for my computer? -> it is simply a shared drive.

thanks

---

### Post by Grog140 on 2006-06-21
If I reinstall my machine and preserve the backup file will it work?

I mean will it basically be as if I did not format at all?

---

### Post by pecos.wil on 2006-06-22
Yes, if you create the backup.tgz and move it off your machine and install something else or it gets fragged then you can reinstall ubuntu and then apply the backup.tgz via the instructions @ the very beginning of the forum.

---

### Post by Adler on 2006-08-24
Hi All,

I guess that I got caught up in something recently, and lost my whole set-up. 

Normally, I back-up my files, and folders to either an external mass storage unit (300Gb Seagate Drive), DVD, or put it in Cyberspace e.g. email. So, in most cases I'm safe. **However**, I don't think that I'm safe enough. Like, I did loose a bunch of my Server, CMS site settings.

This thread is a little old -- so what's new? Applications, or just Code?

Adler

---

### Post by A-star on 2006-08-24
Nothing as far as I know, the howto in the first post keeps working for me.

---

### Post by calvinthomas on 2006-08-24
Hi, I don't have the harddisk space to back this up to on my drive, can I directly put it to a dvd, (My drive is only 8 GB 1.6GB free) so with bz2 compression i'm guessing it would fit on one dvd? Can anyone tell me how to do this?

Calv

---

### Post by Adler on 2006-08-24
A-star,

Thanks for the reply. Isn't there anything else out there? 

Basically, a lot of us would like to save *everything* from time to time or run a chron job.

Some of us have limit disk space, but others have external drives where space doesn't matter. Isn't there anything else out there?

Adler

---

### Post by A-star on 2006-08-25
there is some software wich does the same as my first post but you can set it up to run a specified times. And it has a nice gui too.
Unfortunately I can't remember the name.

---

### Post by Kaobear on 2006-08-25
Nicely done, simple and clean

---

### Post by kencoe on 2006-08-26
Please excuse me if I am having a brain fart, but I seem to be missing something in these comments. 

I have seen a few people ask about resized or moved partitions. If you re-install and have /home (for instance) now on a second drive, wouldn't the backup just transparently use the mounted partition as the old sub-dir? wouldn't you just need to copy your new /etc/fstab before the restore, and then move it back over after completion?

Also, any problems with this method and saving backup to a different dir? I would really like to create them in, say, /var/backups.

Figured I'd check as I have a couple of Servers that I would like a lean way to backup, and this seems like the cleanest solution I've seen yet...

---

### Post by Adler on 2006-08-26
kencoe,

***If*** you think that you have some type of brain disfunction, I'm beyond any help.

For the last couple of days -- since the issue with Xorg -- I've been researching what seems to be out there. I've been looking @ g4l, g4u, sbackup, systemresecuecd, rsync, etc., etc.

Commands lines work, but at this point I want to basically clone my workstation then run a chron job. Most of what I've seen dates back years.

BTW, Noron Ghost still doesn't work w/ Linux and I'm looking for a complete GUI guided type of Live Cd / Install. 

Revive me when you can!

Adler

BTW -- I just had to edit this. I'm making CD coasters out here making ISO boot disks in my search. I forgot to mention that.

---

### Post by p.i.m.p on 2006-08-27
it doesnt work... it even includes files excluded with --exclude :( any ideas? i tried putting / at the end still doesnt work... :((

---

### Post by gmccague on 2006-08-29
> **bionnaki said:**
> in [this](http://www.ubuntuforums.org/showthread.php?t=85246) user frenkel suggests spliting up the backup. 

Can anyone confirm this?
I'd like to split my backup to 4 gigs each
to fit onto dvd-r.

Here's what you do. Go out and buy a nice 300GB IDE harddrive and USB2 cannister from your local retailer. My favorite in this regard is [http://www.ncix.com/](http://www.ncix.com/). You should be able to get away with less than $150 for both bits. You don't need high end here as it is just a backup device. 

Once you have the drive hook it up to your system. You'll find information on how to do this at [https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html)

Now I recommend that you create a mount point called "backup" that points to your fancy new drive. 

You want to keep the files on the new backup harddrive you purchased but that is never enough. Take it from me. 

Don't worry about the harddrive if you already have enough space on your system to store a copy of your backup. Unfortunately I have not yet found a tool for backing directly up to DVD yet. 

The next step would be to preserve your important files (like your music library) in 4GB chunks. 

The command I recommend for this would be:

tar -cjvp /home/<your home directory>/music/ | split -b 4024m - /mount/backup/music.tar.bz2

The above command will create a number of files with names such as music.tar.bz2aa, music.tar.bz2ab, etc.

Burn the files created with the above command to DVD! Ubuntu is slick for drag and drop in this regard. 

I wish it was easier to backup my data to DVD as I would do it more often. With this method you're backups are never really that up to date. 

Don't forget to test the above and make sure it works!

---

### Post by LotsOfPhil on 2006-08-29
> **p.i.m.p said:**
> it doesnt work... it even includes files excluded with --exclude :( any ideas? i tried putting / at the end still doesnt work... :((

try putting an asterisk in there.
If you want to exclude /windows/ProgramBackups then use

 --exclude=/windows/ProgramBackups/*

---

### Post by fstab on 2006-08-30
I accidentally filled up my Ubuntu installation with MythTV (/dev/hda4).  Things were not good.  So, I copied my Ubuntu backup that I created using the instructions at the start of this thread to a new partition (/dev/hda1).

Everything runs okay, but Ubuntu thinks my root filesystem is on /dev/hda4 when I know for sure it's on /dev/hda1.  Look at the output of the mount command after mounting /dev/hda1 to /mnt/hda1: 

sh-3.1$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4              26G  6.3G   18G  26% /
varrun                252M   68K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  140K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/hda1              26G  6.3G   18G  26% /mnt/hda1

If I make a file on / it shows up in /mnt/hda1.  

When I mount my old Ubunut partition on /dev/hda4 to /mnt/hda4:

sh-3.1$ sudo mount /dev/hda4 /mnt/hda4
sh-3.1$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4              26G  6.3G   18G  26% /
varrun                252M   68K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  140K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/hda1              26G  6.3G   18G  26% /mnt/hda1
/dev/hda4              23G   22G     0 100% /mnt/hda4
sh-3.1$

It shows that /dev/hda4 is not /.  How can I make the mount command say that / is mounted on /dev/hda1?

---

### Post by Antonlacon on 2006-08-30
> I have seen a few people ask about resized or moved partitions. If you re-install and have /home (for instance) now on a second drive, wouldn't the backup just transparently use the mounted partition as the old sub-dir? wouldn't you just need to copy your new /etc/fstab before the restore, and then move it back over after completion?


Correct, just edit the fstab to reflect the changes and have all partitions mounted before rolling out the / tarball.

> Also, any problems with this method and saving backup to a different dir? I would really like to create them in, say, /var/backups.

Meaning create the tarball anywhere you want? Yes. Simply add the directory to the filename,```
 tar -cvzpf /var/backups/backup.tar.gz --big-list-of-excludes-here /

```
> For the last couple of days -- since the issue with Xorg -- I've been researching what seems to be out there. I've been looking @ g4l, g4u, sbackup, systemresecuecd, rsync, etc., etc.

Commands lines work, but at this point I want to basically clone my workstation then run a chron job. Most of what I've seen dates back years.


What's the purpose of the cron job? Cloning a drive to a system image is very simple from a livecd, and I'm not sure how you'd interact with the gui from a cron. ```
 dd if=/dev/hda | gzip -c > drive-backup.img 
```should take care of it.  dd will image the entire drive, including free space, hence the compression.  Zeroing the freespace will typically result in a smaller image.

```
dd if=/dev/zero of=/tmp/delete.me && rm /tmp/delete.me
```

Note: the drive being imaged cannot be the same drive holding the image... Unless you only imaged a partition and were saving to a different one.

> it doesnt work... it even includes files excluded with --exclude  any ideas? i tried putting / at the end still doesnt work...

Post what the command being entered is rather than it doesn't work.

---

### Post by Adler on 2006-08-30
> What's the purpose of the cron job? Cloning a drive to a system image is very simple from a livecd, and I'm not sure how you'd interact with the gui from a cron.

Antonlacon,

What Live CD are you using and the app to clone a system. I'd like to run a cron job to back-up filles thate were altered versus doing a complete clone that would certainly take more time. But, at this point I'd could just run the machine overnight whenever I wanted to clone the system.

Any comments would be appreciated. 

Adler

---

### Post by Antonlacon on 2006-08-30
A Kubuntu livecd.  The command is dd.  Just change the above command to reflect your hard drive if it isn't /dev/hda.  If you're deadset for a gui, there is partimage but I haven't used it.

Incremental backups like the cron job idea are more so a job for rsync or unison rather than dd.

---

### Post by kencoe on 2006-08-30
Thanks AntonLacon,

Thought that was the case, but somehow got it all mucked up in the cranium. 

B.T.W.
> **Antonlacon said:**
> ... --big-list-of-excludes-here /


Nice touch.

---

### Post by seelk on 2006-08-30
> **p.i.m.p said:**
> it doesnt work... it even includes files excluded with --exclude :( any ideas? i tried putting / at the end still doesnt work... :((

When this happened to me I made sure I did a 'sudo su'.  As the HOWTO mentions make sure you are completely root before backing/restoring your system.

---

### Post by chrisccoulson on 2006-09-11
To the original poster:

I used your method to archive my system at the weekend, for the purpose of moving it to another partition. I excluded the virtual folders /sys, /proc and /dev.

When I rebooted the system, I found that my network interfaces were not coming up automatically, including the loopback interface. This was causing a long pause logging in to GNOME.

After much time debugging yesterday, I found my problem was caused by failing to mount virtual filesystems in to /var/run and /var/lock. This was due to me including the contents of these folders in my archive. After clearing them out using the live CD, all seemed to work ok.

Has anyone else had this problem?

When I next create a backup, I shall exclude /var/run and /var/lock from my archive.

---

### Post by guyvdb on 2006-09-15
This works great. I corrupted my system with mondo, and the old howto didnt work, this one does; thanks

---

### Post by rlynch on 2006-09-26
thanks for the how-to, backing up now

---

### Post by baytuni on 2006-11-14
I think I've forgot to exclude the "sys" directory when I did the backup and facing with a write error problem while extracting "sys" directory. what can i do about that. Is there anyway to delete sys directory from archive

---

### Post by StarryTripper on 2006-11-16
I've used this backup method to migrate two Ubuntu Edgy installations to a software raid1 mirror.

I searched high and low to try to figure how to do the migration, and just couldn't get it figured out.

I downloaded the alternate CD and installed a fresh Edgy on two additional (and identical to one another) hard drives using software raid.  The trick is do not reboot from the installation until the raid devices have finished sync'ing.  You can check by doing an Alt+F2 to another session and running ```
cat /proc/mdstat
```.  Reboot only after everything has sync'ed.

At that point I then booted to the regular "Live" CD, installed mdadm and did a ```
mdadm --assemble --scan
``` then mounted the newly created raid devices.  I then mounted the partition with my origanal installtion as  I want to mirror as READ ONLY (if you don't, you'll get an error message on the last file about it being changed since last read or something, mounting read only takes care of it) and used the backup method to create a tar file on the software mirror.  I excluded some additional files, like /etc/fstab, /etc/mdadm/mdadm.conf, initrd, initrd.img, vmlinuz and my /home directory (I moved that separately to another raid devices, my original installation it was part of root) and /dev (I know there's some discussion about this, but in the case of moving to software raid I think you need the /dev that has the md devices, my installation I was migrating from did not have the md devices so I did not want to bring that over to the mirror in fear that it would then fail to work).

I am sure there are more "correct" ways to migrate to raid, like the missing drive method that confused the hell out of me.  And I guess that cp or rsync with the proper options would have saved some time over compressing, then decompressing the data.  But since this method is tried and tested I figured I'd go with it.

I have just done tis yesterday and have yet to test if the installer properly configured GRUB on both drives, so that it will boot in the event of a failure.  I hope it did!

---

### Post by finite9 on 2006-11-16
Having a 'system' backup is one thing, and if I used that I would only back up to another HDD as and when needed, like before major upgrade, or before performing something 'dangerous'.

Having a true incremental backup system is another thing entirely.  I do yearly, monthly and weekly backups and plan to use rsync for dailies.  If my system borks unexpectedly, I re-install using CD (I have my own guide that explains how to very rapidly re-install everything I use, which I cut/paste into a terminal to apt-get it all), then I apply yearly/monthly/weekly backup.  There is nothing more important than my documents and the digital images/videos of my child.  Here is my yearly script.  other scripts require copying snar using cp -u, to snar-1, snar-2 etc:

```
#!/bin/sh
rm -f /var/log/snar*
# important: 
# cannot use --exclude as this breaks incrementals.
# cannot use -z to gzip within tar command as this is unsupported with incrementals.
# need to run as root in case there are other users in /home
echo "Archiving files..."
tar -cvPWf \
	/home/backup-level0-yearly.tar \
	--listed-incremental /var/log/snar \
		/home/finite9/ \
		'/media/hda2/Documents and Settings/All Users/Documents/My Pictures/' \
		'/media/hda2/Documents and Settings/user2/My Documents/' \
		'/media/hda2/Documents and Settings/user2/Application Data/cbt/' \
		'/media/hda2/Documents and Settings/user2/Application Data/GnuPG/' \
		'/media/hda2/Documents and Settings/user2/Application Data/Mozilla/' \
		'/media/hda2/Documents and Settings/user2/Application Data/Thunderbird/' \
			> /home/backup-level0-yearly.tar.log
echo "Compressing archive with gzip..."
gzip -v /home/backup-level0-yearly.tar

## move file to my home so I can GPG it
mv /home/backup-level0-yearly.tar.gz /home/andrew/backup-level0-yearly.tgz
mv /home/backup-level0-yearly.tar.log /home/finite9/
chown finite9:finite9 /home/finite9/backup-level0-yearly.tgz
chown finite9:finite9 /home/finite9/backup-level0-yearly.tar.log

## encrypt the tarball
echo "Encrypting archive with GnuPG..."
gpg -r finite9@finite9.net -o /home/finite9/backup-level0-yearly.tgz.gpg -ve /home/finite9/backup-level0-yearly.tgz

## remove tgz file as GPG doesn't do this automatically
rm -f /home/finite9/backup-level0-yearly.tgz

## root gpg'd file so change ownership to me
chown finite9:finite9 /home/finite9/backup-level0-yearly.tgz.gpg

## use split to split a multiGIG file into manageable 1GB parts.
echo "Splitting encrypted archive into 1GB chunks..."
cd /home/finite9
split -b 1073741824 /home/finite9/backup-level0-yearly.tgz.gpg
chown andrew:andrew /home/finite9/xa*

## remove GPG file after split
rm -f /home/finite9/backup-level0-yearly.tgz.gpg

```

---

### Post by sparty2809 on 2006-12-12
Will this work with RAID1?

Also, if I want to take the backup and install it on a server with different hardware, will this work?

---

### Post by Robertjm on 2006-12-18
Hi all,

I'm trying to use TAR to backup my system onto DVD-sized chunks, but am unsure on the syntax. I've pasted below the copy of my backup.sh file. I ran it earlier without a split in there forgetting about the 4Gb size limitation in FAT32 partitions (my external drive).

So now I'm trying to add the |SPLIT in there, but am not sure if the syntax is correct.

Here it is:

tar cvpjf | split -b 4024m /media/SEA_DISK/BACKUPS/20061217backup.tar.bz2 --exclude=/wine --exclude=/proc --exclude=/lost+found --exclude=/media/SEA_DISK/BACKUPS/20061217backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/temp --exclude=/tmp --exclude=/dev --exclude=/home/.Trash-root --exclude=/home/robertjm/.Trash --exclude=/media --exclude=/var/cache --exclude=/var/tmp /

---

### Post by finite9 on 2006-12-18
Dont think that will work as your passing all the TAR args as args to split.  You have included split too early in the script.  You should add "| split -b 4024m..." to the end of the entire tar command.

---

### Post by Robertjm on 2006-12-18
Thanks for that. It didn't look entirely correct, but I'd found an example as I wrote it on another forum.  Perhaps the HOWTO back up needs to be amended for that to include a section on spliiting.

Robert

> **finite9 said:**
> Dont think that will work as your passing all the TAR args as args to split.  You have included split too early in the script.  You should add "| split -b 4024m..." to the end of the entire tar command.

---

### Post by Furox on 2006-12-24
great how - to very simple,
just one question if i restore a full system, will it delete other things i have installed
for example
say i installed flash & blender 3d
then did backup 
and then after installed a kde app ( but the installation goes horribly wrong and kde starts interefering )
when i restore will the kde stuff ive installed be deleted and the system will completly restore back to the backup i made ?

thanks

---

### Post by FLPCGuy on 2006-12-24
I've read this entire backup forum and learned a little bit about a lot of backup techniques and gathered a lot of great reference links. There are certainly a lot of ways to go.  But it seems to me a few fundamentals have been assumed or ignored, from the perspective of new users.  

First, a lot of the problems people have had here seem to be the result of trying to restore a backup to a system with different partitions and mount points.  I haven't seen anyone mention the importance of knowing, documenting, and reproducing the exact same mount points on the system to which a backup will be restored.  I'm thinking there may be a key configuration file that should be stored as data outside the backup as a reference to prepare a new system for the restore.

Secondly, if the reproducing part can be overcome by editing the /etc/fstab file, then perhaps that is worth a more detailed discussion.  Third, little mention seems to be made of permissions which must certainly have an impact on what you can backup and what you can't.  There is a folder in my Edgy 6.10 /var folder called backups and root can't even access this folder.  I'm not sure why. 

Finally, as a long-time system admin (Novell then Windows) responsible for server backups, one of the most basic determinations I've always had to make before backing up is whether I'm backing up system information or unique user data.  User data is independent of any particular system while system data is independent of user data.  So it makes sense to split backups by these fundamental differences considering that restores will likely be either a system restore (perhaps for another user) or a personal data restore on a different system as often as restoring both to the original or an identical piece of hardware.

 I haven't yet figured out which directories are vital to the system, which contain temporary system data, and where applications install. Do they add anything in my home directory structure (complicating the separation of my files from system files)?  

Perhaps someone could review some of their favorite techniques or backup code examples with these issues in mind.

---

### Post by Furox on 2006-12-25
that is a good point you have bought up, and clearly seeing that you have experience in the backup ~fundamentals~ maybe you could shed some light into restoring a system to a certain point, (other than reinstalling Ubuntu and installing all the programs again)

Thanks

---

### Post by FLPCGuy on 2006-12-25
> **Furox said:**
> that is a good point you have bought up, and clearly seeing that you have experience in the backup ~fundamentals~ maybe you could shed some light into restoring a system to a certain point, (other than reinstalling Ubuntu and installing all the programs again)

Thanks

I didn't mean to convey any sense of authority with regard to Linux.  I'm a new user too.  From what I've read the /etc/fstab file seems to contain valuable info.
Here's a portion of mine with UUID abbreviated:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb8
UUID=a55a59... /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=1A3....  /media/hda1   vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=B07... /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=0C6...  /media/hdb2  vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=328a... /media/hdb6     ext3    defaults        0       2
# /dev/hdb7
UUID=1e3... none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Looking at the first few lines, my root / is mounted on hdb8 an ext3 formatted partition on hdb (2nd drive).  A newer version of Windows was on the first partition of this drive (NTFS), but there is also a vfat partiton (hdb2) which may contain another version of Windoze, another Linux partition (hdb6), a swap partition (hdb7) one of two actually but the one on hdb5 isn't showing.  This is a fairly complex configuration with lots of places for various OS installations.  

There can only be four primary partitions, but one of those may be an extended partition so there can be any number of divisions on the drive since Linux doesn't use a letter assignment.  You might want to play with the GNOME Partition Editor (you can add it to your installed Ubuntu or run it from the live CD) to see a graphical view of your drive that is a lot easier to understand.

I would copy the info in my /etc/fstab file and document what OS is mounted where and the size of each partition (not shown in fstab) so I could reproduce the same partitions and mount points if I need to replace my drive and restore from backup.  It takes some contortions to get GParted to number the partitions the way you might expect but if you have built them in order, you shouldn't have to edit the fstab info from your backup to have things where they belong.  

There are several backup utils with features like full and incremental backup (differential) which makes frequent backups less of a chore.  If you start by installing from a distro CD, then you really only need to backup what's different. 

The other line of reasoning is that drive space, DVD media, and processing power is cheap so there is no longer a need for incremental backups and restores of personal systems.   It is up to you.  In the worst case scenario, you would have to restore the last full backup plus five or six incremental backups to get back to a known good point.

Personally, I've always felt tape was a waste of time when you can get another 8 ms access time hard drive for about the same money.  I've spent too many hours waiting for a tape to crawl along to restore one tiny file some big shot deleted without thinking.  Why put yourself in that position if you don't have to?

Also, I avoid any OS specific or proprietary backup utility if possible, especially for data since I may want to restore that data to an entirely different OS in the future long after the backup program has been forgotten.  Never rely entirely upon Windows backup for personal data.  That program changes format with each new M$ version rendering all your previous backups useless [thanks Bill!]. You are better off using Zip, tar or some other OS independent method that has been around forever and isn't going away anytime soon.

That's about all I can tell you at this point.  Perhaps a Linux guru could expand on this from here and correct me.

---

### Post by morphet on 2007-01-05
Short and sweet. Thanks!

---

### Post by Balaam's Miracle on 2007-01-12
In the hope that nobody objects, i would like to point to a script that kebes and i have been working on.
You can read about it here: [http://ubuntuforums.org/showthread.php?p=2004006#post2004006](http://ubuntuforums.org/showthread.php?p=2004006#post2004006)

This script is intended to make a backup of a collection of files, like an MP3 collection or a large collection of images to name but a few.
The backup is written without additional compression so that the files can be read from any other OS without the need for decompression tools.

Please note that the script was not intended to be used to make a full system backup!

I hope someone will find this script useful.

---

### Post by midia on 2007-01-27
Consider emptying out the users' ".Trash" directory and the root ".Trash" directory before doing a system backup.

---

### Post by kpagpa on 2007-03-19
Hi Everyone,

I backed up my system using the method explained in this article, and at a certain point I had to resort to the backup because everything went horribly wrong!

I tried to install according to the instructions, and it restored the directories I had backed up.  When I tried to create the directories I hadn't backed up,

mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
etc...

it wouldn't let me do it, saying that those directories already existed.  When I rebooted, it wouldn't mount the file system because it said that it wasn't recognizable.  I couldn't use the system at all, and had to completely reinstall from the live CD. 

Has anyone else had this problem, and what is the workaround?

Thanks for your help.

---

### Post by Jason W on 2007-04-22
I've used this method and it works flawlessly.  I am using it as well for Gentoo, which makes for an easy install.    Gives a good known base to start with.  The same with Debian or Ubuntu, it basically lets you start with a good known install and configuration and saves much time.  Thanks for the how to.

---

### Post by bayvista on 2007-04-22
Sorry, Guys. I've lost the plot.

Which article are we talking about as the Elixir of all backups?

---

### Post by hihihi on 2007-05-03
hello,
thanks a lot for this how to.
its very useful.
the only thing i cannot figure out right now is how to overwrite from archive all the backuped folders. the following happens: when extracting for example folder /X it will not overwrite the whole folder, but instead the files inside the folder. that means that if on backup-time folder /X contains file y.doc and later, when things went wrong folder /X contains y.doc and z.doc
after extracting z.doc is still present.
i want to overwrite the folders completely for clean reasons. anybody knows how?
thanks a lot,

---

### Post by webdr on 2007-05-03
;)  ok, and REMEMBER to unlpug any external drives that you don't want included in the backup, or be sure to exclude them.

---

### Post by hihihi on 2007-05-04
--exclude=/media

---

### Post by splitsch on 2007-05-04
Hello!
An other way is to use partimage.
I made an howto (in french!). You can find it here: [partimage](http://splitsch.blog-libre.fr/technologies/sauvegarder-et-restaurer-son-systeme-gratuitement-via-partimage.html)

Bye, and thanks for the tips !

---

### Post by Fraoch on 2007-05-16
This worked quite well for me.  bz2 compression really squeezed a lot - I compressed a 9.3 GB install into 6.6 GB.  This took about 2 hours.

However, there's a big drawback IMHO.  When your system changes, you have to delete the old backup and make a new one from scratch, taking up those 2 hours each time (more as your system grows).  I tried this using rcync -azP --delete, even reusing the --exclude flags in this tutorial.  It was even faster, about 1 hour, but compression wasn't nearly as good - it compressed down to 9.2 GB. :P

But the advantage is, the next time I do a backup, only changed and deleted files get moved, so it will be very fast.  No point in copying and recompressing files that haven't changed!  I just verified this - although my system hasn't changed much in that hour since I made the backup, re-running the command took 5 minutes.

rsync even has a --backup option that allows you to keep multiple backups.  I haven't thoroughly investigated this yet but it may be useful.  However I will use up that 40 GB backup partition I have very quickly if I do this.

---

### Post by southernman on 2007-06-10
Have a hard disk that testdisk shows some slight problem with. Using this method of backup, can I setup a new hard disk, with the same parttions and untar the backup to it... leaving me the same working system I have? - minus the disk geometry problems of course.

---

### Post by Thorun on 2007-06-11
as more people mentioned - i did try this backup (at top page one) and restore. 
But the system wouldn't let me create the folders i have excluded in the backup (because the folders allready existed).

I did type:
```
tar cvpjf backup01.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup01.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/media /
```
And the backup did work wery well.

Now i have just tried to restore my system because i tried to install a bunch of programs - and everything went wrong (hence the restore). 
But now i still see the shortcuts, the same stuff on my desktop and all other old stuff i wanted to  be gone.

Explanation:
At the time i created the backup i had file X in some folders. Now the files is newer - called Y. When i restored my system - i wanted to get rid of the Y-files and only wanted the X-files (hehe) to get back. But now my system has both X and Y files in one huge mess.

For restore i did type:
```
tar xvpjf backup01.tar.bz2 -C /
mkdir proc
#error - couldn't make the folder as it allready exists
mkdir mnt 
#same error 

```
and so on...


Is it possibly to delete the partition with all the Y-files and restore my backup - so none of my new stuff is saved? And how?
And why did the excluded folders still exist?



Edit:
Because the strong addiction to Windows-like programs (i allways use PQ Partition Magic v8.0 for partition stuff, and i'm wery much used to Northon Ghost 2003 to make system backups - which never have failed me) I think that what i'm asking for is not the graphical interface of Northon Ghost2003, but a program that do the stuff in the way. Eg. a program that just backups a whole partition or harddisk and when restore is needed, it just overwrites everything with the old backup. No left Y-files (see above).


Edit 2:
Now i have tried to re-install ubuntu from the Live CD and then run the backup with the restore-option on page 1. Now the system won't even start. :(

---

### Post by diskotek on 2007-07-19
is it better to have and "/home" in another partition? it can also works?

---

### Post by Robertjm on 2007-07-19
The big advantage of having /home in a separate partition is that if/when it comes time to upgrade or change your distro you can do a clean install by wiping all your partitions except for /home (or any other special partitions you created for your personal data/installations).

Robert

---

### Post by diskotek on 2007-07-23
thank you for reply. i think i need that

---

### Post by pointzero on 2007-08-04
> **A-star said:**
> 
WARNING: this will overwrite every single file on your partition with the one in the archive!

Just so I understand the way this works properly.  When it overwrites the files does it also delete anything you had installed after the backup.  So say I make a backup and install a bunch of software I didn't like afterwards.  Then used this method, does it erase everything post backup?

:popcorn:

---

### Post by Robertjm on 2007-08-04
Yes that would happen. Just make ABSOLUTELY sure that you don't have any data files on that partition you do want (i.e.: email files, downloads, etc). Cause its gonna get toasted too!!

Robert

---

### Post by mikeize on 2007-09-15
I've followed the directions at the beginning of this thread, and left it running overnight.  Everything seemed to be running fine when I went to bed, but when I checked the terminal just now, the last line said:

tar: Error exit delayed from previous errors

Can someone tell me what this means, or how to find out?  Does this mean my backup is corrupted?  I plan to use it for a reinstall, so I need to know that it will work.  Thanks!

-mike

---

### Post by southernman on 2007-09-15
> **mikeize said:**
> I've followed the directions at the beginning of this thread, and left it running overnight.  Everything seemed to be running fine when I went to bed, but when I checked the terminal just now, the last line said:

tar: Error exit delayed from previous errors

Can someone tell me what this means, or how to find out?  Does this mean my backup is corrupted?  I plan to use it for a reinstall, so I need to know that it will work.  Thanks!

-mike

This error is noted in the howto, Mike...

> EDIT2:
At the end of the process you might get a message along the lines of 'tar: Error exit delayed from previous errors' or something, but in most cases you can just ignore that.

Can't say why the error occurs, but it's been my experience to not be a problem and the restored files work as expected. YMMV

---

### Post by mikeize on 2007-09-15
heh heh...  missed that part!  Thanks.  Just want to be reasonably sure.

-mike

---

### Post by autowaaagh on 2007-09-21
I have recently installed ubuntu on an older IDE harddrive i have which is starting to screw up on me.  I decided to go out and get a fancy new SATA drive since my MoBo has only a few IDE slots, but plenty of SATA slots.

I was wondering what I should expect if i backed up all my stuff the way that is described at the beg of this thread, re-ran the install using my SATA drive as the install point, and then using this backup file.

---

### Post by natehatewindows on 2007-11-29
how would this work if you have a separate /home?

---

### Post by shadowtrk on 2007-12-09
Hi everyone,
Just wanted to drop a note saying Thanks for the good work im running a backup as I write this. Just as a Note Make sure u clean out ur Trash and any other folders and files you dont want backed up. I have had to restart my backup after noticeing that .trash had 2gigs of old data

lol

---

### Post by Robertjm on 2007-12-09
I've explain based upon my own Ubuntu installation.

Over 18 months ago I decided to switch from Windows to Linux. At the time of installing Linux I created multiple partitions on one hard drive. You can look over the web for all sorts of recommendations of how/why to partition so I won't list any here, except one.

As said earlier, its a good idea for having your /home on a different partition. When you install Linux it will ask you if you want to partition your drive. Along with that you will have the option of formatting any partitions. Formatting as in wiping the slate clean. Needless to say, with wiping it destroys data. 

Many people advocate doing a clean install, rather than an upgrade when going from one version to another. The benefits of that are legacy files no longer needed are cleared, as well as any imcompatibilites that might exist should we upgrade some programs, but not others that are dependencies of the newer versions. If your /home directory is part of one big partition there is no way to keep that formatted while reformatting the rest of the drive.

I started with Dapper Drake. Then went to Feisty Fawn and now last week went to Gutsy Gibbon. Each time I did a complete reinstall, reformatting all my partitions except for the three that I have data on, /home /home/parallels and /home/photos. Had those simply been folders on one big partition rather than multiple partifitions, I would have had to spend a ton of time backing it all up and then copying it to the new installation just to get back to where I was, not to mention the possibility of losing it all in the process!

To give you a better idea of the whole partitioning thing, think of the /home as bieng the equivilent of the Application Data folder (I think that's what its called) in Windows. That's where stuff is centrally located. Rather than keep data in a data folder with the program's folder its put elsewhere.

The beauty is that if you leave it where the program's installation process puts it, it will STILL be there when you install the new version through the upgrade to the new OS.

Case in point. When I went to Gutsy I turn it on and my desktop had all the icons I'd added since installing Feisty AND all my email was in my Thunderbird Inbox when launching the program!!

Hope that helps.

And to add to what shadowtrk posted, you should tell your backup software to ignore any cache or tmp directories. Those contain files which will just be rewritten when the programs run. Can be several gigs there, especially in cache, if you use your programs for editing photos or videos!

Robert

> **natehatewindows said:**
> how would this work if you have a separate /home?

---

### Post by bayvista on 2007-12-10
Good suggestion. 

I did something similar when I moved from Windows to Ubuntu. When it asks you to format the partitions, it identifies your Windows partition. You can keep this and just add extra partitions for Ubuntu. U is clever enough to recognize the partitions it needs and will install on these, leaving your Windows untouched. Now here's the cracker. 

When you boot up Ubuntu, it automatically mounts all partitions including Windows! So now you can access all your Windows files.

I keep all my files in my old Windows system and only use the Home directory for work space. Even my Email (Thunderbird) saves all my stuff in 'My Documents' (the Windows general document folder.

Remember, the guys that developed Ubuntu thought of these things first. It's just a little difficult finding the information.

Good Ubuntuing!!

Dave

---

### Post by eyeorg on 2008-05-09
I am in need of some serious help.  I performed the backup and the restore as directed (first installing Ubuntu 7.10) on the server then performing the restore.

I am moving from an old server (maybe ubuntu 5x) with a single hard drive to a brand new server with a Raid 5 configuration (4 HD's). 

After performing the restore now when I boot the server I get the following error message.

> 
Alert! /dev/sda1 does not exist.  Dropping to a shell.

BusyBox V1.00 - Pre10
/bin/sh: Can't access tty; job control turned off


And now I cant seem to do anything.  I am VERY new to Ubuntu and not sure of anything.  Any help would be appreciated.

I ran fdisk -l /dev/sda after finding the install disk and a prompt and received this(not sure if it helps)
> 
/dev/sda1 * - linux
/dev/sda2   - extended
/dev/sda5   - linux swap


---

### Post by AlienM1nd on 2008-05-10
> **bionnaki said:**
> I just realized an entire system backup from / would be about 26 gigs. I'd like to have everything on DVD-R, so what do you think would be the best way to divide the backup? thanks again!

dar -c /backup/folder -s 700M -z5 -R /

---

### Post by eyeorg on 2008-05-23
HELP ANYONE??  This is why I love ubuntu!

---

### Post by chaanakya_chiraag on 2009-01-18
I was just wondering if it is normal to lose internet while the system is being backed up.  It came back afterwards, but while it was creating the archive, I lost internet access.

---

### Post by jeggerleg on 2009-01-31
Hi

I have successfully followed the instructions in this thread to backup my Ubuntu system. I have ended up with a file of 13.5gb - now the problem:
I am trying to copy this file to an external hard disc (Western Digital) after about 4gb Ubuntu throws up an error and tells me the file is too large to copy.
Any ideas?

---

### Post by PoPpiLLs on 2009-02-01
jeggerleg what file system is on your external hard disc if it fat32 it has a 4gb file size limit.

---

### Post by Lod on 2009-02-01
In addition to the Fat32 remark, if I remember correctly Nautilus had problems handling large files itself as well. If your external hard drive is not Fat32 you might try to copy the file with the commandline.

---

### Post by Tom_T on 2009-02-02
Am I better backing up using this method or using sbackup_0.10.5 ??

How about backing up an entire drive with XP as a dual boot ?? What is the best solution for that ?

Thanks

---

### Post by jeggerleg on 2009-02-02
> **PoPpiLLs said:**
> jeggerleg what file system is on your external hard disc if it fat32 it has a 4gb file size limit.


Yes,thank you - in 17 years of using Windows either I have never come across the problem or if I've read of that limit I've forgotten. I've now formatted the disc to ntfs using gparted and no longer have that restriction. I originally reformatted it to the Linux file system but that created even more problems.

---

### Post by Rodney9 on 2009-02-02
I have a 120Gb internal hard drive with Ubuntu 8.10 and a external 320Gb for back ups.
I used -   > tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /
and I end up with a 8Gb file, it is to big for burning to dvd and my 320Gb backup external hard drive will not copy more then 4Gb at once, if I partition the drive I will lose 100's Gb's of backups.
I tried G4L, Ghost for Linux, but it will see the external hard drive or the keyboard, but never the two together.
Does Clonzilla or Fog make a image that will fit across two or more cd/dvds ? or is there something better ?

PS I tried > # tar cvpzf -M --tape-length=307200 file=backup.tgz largefile.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
but get - > tar: Cannot use multi-volume compressed archives

---

### Post by chriscash on 2009-02-03
thanks bro!
now, i don't have to worry about my files,:D

---

### Post by jeggerleg on 2009-02-05
> **Rodney9 said:**
> I have a 120Gb internal hard drive with Ubuntu 8.10 and a external 320Gb for back ups.
I used -   
and I end up with a 8Gb file, it is to big for burning to dvd and my 320Gb backup external hard drive will not copy more then 4Gb at once, if I partition the drive I will lose 100's Gb's of backups.-


Can't you partition the drive and format the new partition as ntfs leaving the 100gb alone?

---

### Post by josheby on 2009-02-05
OK... I am new to ubuntu and linux all together for that matter.  I like this idea and think it could be exactly what I am looking for.

Now say I setup and run backups like this and create tarballs of my system...

If my system were to become messed up to the point I cannot boot... for instance... a hard drive dies or the OS gets royal messed up (or I mess it up because im new at this...) what all is involved in putting it back?

1) Can I boot to a live CD... mount the drive volume that my install is on, mount my network drive where my backups are and then just copy the tarball over and extract it?  Once that is done reboot without the live disk and it should load right up?

2) If #1 doesn't work, would I be able to do a fresh install of ubuntu... and then mount my backup drive and perform the restore at that point with all of my installed software and everything in tact?

Sorry if these seem like simple questions.  I have only begun to scratch the surface of ubuntu/linux.  I thank anyone and everyone in advance for the help!

---

### Post by slyman1973 on 2009-04-01
Thanks for the howto! I've had to add some folders in the /media listing that are mounts to samba network folders.

```
tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/media/installation\040programs --exclude=/media/main --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /
```

:p

---

### Post by petteriIII on 2009-04-02
A-star, you said in your first post: 
EDIT : kvidell suggests below we also exclude the /dev directory. I have other evidence that says it is very unwise to do so though.

Will you elaborate, please ? I have made few months of full-day hard work trying to hone this this method of backup, and there is something wrong with it.  I will not include my findings at this moment for the fear that I would influence your thoughts.

---

### Post by Cx_Jx on 2009-04-08
> **kpagpa said:**
> Hi Everyone,

I backed up my system using the method explained in this article, and at a certain point I had to resort to the backup because everything went horribly wrong!

I tried to install according to the instructions, and it restored the directories I had backed up.  When I tried to create the directories I hadn't backed up,

mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys
etc...

it wouldn't let me do it, saying that those directories already existed.  When I rebooted, it wouldn't mount the file system because it said that it wasn't recognizable.  I couldn't use the system at all, and had to completely reinstall from the live CD. 

Has anyone else had this problem, and what is the workaround?

Thanks for your help.

I have the same issue...

the /lost+found /proc /sys /mnt directories persisted after the restore (tar xpvzf...) and could not be created using mkdir as instructed in the tutorial... same error "directory already exist"

Upon reboot I get a boot fail.
Same applies if I try to restore using a new install -- using version 8.04 LTS

I see another post experiencing similar problems but no replies.

Anybody have any suggestions.

Thanks.

Chris

After digging around, this might be relevant.  I am restoring my working installation onto a new hard disk in order to try new things... and to verify the effectiveness of the backup :)
...I am suspecting there is an issue created by the different UUID in /etc/fstab and /boot/grub/menu.lst in the back up files not agreeing with the actual UUID of the new hdd that were created when the OS was installed freshly onto that hdd.  Any comments?

---

### Post by v_dragon on 2009-04-14
hi!
This is a great how too
I have a question for you all that is kinda related.
Been using Ubuntu exclusively for some time now but...i need to now dual boot to winblows. I have a few modifications to make to my hardware anyway (adding a new dvdburner, different cpu heatsink...etc) 

Sooo...will this how too apply and/or play nice with installing windows, then running the ubuntu install to setup the partitions, OS and grub and all that then run the restore? better solution?? ,, I want to do a full backup and restore of the Ubuntu system.

thanks!
(^_^)

---

### Post by funky_uncle on 2009-04-20
I can't get the "--exclude" command to work. Here is what I enter in the terminal:```
sudo tar zcvfp /tmp/funkybackup.tgz /home/funky --exclude=/Music --exclude=/incoming --exclude=/Themes --exclude=/divLinux

```but it still copies the folders I try to exclude. I have tried without the "=" as I saw done in another thread. Same depressing result. What am I doing wrong? I read the command over and over and I can't find the fault.

---

### Post by funky_uncle on 2009-04-20
I figured it out: I had to type out the whole path of the directories I wanted to exclude, like "/home/funky/Music" instead of just "/Music".

And everything goes fine until this:```
tar: Error exit delayed from previous errors
```so... I dunno?

---

### Post by funky_uncle on 2009-04-20
And what the heck does ```
Cannot stat: No such file or directory

```mean?

---

### Post by funky_uncle on 2009-04-24
...bump?

---

### Post by majed on 2009-04-24
funky_uncle,

these errors r so not informative.. they could be bcz u r running out of space in /tmp so check that.. they could be bcz u got some spaces in the file names or paths.. use quotes for that.. if u still get the error and u r not out of space, try the following to get a more descriptive error message..

```

nohup [command] nohup.out

```

any output messages would then be written in the nohup.out file..

I also recommend trying to do your backup with this command instead:

```

ls -a /home/funky | grep -v "." | grep -v ".." | grep -v "Music" | grep -v "incoming" | grep -v "divLinux" | xargs sudo tar cvpzf /tmp/funkybackup.tar.gz  

```
good luck!

---

### Post by finippino on 2009-04-24
I have a Asus eeepc 1000HA with dual boot of xp and eeeBuntu 8.10 remix installed.  So last night I realized that Ubuntu 9.04 was just released so I downloaded the Netbook Remix version and installed.  Before I did, I created using this back up process which has worked for me many times.  So I began to install the new Ubuntu 9.04 but this time I resized the partitions.  After some time of playing with Ubuntu, I found some bugs which I knew I could not handle messing with and realized then why I should always wait before installing a new release.  So I thought I have a back up of my previous install of eeeBuntu.  Ill just reinstall it, put the partitions back to the same size and do a restore.  Well it did not go as planned.  I restored and rebooted but when I got to the grub I selected the eBuntu 8.04 from the menu and it gave me, "Error 15: File not found".  So I am thinking because I resized the partitions I pretty much screwed up Grub.  Im pretty new to linux, so are my options pretty much to start from a fresh install and reconfigure everything again or is there a solution to this?  Any help would greatly be appreciated by this noob.

Thanks

---

### Post by majed on 2009-04-25
> **finippino said:**
> I have a Asus eeepc 1000HA with dual boot of xp and eeeBuntu 8.10 remix installed.  So last night I realized that Ubuntu 9.04 was just released so I downloaded the Netbook Remix version and installed.  Before I did, I created using this back up process which has worked for me many times.  So I began to install the new Ubuntu 9.04 but this time I resized the partitions.  After some time of playing with Ubuntu, I found some bugs which I knew I could not handle messing with and realized then why I should always wait before installing a new release.  So I thought I have a back up of my previous install of eeeBuntu.  Ill just reinstall it, put the partitions back to the same size and do a restore.  Well it did not go as planned.  I restored and rebooted but when I got to the grub I selected the eBuntu 8.04 from the menu and it gave me, "Error 15: File not found".  So I am thinking because I resized the partitions I pretty much screwed up Grub.  Im pretty new to linux, so are my options pretty much to start from a fresh install and reconfigure everything again or is there a solution to this?  Any help would greatly be appreciated by this noob.

Thanks

Check this out.. 

[http://ubuntuforums.org/showpost.php?p=1879448&postcount=4](http://ubuntuforums.org/showpost.php?p=1879448&postcount=4)

I am sure this can be fixed by reconfiguring grub, but if you don't know how to reconfigure it, then u might as well just reinstall it.

Good luck!

---

### Post by funky_uncle on 2009-04-26
> **majed said:**
> funky_uncle,

these errors r so not informative.. they could be bcz u r running out of space in /tmp so check that.. they could be bcz u got some spaces in the file names or paths.. use quotes for that.. if u still get the error and u r not out of space, try the following to get a more descriptive error message..

```

nohup [command] nohup.out

```

any output messages would then be written in the nohup.out file..

I also recommend trying to do your backup with this command instead:

```

ls -a /home/funky | grep -v "." | grep -v ".." | grep -v "Music" | grep -v "incoming" | grep -v "divLinux" | xargs sudo tar cvpzf /tmp/funkybackup.tar.gz  

```
good luck!OK, trying to learn something here... I took a look at what the commands does ([http://linux.about.com/od/commands/l/blcmdl1_ls.htm](http://linux.about.com/od/commands/l/blcmdl1_ls.htm)) but I don't really understand it. ls for listing info about the files, right? But does it also build an archive of the files? I don't mind just copying and pasting the command, I just want to know what I'm doing.

---

### Post by majed on 2009-04-26
> **funky_uncle said:**
> OK, trying to learn something here... I took a look at what the commands does ([http://linux.about.com/od/commands/l/blcmdl1_ls.htm](http://linux.about.com/od/commands/l/blcmdl1_ls.htm)) but I don't really understand it. ls for listing info about the files, right? But does it also build an archive of the files? I don't mind just copying and pasting the command, I just want to know what I'm doing.

That's the right way to learn.. :)

This is the explanation of the command I suggested:

[ ls -a /home/funky ] list all the directory contents, the -a option prints along all the hidden files that r usually used by applications to store meta data and configurations..

[ | ] this is the pipe.. it will direct the output of the previous command to the next command and is here used more than once.. 

[ grep -v "." ] grep is a matching command.. used to search for text in a stream and prints only lines that contain it.. but with the v option, it does the opposite.. it hides the lines that has what u searched for..

so i guess u can now follow the rest of the command..

but wait.. i can see i made a mistake.. i should grep -v the . and .. exclusively with a regular expression to avoid excluding any files with names having a dot, but that's only under /home/funky so if u only have directories there then u should have no issue.. 

let me work on my reg exp then get back to u.. it's bee a while :)

u can certainly play with ls, pipe, and grep to learn them and get the idea behind piping.. no harm can be done if u don't include any other commands or directives like this " > ", which is save but can be dangerous..

---

### Post by majed on 2009-04-26
> **majed said:**
> 

let me work on my reg exp then get back to u.. it's bee a while :)



OK.. here goes.. i added the starting and ending anchor characters to each grep match string to make sure u only exclude these from the final list of files that would be directed to the tar command in the end..

```

ls -a /home/funky | grep -v "^.$" | grep -v "^..$" | grep -v "^Music$" | grep -v "^incoming$" | grep -v "^divLinux$" | xargs sudo tar cvpzf /tmp/funkybackup.tar.gz

```

---

### Post by funky_uncle on 2009-04-26
Whoa, this is a little over my head, I'm afraid...

I googled xargs to figure out what it is, and I'm told that *"xargs reads arguments from the standard input, delimited by blanks (which can be protected with double or single quotes or a backslash) or newlines, and executes the command (default is /bin/echo) one or more times with any initial-arguments followed by arguments read from standard input."*

Yeah, I guess that... makes sense. Somehow. Anyway, this is about as much as I understand of the command you suggested:
first, "ls" lists all the files in /home/funky,
sends that list to "grep" which decides which directories to leave out,
then the list is sent to "xargs" which does something I don't understand at all,
and then "tar" creates an archive of the files in the list.

I didn't understand the "starting and ending anchor characthers" bit. But thanks :)

---

### Post by majed on 2009-04-26
> **funky_uncle said:**
> Whoa, this is a little over my head, I'm afraid...

I googled xargs to figure out what it is, and I'm told that *"xargs reads arguments from the standard input, delimited by blanks (which can be protected with double or single quotes or a backslash) or newlines, and executes the command (default is /bin/echo) one or more times with any initial-arguments followed by arguments read from standard input."*

Yeah, I guess that... makes sense. Somehow. Anyway, this is about as much as I understand of the command you suggested:
first, "ls" lists all the files in /home/funky,
sends that list to "grep" which decides which directories to leave out,
then the list is sent to "xargs" which does something I don't understand at all,
and then "tar" creates an archive of the files in the list.

I didn't understand the "starting and ending anchor characthers" bit. But thanks :)


Yup.. u got it alright!

what xargs does is that it takes the list of files that we came up with and prints it at the end of the tar command.. similar to the pipe but in a different way :)

the "^" character denotes the beginning of a line.. 
the "$" character denotes the end of a line.. 

for example, when u grep for "funky", lines with funky or funky_uncle or unclefunky r all matches.. but when u grep for "^funky" then all lines that start with funky would match.. and when u grep for "funky$" then only lines that end with funky would match.. that's why i grepped with both start and finish anchors so u r sure that the grep works the way u want it to work, in case there are some other matches due to similar file or directory names in ur home directory..

try the command step by step to understand what it does..

try this part first: 

```
ls -a /home/funky
```

then pipe it to the next command and see what happens.. 

```
ls -a /home/funky | grep -v "^.$"
```

play around.. put the letter M instead of the dot and the directory "Music" and any other entry with an M would not show.. u know..

this is not about the backup/restore thing though.. its getting to be a command line tutorial :)

I hope no one hates that!

Good luck!

---

### Post by mysoogal on 2009-04-26
if you install ubuntu using wubi !

just copy the ubuntu folder ! from C: with the boot files save to DVD ! thats it

if something goes wrong, replace that folder and your back.

you can also save your files outside ubuntu ! in /host/blaa/blaa/blaa/xp/

i copy my videos there and other configure settings :D

---

### Post by johnmoru on 2009-04-27
Hi....very nice article guys.Thanks for step by step for how to backup a system.Thanks so much.
[Zenerex]("http://zenerexnews.com")
[buy extagen]("http://www.zimbio.com/Hollywood/articles/1772/Buy+Extagen+Buy+Extagen+20+Discount")

---

### Post by renkinjutsu on 2009-04-30
how do you back it up over a samba network?
i don't have a big enough hard drive to make a backup, but i'm getting a new one soon so i want to back this one up..

i want to output tar file to be saved on a windows machine over the network, how do i specify a path?

---

### Post by majed on 2009-04-30
> **renkinjutsu said:**
> how do you back it up over a samba network?
i don't have a big enough hard drive to make a backup, but i'm getting a new one soon so i want to back this one up..

i want to output tar file to be saved on a windows machine over the network, how do i specify a path?

Thanks to Jody Simpson from [https://answers.launchpad.net/ubuntu/+question/6644](https://answers.launchpad.net/ubuntu/+question/6644) ,

```

Using the terminal, enter:

sudo smbmount //servername/sharename /mountdirectory -o username=username,password=password

this command (obviously filling out you info in place" will get you your mount. working.

If you wish to make this permanent, added it to your /etc/fstab

You can do this, again in the terminal, by entering:

sudo gedit /etc/fstab

once you have the file open, add:

//servername/sharename /mountdirectory smbfs username=userename,password=password 0 0

NOTE: This method is fine if its a single user system, however is a security risk if other users are on the machine.
This is due to the fstab file being viewable by all.

```

Now that I am home, I also did it myself using a different way.. I used a script to mount the windows shared directory into my ubuntu system.. 

Here is the code:

```

sudo mount -t cifs //<ip of windows machine>/<name of shared directory> -o username=<windows username>,password=<windows password> /media/<mount point>

```

I would create a windows user with the least possible privileges to use in this command so u don't expose ur password.. unless u feel totally safe about that..

Good luck!

---

### Post by renkinjutsu on 2009-05-04
thanks! i went ahead and mounted the share and my drive is being backed up over the net work now..
i forgot exactly what command you posted on the forum, but i used -t smbfs instead of cifs .. i think it works the same.. right? it mounts alright..

using lzma tar compression, painfully slow =\

---

### Post by Superlinkx on 2009-08-06
I don't know if anyone posted this, but if you are backing up to an external drive, exclude media folder or at least the drive you are saving to. Do not put exclude=/backup.tgz! It won't exist and if you don't exclude=/media or exclude=/media/<name of disk>, you will backup the backup folder and get the weird errors. Almost did this my self.

---

### Post by zhanglini on 2009-10-13
Question regarding the method in post #1:
I have /home in a separate partition, does this method only backup the partition that / is in?

---

### Post by gameguy on 2009-10-26
I did it and it seems to be working. But is there a way to boot up at say, midnight on monday night, tuesday morning (regularly), whatever, do a backup, and shut down.
If possible what would I need to do (as in have what plugged in to the desktop).

---

### Post by majed on 2009-10-26
> **gameguy said:**
> I did it and it seems to be working. But is there a way to boot up at say, midnight on monday night, tuesday morning (regularly), whatever, do a backup, and shut down.
If possible what would I need to do (as in have what plugged in to the desktop).

I believe u can use the BIOS alarm, if ur BIOS supports that.. 

Look at the following link.. u can use the same thing, except that u will need to change step 3 to have the script invoke ur backup or whatever u want to do.. u can then skip step 4 .. enjoy :popcorn:

[http://thdonline.wordpress.com/2009/05/31/wake-up-your-pc-and-download-stuff-in-an-early-morning-revisit/]("http://thdonline.wordpress.com/2009/05/31/wake-up-your-pc-and-download-stuff-in-an-early-morning-revisit/")

Majed

---

### Post by emigrant on 2009-10-31
hi, thank you very much for this benificial tutorial.
is it possible to backup from one machine and restore to another one?
i mean to resotre to a new machine which doestn have anything in its hard disk. so once restore this backup it would have all the new updates and apps which iv been making for some time in my machine?

---

### Post by Robertjm on 2009-11-18
You could back up to an external HDD and then put the "new" drive inside the new computer.

However, one of the problems you're going to possibly encounter is that any differences in hardware (video card, sound card, etc.) is going to cause issues when launching the new computer. 

The best suggestion would be to make sure your new computer uses separate partitions for your data and do a fresh install

Make sure you make yourself a list of all non-default programs you've installed so that you can go back and add them in once the core install is complete. I'm currently in the process of making my list, jumping from Intrepid to Karmic (or possibly Lucid if I feel so inclined. Did the alphas a couple of times with little pain:D  )

Good luck!!

Robert

> **emigrant said:**
> hi, thank you very much for this benificial tutorial.
is it possible to backup from one machine and restore to another one?
i mean to resotre to a new machine which doestn have anything in its hard disk. so once restore this backup it would have all the new updates and apps which iv been making for some time in my machine?

---

### Post by RaDeuX on 2009-11-19
I tried this method on my USB thumbdrive as well as the HDD itself. Each time I try to tar something, it gives me an error saying:
> tar: /: file changed as we read it
tar: Exiting with failure status due to previous errors

---

### Post by majed on 2009-11-19
u could be saving ur backup in the same directory that u r backing up too..

if u post the command u run then that would help..

> **RaDeuX said:**
> I tried this method on my USB thumbdrive as well as the HDD itself. Each time I try to tar something, it gives me an error saying:

---

### Post by RaDeuX on 2009-11-20
> **majed said:**
> u could be saving ur backup in the same directory that u r backing up too..

if u post the command u run then that would help..

Yeah, that's a possibility. Which is why I tried backing it up in my USB thumbdrive and do --exclude=/media, but it still gives me the same error.

---

### Post by majed on 2009-11-20
> **RaDeuX said:**
> Yeah, that's a possibility. Which is why I tried backing it up in my USB thumbdrive and do --exclude=/media, but it still gives me the same error.

I don't know what exactly r u backing up but tar will report that error when a file it is reading has its mtime stamp modified.. if u r trying to backup ur whole system then that file might be a log file that is being updated by another program.. there r tar options to ignore such error and not exit.. like ‘--ignore-command-error’ or ‘--ignore-failed-read’

I also highly recommend rsync instead of tar.. if u don't want to get dirty with the command line then u can use luckyBackup, a great backup and sync GUI for rsync.. 

i personally switched to luckybackup and i like it!

u can install luckybackup from synaptic.. and here is the website for it..
[http://luckybackup.sourceforge.net](http://luckybackup.sourceforge.net)

Best of luck!

---

### Post by milenixloerdi on 2009-11-21
Thanks A-star! Will the backup include all my installed software too please?

Thanks again

---

### Post by linxuser14 on 2010-05-07
Oops, my bad: I didn't realize this thread to be 20 pages long. I'll browse the rest of the pages now.

Hi all,
  This is a fairly old thread, so I posted on a kubuntu lucid forum to see if I get any advise. The following is copied from that post:

2010-05-06 20:11:45

Hi all,
  I'm using karmic and its configured to my liking. I'm curious to try lucid, but I'm wanting to backup my current karmic in case I need or want to restore it. I have my karmic installed on 3 partitions. I'm using tar for backup.

  I'm not sure if I have to do each partition separately. In case I do my planned backup at this point is to move all but Desktop folder within my user folder to a folder named Documents_Hold. And exclude it and Desktop from the tar. My aim is to get the hidden folders in the backup. I'm guessing upgrading to lucid will make changes in them.

  Anyway, my linux partitions are / , /home , and /usr. I'm going to try the following from terminal. Anyone know if what I've assembled (following) is enough, or too much for the tar files. And if I can restore my working karmic, should things go wrong? And thanks.

  / partition:

sudo tar cvpzf /home/*User_Folder*/MyBackup/root_backup.tgz --exclude=/dev --exclude=/home --exclude=/lost+found --exclude=/proc --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/usr /

  /home partition:

sudo tar cvpzf /home/*User_Folder*/MyBackup/home_backup.tgz --exclude=/home/lost+found --exclude=/home/*User_Folder*/Desktop --exclude=/home/*User_Folder*/Documents_Hold --exclude=/home/*User_Folder*/MyBackup /home

  /usr partition:

sudo tar cvpzf /home/*User_Folder*/MyBackup/usr_backup.tgz --exclude=/usr/lost+found /usr

/^)

:| 2nd post/own-reply

2010-05-06 23:43:??

  Upon further delving into this subject, I got referred back to the information I'd first found. Where I'd gleaned the command & options for the method I'm using. at:

#(Don't follow {its here} would be a loop)[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

  I'm still uncertain about the error at the end of tar(-ing) the /home/*User_Folder*/.* hidden folders. I did observe it grabbing all the files from ~/.* folders but, there's the error, at the end. Don't know if its important.

2010-05-06 21:12:11

OK,
  Heres the file result of my backup attempt:

*User_Folder*@lap:~/MyBackup$ ls -l
total 3522652
-rw-r--r-- 1 root          root           607198884 2010-05-06 20:42 home_backup.tgz
-rw-r--r-- 1 root          root           928421146 2010-05-06 20:39 root_backup.tgz
-rw-r--r-- 1 root          root          2068024960 2010-05-06 21:03 usr_backup.tgz
*User_Folder*@lap:~/MyBackup$

  / partition:

Finished with no apparent errors.


  /home partition:

I'm worried backing up the hidden stuff from /home/*User_Folder*

  process ended with:

tar: /home/*User_Folder*/.gvfs: Cannot stat: Permission denied
/home/*User_Folder*/.recently-used.xbel.9PQABV
tar: Exiting with failure status due to previous errors
*User_Folder*@lap:~$

This may be un-needed, to do this part of the backup. But I don't yet know.


  /usr partition:

Finished with no apparent errors.

  I'll let this be for the weekend, before I try doing the upgrade. Any comments/advise would be greatly appreciated.
Thanks.

:guitar:

---

### Post by majed on 2010-05-07
> 
  /home partition:

I'm worried backing up the hidden stuff from /home/*User_Folder*

  process ended with:

tar: /home/*User_Folder*/.gvfs: Cannot stat: Permission denied
/home/*User_Folder*/.recently-used.xbel.9PQABV
tar: Exiting with failure status due to previous errors
*User_Folder*@lap:~$

This may be un-needed, to do this part of the backup. But I don't yet know.


The errors u stated can be safely ignored for ur purpose of the backup..

use the "--ignore-failed-read" tar option and ur backup of the home partition will complete successfully.

Good luck :)

---

### Post by linxuser14 on 2010-05-07
Thanks majed,

Still an error at end:

tar: /home/*User_Folder*/.gvfs: Warning: Cannot stat: Permission denied
/home/*User_Folder*/.recently-used.xbel.9PQABV
root@lap:/home/*User_Folder*#

  But the line about tar: Exiting with failure status due to previous errors disappeared.

  I'm assuming, (I know) ignoring the Warning error will be O.K. Still seeing a lot of posts of problems with upgrading. I'm planning on doing it Sunday night or Monday.

  There is a lot of good info on this thread.

:D

  Hi, editing this in. I had broke my system. It was a 3 partition file system. I reduced it to a 2 partition system. It's up and running now. I made a post on kubuntuforums about it. The link to there is here in case anyone wants to see what I did.

[http://kubuntuforums.net/forums/index.php?topic=3111673.msg228624#msg228624](http://kubuntuforums.net/forums/index.php?topic=3111673.msg228624#msg228624)

---

### Post by wkt on 2010-07-06
> **A-star said:**
> Well, we'll just continue with our example from the previous chapter; the file backup.tgz in the root of the partition.

One of the beautiful things of Linux is that This'll work even on a running system; no need to screw around with **boot-cd**'s or anything. Of course, if you've rendered your system unbootable you might have no choice but to use a **live-cd**, but the results are the same.

Some years ago I already worked with Linux so I could follow your steps of backing up.

What I can't quite understand is how to procede in case of **disk crash**. Do I understand it right that I then have to store the backup.tgz file on an external drive ( copy it there ?, using cp ? ) and then to boot the live-cd to tar it back - but I am a little bit confused how to do that in detailed steps. I think I have to cd into the directory of the internal hard disk ( as / is on the CD I think ) - but where is it ? /mnt or /media or what else ?

Let me add the following question : what about booting from the restored internal disk ? How do I get the MBR/Grub running ?

---

### Post by El_Belgicano on 2010-07-21
Some years ago (good old 7.10-Gutsy) I could just tar my whole system (omiting /media, /mnt and a very few others) to /backup.tgz, screw up the system beyond repair, install a fresh minimal install (using the minimal iso image) and untar the whole system again to root, reboot and I would end up having my system just as it was before screwing it up.

A) Is it still the way to go with 10.04-Lucid?
B) Has someone already used that method on 10.04-Lucid?
C) Which root folders would I need to exclude to be able to backup this way? /media, /mnt, /proc and /sys probably, but what about the "/dev-debate"?

Thanks for your input/help/experience, :p

---

### Post by dirtyhabanero on 2010-08-21
Hey guys, I'm just about to run the backup code mentioned in the first post. I had a quick look at using Simple Backup Config but using terminal seems just as simple...

Basically, I've had a bad night and managed to screw my graphics card settings in an attempt to get dual screens working...so I just did a fresh install of Ubuntu since I couldn't find any quick remedies. I just wanted to know, if by doing a complete backup, from /, and I happen to stuff up my graphic settings again, will I be able to restore / and revert back to 'fresh' settings? ('fresh' as in settings like a fresh install)

I'm not sure if doing a backup from / will be the right thing to do. I'll try it anyway.

Edit: I think I found the answer to my question - post #37 of this thread

---

### Post by vinay nadig on 2010-08-31
hey there!! :) jus created a bakup using ur instructions.. I hav 2 say dey worked marvelously.. :D i hav d backup in my external HDD..  i hav a few questions regarding it though..
1. when i replace all the existing folders in root with the backup someday, will i have to do anything other than creating the excluded directories?? like registry and stuff?? (i recently migrated from windows.. :P )
2. i have a lot of apps an custom settings for my OS.. will all of it also be restored?? (meaning do i have to set the configuration again? like compiz configurations etc? )
thnx in advance!!
cheers!! :D

---

### Post by X1R1 on 2010-10-01
How can I automate this process? I would like to use this tool to backup my servers at work (which I do manually every 2 days or so).

I bet Ill have to use cron but dont know how to do it...

cheers

---

### Post by southernman on 2010-10-01
> **X1R1 said:**
> How can I automate this process? I would like to use this tool to backup my servers at work (which I do manually every 2 days or so).

I bet Ill have to use cron but dont know how to do it...

cheersCron would be an alternative. But there are a a number of tools made just for backups. Rsync would be a good first suggestion.

[Here's]("https://help.ubuntu.com/community/BackupYourSystem") some community documentation on the subject...

Of course, there's plenty of documentation on setting up cron jobs too.

---

### Post by LtPitt on 2010-11-15
Hello my friends!

I'd like to implement the tar function to backup a server I have but I don't know if it'll handle my different disks and partitions...
That's my fdisk -l:

```
Disk /dev/sda: 36.7 GB, 36734100480 bytes
255 heads, 63 sectors/track, 4466 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2   *        3648        3659       96390   83  Linux
/dev/sda3            3660        4466     6482227+   5  Extended
/dev/sda5            3660        3902     1951866   82  Linux swap / Solaris
/dev/sda6            3903        4466     4530298+  83  Linux

Disk /dev/sdb: 36.7 GB, 36734100480 bytes
255 heads, 63 sectors/track, 4466 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1217     9775521   83  Linux
/dev/sdb2            1218        4466    26097592+  83  Linux

Disk /dev/sdc: 36.7 GB, 36734100480 bytes
255 heads, 63 sectors/track, 4466 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3647    29294496   83  Linux
/dev/sdc2   *        3648        3659       96390   83  Linux
/dev/sdc3            3660        4466     6482227+   5  Extended
/dev/sdc5            3660        3902     1951866   82  Linux swap / Solaris
/dev/sdc6            3903        4466     4530298+  83  Linux
```

Any hints to do a complete and working backup?
Keep in mind that this is a proxy server and the only hd needed to make it work should be sda (system) and sdb (cache and logfiles).
sdc is just a mirror of sda.

Thank you all for your attention and ideas :)

---

### Post by Timxtreem on 2010-11-15
Hello to you all...

I would also like to know if this can be implemented for backing up an Ubuntu server system (used for webhosting).
My system is based on Ubuntu 10.04 with DirectAdmin and I have only 4 partitions:

Partition "/" which is 10Gb and currently 3Gb in use
Partition "/temp"
Partition "/home"
Partition "swap"

Usually, I backup /home and all users files every week via FTP.
What I would like to do is to backup my system before an upgrade (e.g. MySql, Php, Apache, proftp etc.) and restore it immediately if something goes wrong.

Should I backup the whole partition "/" using the procedure described at the first post? If yes, are there any certain files I should exclude?

Do you recommend another solution for this kind of server?
Note that I have access to the server only via SSH, but I have a "rescue system" function using a live cd image.

Best regards,
Tim

---

### Post by Elwood72 on 2010-11-15
I'm having a silly issue with my backup. I just finished doing a clean install of 10.10,and it's going off without a hitch so far,but....

I backed up everything I wanted to save to a disc,and I even went so far as to make sure I could extract it properly *before* I upgraded. It went off without a hitch initially,but now I can't open the file. Whenever I try; I get this error message:

> An error occurred while loading the archive..

Archive:  /home/elwood/Downloads/u1002.exe
[/home/elwood/Downloads/u1002.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/elwood/Downloads/u1002.exe or
          /home/elwood/Downloads/u1002.exe.zip, and cannot find /home/elwood/Downloads/u1002.exe.ZIP, period.


I also got one about not having the necessary permissions

I know whatever it is is simple,but I'm stumped.

---

### Post by El_Belgicano on 2010-11-16
> **LtPitt said:**
> Hello my friends!

I'd like to implement the tar function to backup a server I have but I don't know if it'll handle my different disks and partitions...
That's my fdisk -l:

<snip>

Any hints to do a complete and working backup?
Keep in mind that this is a proxy server and the only hd needed to make it work should be sda (system) and sdb (cache and logfiles).
sdc is just a mirror of sda.

Thank you all for your attention and ideas :)

Hello, if you tar from "/" with sudo, you'll backup all the mounted partitions at their mountpoints, should you wish to exclude some of them, unmount or use the "--exclude=/mountpoint"-flag in the tar command.
>> [Other thread about tar]("http://ubuntuforums.org/showpost.php?p=10089603&postcount=1140")

> **Timxtreem said:**
> Hello to you all...

I would also like to know if this can be implemented for backing up an Ubuntu server system (used for webhosting).
My system is based on Ubuntu 10.04 with DirectAdmin and I have only 4 partitions:

Partition "/" which is 10Gb and currently 3Gb in use
Partition "/temp"
Partition "/home"
Partition "swap"

Usually, I backup /home and all users files every week via FTP.
What I would like to do is to backup my system before an upgrade (e.g. MySql, Php, Apache, proftp etc.) and restore it immediately if something goes wrong.

Should I backup the whole partition "/" using the procedure described at the first post? If yes, are there any certain files I should exclude?

Do you recommend another solution for this kind of server?
Note that I have access to the server only via SSH, but I have a "rescue system" function using a live cd image.

Best regards,
Tim

Same as above for the procedure, see the link. No reason why it shoudn't work.

> **Elwood72 said:**
> I'm having a silly issue with my backup. I just finished doing a clean install of 10.10,and it's going off without a hitch so far,but....

I backed up everything I wanted to save to a disc,and I even went so far as to make sure I could extract it properly *before* I upgraded. It went off without a hitch initially,but now I can't open the file. Whenever I try; I get this error message:

<snip>

I also got one about not having the necessary permissions

I know whatever it is is simple,but I'm stumped.

See the link above to match your procedure with mine, also if you could give more details about how you did yours: exact command to tar, and to untar... didn't you forget to sudo the untarring part?

---

### Post by Elwood72 on 2010-11-16
> **El_Belgicano said:**
> 
See the link above to match your procedure with mine, also if you could give more details about how you did yours: exact command to tar, and to untar... didn't you forget to sudo the untarring part?

Here's exactly what I did:

I was on 10.04

I backed it up,and burned it to a disc.

I upgraded to 10.10 using the Upgrade Manager

(A so-called "Dirty" install)

I was still having the now-petty issues which caused me to upgrade in the first place.

I decided to do a "clean" install

I burned a disc,to do the clean install.

Before I did the install,I checked the backup disc to make sure I could get my files.

I had no problems.

When the clean install was completed, I inserted the backup disc to retrieve my old files.

I can save and extract the (backup) u1002 file,but I can't open it.

I have it in .zip and .exe formats,and neither one will open.

I want to open it so I can retrieve some of the files I backed up.


Other than that,everything is fine.

---

### Post by El_Belgicano on 2010-11-16
> **Elwood72 said:**
> Here's exactly what I did:

I was on 10.04
I backed it up,and burned it to a disc.
I upgraded to 10.10 using the Upgrade Manager
(A so-called "Dirty" install)
I was still having the now-petty issues which caused me to upgrade in the first place.
I decided to do a "clean" install
I burned a disc,to do the clean install.
Before I did the install,I checked the backup disc to make sure I could get my files.
I had no problems.
When the clean install was completed, I inserted the backup disc to retrieve my old files.
I can save and extract the (backup) u1002 file,but I can't open it.
I have it in .zip and .exe formats,and neither one will open.
I want to open it so I can retrieve some of the files I backed up.
Other than that,everything is fine.

What program did you use to make the backup? also, do not try to backup system files across versions...
for your .zip, one thing i can think of is you don't have the packages to handle them, have a search in synaptic for the packages ("zip" and "unzip")
Have a look at the manpage for both "tar" and "zip" you'll find a lot of useful info.
Don't worry for your files, as long as you have the archive, we'll get them back ;)

---

### Post by Elwood72 on 2010-11-16
> **El_Belgicano said:**
> What program did you use to make the backup? also, do not try to backup system files across versions...
for your .zip, one thing i can think of is you don't have the packages to handle them, have a search in synaptic for the packages ("zip" and "unzip")
Have a look at the manpage for both "tar" and "zip" you'll find a lot of useful info.
Don't worry for your files, as long as you have the archive, we'll get them back ;)

I don't recall which program I used,but it was recommended on this very board.

I think that you're right about the packages,from this point it seems like the only logical explanation. I'm going to check them out now.

Further bulletins as events warrant....:)


I installed everything from the package manager that had anything to do with .zip files...still nothing.

---

### Post by El_Belgicano on 2010-11-17
> **Elwood72 said:**
> I don't recall which program I used,but it was recommended on this very board.

I think that you're right about the packages,from this point it seems like the only logical explanation. I'm going to check them out now.

Further bulletins as events warrant....:)


I installed everything from the package manager that had anything to do with .zip files...still nothing.

I suggest you have a look at "man unzip" to extract the files you need, optionnally, you can select an output folder to extract all the files to and sort your way through what you need and what you don't need, recover the needed config files, and other personal stuff...

Make an empty folder with enough space to handle all your files.
Then:
```
cd /the/folder/you/want/to/extract/to/
unzip /path/to/your/backupfile.zip
```

Next time you backup, I strongly recommend the method in the link I provided since tar is standard in opposition to zip...

Hope that helps.

---

### Post by 2603Munna on 2011-01-18
Is there anyway to  restore system like this .., without being taking any backup of data

---

### Post by El_Belgicano on 2011-01-18
> **2603Munna said:**
> Is there anyway to  restore system like this .., without being taking any backup of data

Well "restoring" means a backup has to be made at some point...

If you are looking at something other than tar, you may think about disk imaging or simply a 1:1 copy of the files to another drive... But there is no "cancel" button to go back some steps.

---

### Post by malapradej on 2011-08-08
I am doing this partly for my own reference and for others who my want to try my monthly backup system. You can tailor this for your own need by changing some of the paths, parameters and variables to make it suit your needs. I am relatively new to ubuntu (less than 1 year), so feel free to suggest improvements.

I needed a backup system on my wife&#8217;s netbook that will do a monthly backup onto an external usb HD without having to use any GUI tools and done in the background. It excludes certain directories and compresses the data using gzip, but you can change the compression method by changing the "z" parameter after the "tar" command. The added bonus of this method is it does incremental backups after the first full backup. I you need to do another full backup (say after a couple of months) you can just delete the increm_log.snar file and if you don't care for previous backups, your previous log and backup files as well. I will be doing this as I am more interested in the latest data and maybe a restore of something a few months ago than many years in the past. You will start by creating a script file in the users home folder which will then be run by a anacron job which will need to be added to the /etc/anacrontab file.

The following line of text was added to the file I created - /etc/home/ericam/run_backup.sh.:
--------------------------------------------------------------------------------------------------------------
[COLOR=RoyalBlue]#!/bin/bash
# script that runs backup of /home folder and logs information

# creates the variables/files based on the date and time for the log files and .snar file needed by tar for the incremental backup. If does not find the snar file it will create a new full backup.
BACKUPLIST=/media/LINUX_BU/ericam-DOT-SE/$(date +%F-%T)_backup_list.log
BACKUPERR=/media/LINUX_BU/ericam-DOT-SE/$(date +%F-%T)_backup_errors.log
INCREMFILE=/media/LINUX_BU/ericam-DOT-SE/increm_log.snar

# writes the date to the 2 new log files
date > $BACKUPLIST
date > $BACKUPERR

echo "=================" >> $BACKUPLIST
echo "=================" >> $BACKUPERR

# creates a tar archive that will be compressed using gzip compression. It will send all errors and a list of files and folders backed up to a files. It uses absolute path names, keeps file permissions, excludes certain folders.
tar -cvpPzf /media/LINUX_BU/ericam-DOT-SE/$(date +%F-%T)_backup.tar.gz --listed-incremental=$INCREMFILE --exclude=/home/lost+found --exclude=/home/ericam/lost+found --exclude=/home/ericam/Downloads --exclude=/home/malapradej/lost+found --exclude=/home/malapradej/Downloads --exclude=/home/*/.gvfs /home >> $BACKUPLIST 2>> $BACKUPERR

echo "=================" >> $BACKUPLIST
echo "=================" >> $BACKUPERR

date >> $BACKUPLIST
date >> $BACKUPERR[/COLOR]
----------------------------------------------------------------------------------------------------------------

Make sure that the above folder is owned by root and that the user has the privileges to run this file without providing a password, otherwise other users home folders will not be backed up. Some would say this creates a security hole, but as it is only me and my wifes data on the netbook I don't see the need to be over cautious. I will not advise the use of this backup system on a computer that is used by people you don't know or trust.

Be carefull when editing the sudoers file. I use vim and have come to understand how it works, for most users nano will be a better option. in the terminal type: 
sudo select-editor
make sure that nano is selected.
in therminal type 
sudo visudo

[LEFT][FONT=Arial]This will bring up a text editor that will check the sudoers file before  it is saved to make sure you have not done something wrong[/FONT]. I give an example of my sudoers file but please be carefull when adding to yours as this may lock down your system and you won't be able to run any commands needing root permissions/sudo. I will recommend reading the sudoers man and help pages first before you start editing. The bits I added are in blue.

----------------------------------------------------------------------------------------------------------------------
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset

# Host alias specification

# User alias specification
[COLOR=RoyalBlue]User_Alias BU_USER = ericam, malapradej[/COLOR]

# Cmnd alias specification
[COLOR=RoyalBlue]Cmnd_Alias RUNBACKUP = /home/ericam/run_backup.sh[/COLOR]

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d

#allows users to run backup script as root
[COLOR=RoyalBlue]BU_USER ALL = NOPASSWD: RUNBACKUP[/COLOR]

---------------------------------------------------------------------------------------------------------------------

This basically allows any user in the BU-USER variable to run the backup script in the RUNBACKUP variable.

I then need to edit the anacrontab file to make sure this script is run monthly. I open the /etc/anacron tab with any text editor and the example below is mine with text in blue newly added.

----------------------------------------------------------------------------------------------------------------------
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1    5    cron.daily     nice run-parts --report /etc/cron.daily
7    10    cron.weekly     nice run-parts --report /etc/cron.weekly
@monthly    15    cron.monthly nice run-parts --report /etc/cron.monthly
[COLOR=RoyalBlue]
@monthly    30    erica_monthly_backup    /home/ericam/run_backup.sh[/COLOR]
-----------------------------------------------------------------------------------------------------------------------
This checks to see every morning by running the anacron, if it has been more than a months since the script has run. If it has it will try and run it again. The 30 stands for a 30 minute delay before the script will run.

You can at any time run the backup script to make a full or incremental backup by just cd'ing to where it is saved and type

sudo bash run_backup.sh

In a sense you don't even need the anacron but this will try and automate it, so you don't have to keep on thinking of when the last time was when you did a backup.

Hopefully somebody finds this usefull.:)

[/LEFT]

---

### Post by dcsoldschool53 on 2011-09-07
Thanks.

---

### Post by leppel on 2011-09-07
Is there anyway that you can make this tar file an ISO image? That would be fantastic!

---

### Post by dragonetti on 2011-09-27
How do you delete ALL the files/folders on the target (restore directory) which arent in the original archive during a TAR full system restore?
 
I tried the "recursive-unlink" switch, but I keep getting the message that directorys (like var) can not be unlinked... (I excluded the "proc" / "lost+found" ...etc directories)
But I am running an ubuntu 10.04 LTS => VPS version, maybe that's why unlinking isn't succesful.
 
Another method I tried is to use the "find" command (searching for modified files thus including new files) between: now - [date] ... then redirect the results to a "rm -rf"
 
Any other suggestion / tip(s) are very welcome

---

