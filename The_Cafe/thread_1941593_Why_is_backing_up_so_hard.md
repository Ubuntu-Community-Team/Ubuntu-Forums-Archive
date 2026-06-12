---
title: "Why is backing up so hard?"
date: 2012-03-15
forum: The Cafe
---

### Post by wolfen69 on 2012-03-15
No matter which OS people use, it seems backups are always an issue. I myself do it the old school way and copy ("by hand") new stuff to my external drives. Then again, I don't get tons of new stuff daily, so it's easy for me.

Is it a problem for you, and are you looking for another way?

---

### Post by Copper Bezel on 2012-03-16
I use online backup for document files (Dropbox), and then make a periodic backup with drag and drop or rsync. Those backups are non-selective (I've lost too much crap in the past doing what I though were complete backups of new material.)

I work with document files, though, and don't have a lot of media, so I can copy everything off in a half hour over USB 2.0.

I don't have to think about the Dropbox side of things for my critical files, but I don't do the full backups remotely as frequently as I ought to. In fact, I schedule it according to whenever I lose The Game.

....Dammit.

---

### Post by Lucradia on 2012-03-16
Backing up isn't hard for me, because I only back up documents, to a 32GB flash drive. I do not back up programs or anything of the sort. Only time I do is when I need to install a driver that is required by the system to connect to the Internet. (Windows 7 does not have my Intel LAN Card in its database.)

I do not, and will not back up programs, their settings, etc. because, why? I can just re-set them myself later if I feel like it.

---

### Post by odiseo77 on 2012-03-16
I wouldn't say it's a problem for me, but since I have 96 Gb of data to back up, it takes around 45 minutes or one hour to complete the transfer to an external HD, so it's a bit bothersome. That's why I often postpone it for weeks.

---

### Post by aysiu on 2012-03-16
I use two major backups--Crashplan, which automatically backs everything up to their servers; and rsync, which manually backs up changed or new files to my external hard drives. I don't think backup is difficult, but you do have to remember to do it. I just do the manual backup once a week, basically. The online backup happens without any user intervention, so it's not hard at all.

---

### Post by wojox on 2012-03-16
Automatic deja-dup backup to Ubuntu One.

---

### Post by wolfen69 on 2012-03-16
I've dealt with many people that have no clue as to backup. Then they complain......

---

### Post by sudodus on 2012-03-16
I use a mixture of

- ***clonezilla*** imaging where Windows is involved,
- ***unison*** syncing of an ext3 picture and multimedia drive and between external esata+usb drives with different backup versions
-direct ***rsync***ing (for temporary backing up of current stuff)

And I do a complete backup at least once a month, and when I have valuable stuff I backup that stuff with rsync. And believe me, I have needed to restore data from the backups several times ;-)

---

### Post by wolfen69 on 2012-03-16
> **aysiu said:**
> I use two major backups--Crashplan, which automatically backs everything up to their servers; and rsync, which manually backs up changed or new files to my external hard drives. I don't think backup is difficult, but you do have to remember to do it. I just do the manual backup once a week, basically. The online backup happens without any user intervention, so it's not hard at all.

Without getting technical, would anyone expect any *less* from you? You're a legend as is. ;)

---

### Post by Neezer on 2012-03-16
Backing up isn't hard.....cron and rsync for data and all that. rsync /home and any other folders that you want to save onto an external hard drive or a separate machine. 

This is not a difficult problem to solve. The real problem is that there is a mentality that it won't happen to me, or if my drive starts to fail, I'll save it in time...

---

### Post by Quarkrad on 2012-03-16
I have my pc backup automatically every time I switch off using a combination of GADmin-Rsync and a script.  I backup /home and another partition where  I keep my personal data (docs/photos/videos etc) to a 2nd HD -the total backup is 302GB.  This is great as I do not have to worry about backing up - I power down the pc and walk away, the backup routine runs automatically backing up only changes - couldn't be simpler.  I'm a newbie and got some help with the script when I first started off with Ubuntu (8.04) - I had a similar setup in my Windoze days, for me this is a very good solution.  (The personal data is on a ntfs partition and the backup is to a ntfs partition - Ubuntu /home being on ext4).

---

### Post by StephanG on 2012-03-16
I'm reading everyone else's back up plan, and thinking, "This is just sweeping the real problem under the rug."

You're all busy trying to make copies of Data.  Which results in *even more* data!  The real problem, which needs to be adressed is that we have so much data that we care about in the first place!

So, the ideal solution, is just to stop caring if you lose everything.  That way you start out with a clean slate everytime there happens to be a mass data extinction. :guitar:

---

### Post by weresheep on 2012-03-16
To me rsync isn't a backup solution. It is great for mirroring data for redundancy reasons (to prevent data loss if a hard drive fails etc.) but it doesn't allow to e.g. retreive a file you deleted 3 months ago by mistake but now really need. For this reason I use a mixture or rdiff-backup and rsync to create and then also mirror my backup directory.

My server (old Pentium 133MHz machine) has a 40GB system drive and a 1TB data drive. The system drive contains the OS (Debian Stable) and my home directory which currently has about 500MiB of data. The data drive contains media files (music and photos etc.).

I use rdiff-backup to create incremental backups of my home directory into another directory on the system drive. This backup directory is then rsync'd to the data drive so that I have a mirror of my backup.

I also have a 1TB USB drive attached to the computer which I turn on every once in a while. I use rsync to sync the data drive (which contains a copy of my backup and all my media) to the USB drive.

My main backup script runs via cron every night at 3am and has been for about 24 months now. With this setup I can go back in time to any point in the last two years to retreive any needed data.

My current backup directory is about 10GiB in size (I occasionally have large files in my home directory for a while that get backed up and they bump up the backup size a lot) and the drive has about 15GiB of free space. If I ever get short of space on my system drive I can always start trimming my back of the older entries or move the system drive to a spare 120GB I have laying around.

I don't backup my media files as I would need a lot more drive space which isn't an option for now, but I think this not too much of a risk as I generally don't delete anything from these directories so mirroring them is good enough for now.

It has taken a while to get to this system but I think it works quite well and with very little manual work on my part :)

-weresheep

---

### Post by GeneralZod on 2012-03-16
Selective backups using rdiff-backup and rsync.net (all completely automated) a couple of times a week; all unblacklisted files/ directories to external drive every couple of weeks or so.

---

### Post by MisterGaribaldi on 2012-03-16
I back up my data as I go along, both to local HDDs and to a personal fileserver I've got set up for that purpose.

Backing up data has never been a big deal to me, either.

As for it causing grief, I'm not particularly sympathetic to those who should know better but just can't be bothered, and to those who think that there should never be any problems in their computing experience and then lose everything.

Sucks to be them, frankly.

---

### Post by Copper Bezel on 2012-03-16
[QUOTE=wolfen69]I find all of your responses funny. It seems you people need some structured way of doing it. It's automatic and natural to me. Without hassle. My guess is most of you would lose all of your stuff if the worst happened.[/QUOTE]
No offense, but are you reading a different thread than I am? A full backup takes computer cycles. A selective backup takes *your* time and effort. And the whole point of the online backup services is that they're something you install and never think about again. Doing backups in a more universal way takes *less* time than the way you're doing them, and it's unquestionably more reliable, because there's no chance for human error. (Which is fine, and I'm not criticizing you, but you started with the question of whether it's inconvenient for anyone, and I think the answer is, quite unanimously, "No.")

---

### Post by forrestcupp on 2012-03-16
I just learned a very important lesson about backing up. I was resizing my partitions, and right after I began, I realized that I set something how I didn't want it. So I pressed Cancel. No matter how quickly you get to it, DO NOT EVER PRESS CANCEL after you have already started the process of messing with partitions. I lost everything. The bad thing is that I hadn't backed up in about a month, and I lost all of my complicated tax forms that I only stored on my computer. Stupid! I was lucky that I had my GnuCash data and some other very important files on Dropbox. You can bet I'll be moving my tax records to Dropbox, and also be making regular backups from now on.

> **aysiu said:**
> and rsync, which manually backs up changed or new files to my external hard drives.luckyBackup is a pretty good GUI frontend for rsync. It's in the repos.

> **StephanG said:**
> 
So, the ideal solution, is just to stop caring if you lose everything.  That way you start out with a clean slate everytime there happens to be a mass data extinction. :guitar:For people who have a paperless system, and who have all of their tax documents, other vitally important documents, family photos, and any other of a thousand different very important things stored on their computers, your solution can't be taken seriously at all. ;)

> **weresheep said:**
> To me rsync isn't a backup solution. It is great for mirroring data for redundancy reasons (to prevent data loss if a hard drive fails etc.) but it doesn't allow to e.g. retreive a file you deleted 3 months ago by mistake but now really need. For this reason I use a mixture or rdiff-backup and rsync to create and then also mirror my backup directory.Deja Dup is included in Ubuntu's default installation, and it does incremental backups like you're talking about. But I don't see that as a good solution, because I don't want to have 20 different time-stamped versions of everything I have on my external hard drive.

My solution is to do an rdiff-type backup or sync, and whenever I'm going to delete something from my computer that I want to keep, I'll manually copy it to a separate folder on my external that isn't included in the sync. That way I don't waste a bunch of space.

---

### Post by keithpeter on 2012-03-16
Hello All

[http://www.jwz.org/doc/backups.html](http://www.jwz.org/doc/backups.html)

I do the two disc thing, one for a sync'd mirror of my home drive, the other a proper backup.

Dropbox for documents that I need syncing between the netbook and desktop.

I'd love full local version control for documents (Libreoffice as well as text) by the way if anyone knows an idiot proof method.

PS: I do use a film camera :twisted:

---

### Post by flemur13013 on 2012-03-16
> **wolfen69 said:**
> I find all of your responses funny. It seems you people need some structured way of doing it.  It's automatic and natural to me. Without hassle.

I find all your responses pointless and stupid and not funny or interesting in any way at all.

---

### Post by winh8r on 2012-03-16
> **wolfen69 said:**
> No matter which OS people use, it seems backups are always an issue. I myself do it the old school way and copy ("by hand") new stuff to my external drives. Then again, I don't get tons of new stuff daily, so it's easy for me.

Is it a problem for you, and are you looking for another way?

I find that a lot of people just can't be bothered to do regular backups. A friend of mine once said to me "Backups are for offices and business stuff, I don't need to do all that on my system at home though"

These people soon learn the importance of backups when the inevitable disaster day strikes though.

I just do a manual backup of new items to an external drive daily, then at the weekend I copy the backup to another dedicated back up disk on a spare machine.

At most , I will lose six days worth of data, which I can live with.

All "important" documents are printed off and stored as hard copy as well.

---

### Post by Dragonbite on 2012-03-16
> **aysiu said:**
> I use two major backups--Crashplan, which automatically backs everything up to their servers; and rsync, which manually backs up changed or new files to my external hard drives. I don't think backup is difficult, but you do have to remember to do it. I just do the manual backup once a week, basically. The online backup happens without any user intervention, so it's not hard at all.

This is similar to what I am looking at setting up.

Right now I (g)rsync my /home directory to an external hard drive,and am looking at eventually getting CrashPlan for online backups.

This works for me so far, because if the computer gets totally destroyed I would get another computer and install some form of Linux on it.  Then just move the files back.

I want to set up CrashPlan to get my backups out of the house but I could conceivably get a network storage to put in my parent's house and have our systems backup there and set up their systems ot back up to one in our house.

Unfortunately the Windows on my wife's laptop is 7 Home, which does not allow backups to network devices.  So I either need to look at using Crashplan on her laptop, or the GoFlex software that came with the hard drive.

Eventually I hope to automate things, but as is 80 GB of files from one machine takes a while to copy.  I am also considering Back-in-Time but I am not going to bother with this until I refresh the desktop in a next couple of months.

So backups for "hardware failures" are getting addressed, and eventually hope to get backups for "house burned down" disasters will be in place.

As for my personal laptop, most files are in Dropbox. I would use UbuntuOne instead, except I go in-and-out of using Ubuntu and since it isn't available outside Ubuntu/Windows/iOS/Android, it doesn't help me there.

---

### Post by Copper Bezel on 2012-03-16
I depend on Dropbox for the web interface anyway. I can't be installing software on every random machine I need to access my files from. The fact that the files will outlive my machine, or me, in the case of a tragic accident, is just a sweet bonus.

I just ran my local backup due to the game-losing, incidentally, and it was easier than I remember it being (and just short of twenty minutes.) I really ought to just put this into a "backup.desktop" file:

```
rsync -ar ~/ '/media/d1a522f1-5e4c-4c18-9f2f-63a8ebed4e44/Backup'
```

Then I could plug in the drive, type a bit of the word "backup" into the overview and be done with it.

Edit: Done. And set to run in terminal so that I know when it finishes, obviously.

---

### Post by Seq on 2012-03-16
I have a home file server with a SATA hotswap drive bay ($20 online), though USB hard disks would work as well. The backup drives have one filesystem mounted by GPT partlabel, which is just the right amount of specificity to identify a backup drive, while allowing to have more than one.

Every Saturday night, the disk is luksOpened, mounted, and rsync copies (almost) all filesystems to the backup drive. The disk is then umounted, luksClosed, and I receive an email indicating success, or detailing failure (STDERR output).

The backup drive also gets copies of the output of `df`, `mount`, `pvs`, and `lvs`.

Every Monday I take out the hotswap drive and take it to work. I take one from work back home, and put it in. Currently my retension and recovery period is $DRIVES weeks. Currently two, but I plan on expanding that when drives get a little cheaper again.

For my use, this is simple enough that I can remember how it works, and somewhat cheap (too much data to backup online affordably. Plus I don't have the bandwidth for that). I used to use rdiff-backup, which was pretty neat, but I don't have enough space on the backup drive anymore.

The backup script I supports rsync, rdiff-backup, and uses LVM for snapshots If applicable.

On my laptop, the bulk of my $home is in git, and automatically pushed to my server. My documents are managed by sparkleshare (so again, git) and sync'd with the server. Bulk data (music, photos) are manually sync'd with Unison when changes happen (though I've been thinking about running that via cron).

I have a few metapackages in my PPA that can quickly rebuild a workstation for me, and the laptop is suspended when I'm not using it, so I don't bother with backing anything specifically from the laptop, since everything important is on my server anyway.

---

### Post by Seq on 2012-03-16
> **forrestcupp said:**
> I just learned a very important lesson about backing up. I was resizing my partitions, and right after I began, I realized that I set something how I didn't want it. So I pressed Cancel. No matter how quickly you get to it, DO NOT EVER PRESS CANCEL after you have already started the process of messing with partitions. I lost everything. The bad thing is that I hadn't backed up in about a month, and I lost all of my complicated tax forms that I only stored on my computer. Stupid! I was lucky that I had my GnuCash data and some other very important files on Dropbox. You can bet I'll be moving my tax records to Dropbox, and also be making regular backups from now on.

Too late now, but you might want to look in to testdisk. I've used it to recovery partition layouts after I've made a similar mistake.

---

### Post by JDShu on 2012-03-16
I don't have the discipline to back things up constantly. In the end what I do is put everything I cannot afford to lose onto webservices. I use GitHub for my software projects, Picasa for photos, and Dropbox for everything else.

---

### Post by Erik1984 on 2012-03-16
> **JDShu said:**
> I don't have the discipline to back things up constantly. In the end what I do is put everything I cannot afford to lose onto webservices. I use GitHub for my software projects, Picasa for photos, and Dropbox for everything else.

I don't have the discipline either, that's why I use a crontab for my rsync scripts.

---

### Post by forrestcupp on 2012-03-16
> **Seq said:**
> Too late now, but you might want to look in to testdisk. I've used it to recovery partition layouts after I've made a similar mistake.

Yeah, I saw that. I sure wish I would have known testdisk is in the repos and I could have run it from the same LiveUSB session I was in at the time. You're right, though. It's too late. I've already reinstalled everything. I will know if it ever happens again, though.

Fortunately, the only thing that really mattered that I didn't have backed up was my 2011 tax forms. That's probably one of the worst things I could have lost, but at least that was all I didn't have backed up. It was stupid of me to not do a backup after I did all of that work, but at least I can fill out all of those forms again whenever I feel like taking the time to do it.

---

### Post by Peripheral Visionary on 2012-03-16
It depends on what you're backing up. Backing up a big ol' 18-wheeler with a box trailer into a tight parking space is pretty hard... backing a trailered fishin' boat into the water is easy. :tongue:

/dumb sad joke

I just do manual backups of documents, pictures, and music to a CD once a month. Or more often if I add some really important docs, pics, or tunes. I'm a little scared of "the cloud," I guess.

All my settings are so easy to remember and input on a fresh installation I don't really back that stuff up.

---

### Post by kevdog on 2012-03-16
maybe someone can write a small tutorial about using rdiff-backup.  I just use rsync.  Its Ok I guess.

---

### Post by Old_Grey_Wolf on 2012-03-16
Backups are getting easier as I learn what I want and what the tools do.

I used the manual file copy method for a long time; however, I kept encountering permission obstacles that I had to overcome by doing it that way.

It tried other software until I found something that worked for me.

For example, I tried Déjà Dup; however, that is more of a disaster recovery system. I want to recover individual files when I need them.  Déjà Dup is more oriented to restoring the entire file system or directory.

I finally decided on using rsync for servers and grsync for desktops. They do what I need to do and they are easy to use. I can backup the entire file system or directories/partitions; such as, /home and restore individual files when I need to.

---

### Post by rewyllys on 2012-03-16
Essentially, I think that it's hard to overdo backups.  

And yes, I learned the hard way, many years ago!:frown:  

So . . .

I use LuckyBackup to make a nightly backup of my desktop's /home directory to a local external hard disk connected to the desktop.

I use Dropbox to sync most of the folders in my /home directory among my laptop, my desktop, my wife's desktop's C: drive (she insists on sticking with Windows), and my VirtualBox installation of Windows XP on my desktop.  (I use XP for preparing my income-tax returns, for OmniPage OCRing, and for a couple of other minor Windows programs that don't like being run in Wine. BTW, I place my income-tax returns in a Dropbox folder in XP, so that they are thus kept copied to the other machines.)

I use CrashPlan to keep my desktop's /home directory and my wife's desktop files continually updated in the cloud.

I use Paragon Backup to back up my wife's desktop to a local external hard drive connected to her computer.

Hurray for redundancy!:p

---

### Post by Lightstar on 2012-03-16
I kinda dislike deja dup and all the other systems that change the whole file extentions and/or compresses them into odd formats.  I like a plain copy.

I've been using LuckyBackup.

It's a simple copy of whatever selected folders you want.
It also updates / copies only what has changed since last time.

Since it's a simple copy, I can easily recover single files or just browse the backup like any other folders.

---

### Post by markp1989 on 2012-03-17
I use dropbox for all my important stuff, so those files get stored on every pc I own.

my file server does an rsync, without the delete flag, of the dropbox folder to a raid 5 partition 4 times a day,to protect against my complete dropbox getting deleted, at the same time it also do an rsync of the dropbox folder to a vps that I rent monthly as a last resort. 

I use deja-dup daily on all machines in my house to back up the home folder to the file server, I don't actually need to backup the home folder as everything that is critical is in the dropbox folder, but I do it just encase everything goes wrong.

---

### Post by sidzen on 2012-03-17
Because it is a discipline

---

### Post by forrestcupp on 2012-03-17
> **kevdog said:**
> maybe someone can write a small tutorial about using rdiff-backup.  I just use rsync.  Its Ok I guess.

You should check out luckyBackup. It's a pretty good frontend to rsync, and it makes it easy to set everything up how you like it. With luckyBackup, you can set it up for backup mode or sync mode. I've found that for my needs, backup mode with only one snapshot is my best options.

---

### Post by mr-woof on 2012-03-17
I've been using Rsync, to synch the data to a couple of usb hard drives, seems to be working very well at the moment. I manually do this once a month or so, my data doesn't really change that much month to month. 

I keep thinking about setting up an old machine as a backup/file server type machine, would you just use Ubuntu server for something like that?

---

### Post by CharlesA on 2012-03-17
> **mr-woof said:**
> I've been using Rsync, to synch the data to a couple of usb hard drives, seems to be working very well at the moment. I manually do this once a month or so, my data doesn't really change that much month to month. 

I keep thinking about setting up an old machine as a backup/file server type machine, would you just use Ubuntu server for something like that?

That's what I've been using. I've got all the Windows machines at home set to backup to my file server via robocopy, and then rsync the file server to an external drive daily. The backups are incremental, so I can go back at least a couple months if I find that I have mistakenly deleted something.

---

### Post by mr-woof on 2012-03-17
I think the main thing is that we do backup our data, I do like the idea of a backup server. I was thinking I might be able to use a raspberry PI for it.

---

### Post by arnab_das on 2012-03-17
i've tried using online backups in various permutations and combinations. and my conclusion is this: online backups are simply not worth it. its expensive, consumes a fair amount of data, sync failures and of course space limitations are a reality.

the best thing to do is to get hold of an extra local drive to store things. and use dyndns or some similar service to remotely access files. its cheaper and much much more reliable.

---

### Post by Copper Bezel on 2012-03-17
[QUOTE=arnab_das]i've tried using online backups in various permutations and combinations. and my conclusion is this: online backups are simply not worth it. its expensive, consumes a fair amount of data, sync failures and of course space limitations are a reality.[/QUOTE]
They can't work for everyone, certainly. I haven't had any sync failures with Dropbox, but all of the other problems depend on how much data you're pushing. Working with just document files, I get my backup for free, and with no noticeable overhead. Doing graphics work or something like that, it just wouldn't be an option at all.

---

### Post by standingwave on 2012-03-17
I use rsync once a day to back up changed files to a removable hard drive. Doesn't seem that hard to me. I alternate backups between two drives so even if I lose one, I still have the other.

---

### Post by PhilGil on 2012-03-17
I'm not sure I find backups that hard - you just need to use one of the "set and forget" tools that are available. You do need some discipline to set things up and to periodically check that all is well.

I've mentioned my backup strategy several times in previous threads: BackInTime to do automatic, daily backups to a USB hard drive supplemented by a weekly backup to a portable hard drive that I keep at the office. I have no problem with online services for offsite backups - I used Carbonite when I was on Windows and found it convenient and easy to use. However, the portable hard drive is cheaper.

I have loads of irreplacable files on my hard drive (such as family photos and financial records) and, for me, regular backups are a necessity.

---

### Post by forrestcupp on 2012-03-17
Looks like we're starting to establish that backing up isn't so hard. :)

---

### Post by kevdog on 2012-03-17
So I was doing and rsync backup and ran across this peculiar error:

rsync: recv_generator: failed to stat "/home/kevdog/backup/pj/My Documents/X
oom/sdcard/pulse/catalogImageCache/http%3A%2F%2Fpulseapi.appspot.com%2Fapi%2Fcat
alog%2Fcatalog_image%3Fcatalog_item_primary_key%3D53820411%26image_type%3Dicon%2
6width%3D60%26height%3D60.1": File name too long (36)

I really didn't know that linux had a file name length constraint.  I admit that the file name is really long -- but I didn't specifically name the file.

---

### Post by wolfen69 on 2012-03-17
> **forrestcupp said:**
> Looks like we're starting to establish that backing up isn't so hard. :)
Thought I'd stop in and see how this thread is going. I do realize, and have known a lot of you have great backup routines that are second to none. However, I think my original question was geared more towards the "average" person.

But there are a lot of great responses, and get to find out how different people do it. I just copy and paste to an external drive when I get something new. Which isn't often, so having a server with rsync, and some sophisticated way of doing it makes no sense to me. Tbh, if I lost everything, my life would still go on just as it is now, and wouldn't be any worse for it. Most of what I save is *very* replaceable, and garbage.

---

### Post by MisterGaribaldi on 2012-03-18
> **forrestcupp said:**
> Looks like we're starting to establish that backing up isn't so hard. :)

Well, that depends, forrestcupp. I find it easier backing up while I'm in a car, than if I'm on foot.

Then again, YMMV. :D

---

### Post by standingwave on 2012-03-18
> **wolfen69 said:**
> But there are a lot of great responses, and get to find out how different people do it. I just copy and paste to an external drive when I get something new. Which isn't often, so having a server with rsync, and some sophisticated way of doing it makes no sense to me. For those with modest backup requirements or don't feel like writing an rsync script, there's always Grsync which wraps a GUI interface around rsync and provides graphical buttons and switches for the most common options. I only back up my data. I figure everything else (the os and programs) is replaceable. My data isn't.

---

### Post by HermanAB on 2012-03-18
The problem is that it is hard to decide what to back up, since the data set is changing all the time.

A better approach is to think what you DON'T want to backup, since that seldom changes.  Then make a rsync rule that includes everything and excludes a few things, put it in /etc/cron.daily and you are done.

---

### Post by forrestcupp on 2012-03-18
> **wolfen69 said:**
> 
But there are a lot of great responses, and get to find out how different people do it. I just copy and paste to an external drive when I get something new. Which isn't often, so having a server with rsync, and some sophisticated way of doing it makes no sense to me. Tbh, if I lost everything, my life would still go on just as it is now, and wouldn't be any worse for it. Most of what I save is *very* replaceable, and garbage.

Then again, there are a lot of people who put their whole lives on their computers, and that type of backup makes a lot of sense. I'm one of those people. All of my taxes and tax receipts, bills, checking accounts, documentation, programming projects and work are all stored on my computer. Almost everything I do is on my computer. If I lost all of that and ever got audited, I'd be in a lot of trouble. If I lost some of that stuff that I've worked my butt off for a lot of hours, I'd probably cry. :)

Not everything that everyone has is replaceable. But if you're not like that, you're one lucky dude. ;)

---

### Post by kaldor on 2012-03-18
> **wolfen69 said:**
> Is it a problem for you, and are you looking for another way?

Not a problem, but it's a hassle. Takes forever to do, presumably because I use NTFS on my external. 

I use Ubuntu One and Dropbox for very non-personal backups. I would never trust anyone but myself with confidential/personal/etc files. I recommend the same to others.

---

### Post by CharlesA on 2012-03-18
> **HermanAB said:**
> The problem is that it is hard to decide what to back up, since the data set is changing all the time.

A better approach is to think what you DON'T want to backup, since that seldom changes.  Then make a rsync rule that includes everything and excludes a few things, put it in /etc/cron.daily and you are done.
Agreed. That is the way I do it. For example, my dvd collection isn't backed up because I can always just rip them again (even if it would take a while). Skipping those saves a ton of space on the backup media.

---

### Post by insane_alien on 2012-03-18
I set up a small bash script years ago that dumps a copy of my home folder onto the backup servers drives. it does this every night, every year it'll compress the whole shebang with bz2 and store it on a seperate drive(along with a sha-256 of every file in there), every month it'll check the hash's against what is in the mirror. It'll take a compressed snapshot of those files and store it with the big compressed directory. 

I haven't touched the script since i wrote it and it has allowed me to recover from quite a few oops moments when tinkering. most i've ever lost was a days work.

backing up isn't hard. setting it up, maybe. if you put some effort into the setting up, you'll never need to think about it again.

---

### Post by CharlesA on 2012-03-18
Just remember to test/check your backups regularly.

---

### Post by Dragonbite on 2012-03-19
I know I should do a restore from a backup to make sure it works, but I'm afraid if THAT fails, then I'm still hosed (and unless I can figure out how to do it successfully, I've lost everything in spite of the backup).

That's why I like the rsync version, so far, because I can navigate through the directory tree and see the files.

I also like how Back-in-Time lets me look through the files and pick a version to restore.

Deja Dup and some others, I haven't a clue whether it will work?, will it overwrite everything? or just some?

I know I should, but I am not so certain...

---

### Post by kevdog on 2012-03-19
I've always restored piecemeal from a backup.  It would usually consist of reinstalling a new version of the OS and then selectively bringing back folder to the new install.  I've never actually had to reverse the backup process completely.  Probably not the most efficient way to do it -- I know.

---

### Post by forrestcupp on 2012-03-19
> **Dragonbite said:**
> I know I should do a restore from a backup to make sure it works, but I'm afraid if THAT fails, then I'm still hosed (and unless I can figure out how to do it successfully, I've lost everything in spite of the backup).

That's why I like the rsync version, so far, because I can navigate through the directory tree and see the files.

I also like how Back-in-Time lets me look through the files and pick a version to restore.

Deja Dup and some others, I haven't a clue whether it will work?, will it overwrite everything? or just some?

I know I should, but I am not so certain...

I prefer non-compressed backups for the same reason. Not just because I'm afraid it won't work, but also because I'd like the ability to go into a backup and fetch one file if I want. I usually use the software to do backups because it automates a lot of stuff, but I manually do any restoring, because how hard is it to copy and paste a bunch of files?

---

### Post by Dragonbite on 2012-03-19
Conveniently, HowToGeek.com just did an article on [[COLOR="Navy"]How to Back Up Ubuntu the Easy Way with Déjà Dup[/COLOR]]("http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/?utm_source=newsletter&utm_medium=email&utm_campaign=190312"). I didn't know that restoring individual files was a capability. I thought it was an all-or-nothing.

---

### Post by CharlesA on 2012-03-19
> **kevdog said:**
> I've always restored piecemeal from a backup.  It would usually consist of reinstalling a new version of the OS and then selectively bringing back folder to the new install.  I've never actually had to reverse the backup process completely.  Probably not the most efficient way to do it -- I know.

I do the same with rsync. I've never really been a fan of compressed backups and I've got plenty of space for the non compressed versions.

> **forrestcupp said:**
> I prefer non-compressed backups for the same reason. Not just because I'm afraid it won't work, but also because I'd like the ability to go into a backup and fetch one file if I want. I usually use the software to do backups because it automates a lot of stuff, but I manually do any restoring, because how hard is it to copy and paste a bunch of files?

I've used rsync to restore backups, but if it's just one or two files, I'll just copy/paste them to where they need to go. Quite easy. ;)

---

### Post by Old_Grey_Wolf on 2012-03-19
> **Dragonbite said:**
> Conveniently, HowToGeek.com just did an article on [[COLOR="Navy"]How to Back Up Ubuntu the Easy Way with Déjà Dup[/COLOR]]("http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/?utm_source=newsletter&utm_medium=email&utm_campaign=190312"). I didn't know that restoring individual files was a capability. I thought it was an all-or-nothing.

Nice link. I decided not to use Déjà Dup because I didn't see an option to restore an individual file. I didn't know it integrated with Nautilus.

---

### Post by KiwiNZ on 2012-03-19
Back is simple, make automated. One copy for onsite one copy Offsite.

---

### Post by CharlesA on 2012-03-19
> **KiwiNZ said:**
> Back is simple, make automated. One copy for onsite one copy Offsite.
Best way to do if even if offsite backups can be a bit of a pain.

---

### Post by IWantFroyo on 2012-03-19
I just have a habit of moving anything I make immediately to a flash drive. No problems here.

---

### Post by wolfen69 on 2012-03-19
> **IWantFroyo said:**
> I just have a habit of moving anything I make immediately to a flash drive. No problems here.
I did that sort of, except I had 2 hard drives in my desktop for storage. (no longer use a desktop pc) And when I got something new or made changes, both drives received the up date via copy and paste. Not automated like some people use, but reliable.

---

### Post by kiwimenace on 2012-05-10
I have a question, I would like to be able to back up, this way.

I have 2 partitions, one with the os file system( / ) and another with /home, the home partition i back up using luckybackup and that works fine for me, totally satisfied with that.

 I would like to be able to back up the os file system( / ) partition by simply just copying(perhaps use luckybackup for this too) all its files to a safe external place, probably into a truecrypt file container. 

Then when i have a problem just use a livecd and copy all the os files back into place and start from there again, first though delete or quick format the partition.

I know theres all the tools etc to do these things but basically the way I have described above would suite me well and i only want to be able to get my system up and running quicker if something happens that my limited linux skills cant fix without reformatting.
 
Anybody see any problems with this ideah?

---

### Post by mamamia88 on 2012-05-10
I have nothing really important on my computer besides my music but i have 2 mp3 players with all my music on it so if if something happened i wouldn't miss anything really.  I also use dropbox which is awesome.

---

### Post by wilee-nilee on 2012-05-10
My computer's are just for running OS's several usually, all my important stuff in on externals.

I use a rsync gui grsync to sync the home and clonezilla to clone each partition individually.

As the late Ron Popeil said "set it and forget it" I like click it and forget it myself. :)

[http://en.wikipedia.org/wiki/Ron_Popeil](http://en.wikipedia.org/wiki/Ron_Popeil)

---

### Post by KiwiNZ on 2012-05-10
Cloud....back up made simple.

I do manually  back up some stuff and put it in our Safe.

---

### Post by Bandit on 2012-05-10
I got a [Rosewill RX35-AT-SU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817182155") and put a WD Blue Caviar 320GB drive in it and it works really really well even formated with NTFS under Ubuntu 12.04.

For those like myself with a lot of data to backup I really recommend it.
I do suggest a cool running drive as there is no vent holes, but with my blue caviar drive I can leave it on all night running a backup and it stays cool with no issues.

Cheers,
Joe

---

### Post by CharlesA on 2012-05-10
> **KiwiNZ said:**
> Cloud....back up made simple.

I do manually  back up some stuff and put it in our Safe.
I backup monthly and put it in my safe.

Daily backups are left out... which probably isn't a good idea, but meh.

---

### Post by sudodus on 2012-05-11
> **kiwimenace said:**
> I have a question, I would like to be able to back up, this way.

I have 2 partitions, one with the os file system( / ) and another with /home, the home partition i back up using luckybackup and that works fine for me, totally satisfied with that.

 I would like to be able to back up the os file system( / ) partition by simply just copying(perhaps use luckybackup for this too) all its files to a safe external place, probably into a truecrypt file container. 

Then when i have a problem just use a livecd and copy all the os files back into place and start from there again, first though delete or quick format the partition.

I know theres all the tools etc to do these things but basically the way I have described above would suite me well and i only want to be able to get my system up and running quicker if something happens that my limited linux skills cant fix without reformatting.
 
Anybody see any problems with this ideah?

It looks good to me. But if you want to be sure, you can get another HDD of the same size as your internal one and test that it works to restore your system.

By the way, I use Clonezilla from a live CD to make images of my internal HDDs. There are many way to backup your data. Use whatever suits you as long as you ***know*** that it really works.

---

### Post by Face-Ache on 2012-05-11
Every time i see this thread i find myself singing "Backing up is hard to do" to the tune of Neil Sedaka's "Breaking up is hard to do"  :D

Okay ..... i'm sorry ...... i'll see myself out .....  *sigh*

---

