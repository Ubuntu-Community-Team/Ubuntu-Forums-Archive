---
title: "Do you backup/clone your installation ?"
date: 2014-05-12
forum: The Cafe
---

### Post by linuxyogi on 2014-05-12
Hi,

Do you think its a good idea to clone the installation so that it can be restored later ? or 

Is it a waste of disk space coz Linux is stable and (almost) free of malware ?

Do you guys do it ?

---

### Post by TheFu on 2014-05-12
I do not bother with cloning. This ain't Windows with license keys.
Just backups of [files, settings, and list of packages]("http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview") to install.  This saves about 4G of backup storage per system.  One of my system backups has 120 days that can be restored and is less than 100MB total storage. That system doesn't really have any data, just settings, hence how it is so efficient on the backups.

A fresh install takes 15 min, restoring my settings and files another 15 min.  rdiff-backup is amazing at being efficient with storage for many versions of daily backups. Generally have 60-120 days of backups for every system (about 30) here. All of the backups fit on a single 500G partition.  I can't imaging how much storage and TIME it would require to do the same via an image solution.

---

### Post by LastDino on 2014-05-12
IMO: Every single person out there should backup whenever possible and keep clone of clean successful install with all his/her software. It wont even take 10 GB to do that and it saves you from hours of frustration. Irrespective of whether you're doing update or fresh install, it is must. 
Oh, yeah, it applies to every OS out here, not just Linux.

---

### Post by buzzingrobot on 2014-05-12
I backup /home (separate partition on its own drive), and anything in /etc or elsewhere that I've changed.

I don't clone or otherwise try to make a bootable recovery image of the entire system because it's easier just to reinstall from an ISO image, retaining /home, and bring over my edits from /etc and elsewhere from the backup. (Your list of sources, including any added PPA's, is in /etc/apt, so I just backup up that entire directory.)

I try to remember to keep an updated list of all installed packages (dpkq-query -l).  Somewhere I have a script that will compare that list to a similar list, and install the packages in the former that are not in the latter. Handy on a new install when I want to install packages I'd added to the old install.

I don't use any kind of compression scheme with my backup, which would require decompression to find and restore files. I just keep everything in the filesystem.  (I use LuckyBackup, which is a GUI wrapper that builds an rsync cron job.)

---

### Post by CharlesA on 2014-05-12
So far I've only cloned Windows boxes, but that may be due to having a nasty experience the last time I tried to clone a *nix box and having it blow up. Then again.. that was years ago... but I've not tried it since.

If anything you should keep a copy of installed packages and your home directory and that should be all you need to do to get a clean install back to it's regular state.

---

### Post by malspa on 2014-05-12
I regularly back-up my data, but that's it.

Still, I think that having a backup image of the entire system is a great idea. I would certainly not advise against it, even if I don't do it myself.

---

### Post by sudodus on 2014-05-12
It is well worth the time and cost to get a drive of the same size or bigger, and ***test that restore works***. Otherwise your backup/clone might give you a false peace of mind.

---

### Post by linuxyogi on 2014-05-12
I backup my music and documents to SpiderOak and video files to DVDs so the only thing that remains is the installation with the extra packages that I have selected and my settings. The  reason I wanna take monthly snapshots is that the snapshots will include all the packages and the software updates. If choose the other path that is do a clean install and restore the packages from a list it will require a lot of bandwidth depending on the number of packages and also the amount of software updates.

> **sudodus said:**
> It is well worth the time and cost to get a drive of the same size or bigger, and ***test that restore works***. Otherwise your backup/clone might give you a false peace of mind.

These are my partitions. I have downloaded CloneZilla. I have used Norton Ghost a long time back. IIRC NG lets you clone a disk to a file and later you can restore from it. I am expecting something similar from CloneZilla. I will just clone my / and save the file to my /home. Now, how am I going to test the restoration process ? I have no idea. I guess I will wait until I do something really weird and unrecoverable and then I will test it. If it doesnt work I will go for a clean install.

```
# parted -l
Model: ATA ST3160215AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  30.0GB  30.0GB  ext4
 2      30.0GB  156GB   126GB   ext4
 3      156GB   160GB   3999MB  linux-swap(v1)
```

---

### Post by HermanAB on 2014-05-12
Just backup your data.

One day when your computer goes to pot and you get a new one, or fix it, you would like to install the latest version of Linux anyway, not an old stale version.

---

### Post by HermanAB on 2014-05-12
double post bug

---

### Post by sudodus on 2014-05-12
> **linuxyogi said:**
> I backup my music and documents to SpiderOak and video files to DVDs so the only thing that remains is the installation with the extra packages that I have selected and my settings. The  reason I wanna take monthly snapshots is that the snapshots will include all the packages and the software updates. If choose the other path that is do a clean install and restore the packages from a list it will require a lot of bandwidth depending on the number of packages and also the amount of software updates.



These are my partitions. I have downloaded CloneZilla. I have used Norton Ghost a long time back. IIRC NG lets you clone a disk to a file and later you can restore from it. I am expecting something similar from CloneZilla.

Yes. Use Clonezilla to make a [compressed] image of the drive or partition(s). The image is a directory with a number of files. The default directory name contains the date and hour when the imaging process started.
>  I will just clone my / and save the file to my /home. Now, how am I going to test the restoration process ? I have no idea. I guess I will wait until I do something really weird and unrecoverable and then I will test it. If it doesnt work I will go for a clean install.

```
# parted -l
Model: ATA ST3160215AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  30.0GB  30.0GB  ext4
 2      30.0GB  156GB   126GB   ext4
 3      156GB   160GB   3999MB  linux-swap(v1)
```

If you only backup your root partition, you can store it in /home, but I would recommend to store it somewhere else, for example in an ***external disk***, that is not connected to the computer except when you make your new image. And you should have at least one image of the whole drive. Later on you can make images of only the root partition.

You need a third drive of the same or bigger size than the original drive. Replace the original drive with this new drive and select restore in Clonezilla. Reboot and test that the system works as it should when running from the new (and cloned) drive. If you make an image only of the root partition, you need the whole drive with bootloader, partition table, swap partition and the home partition for this test to work.

---

### Post by TheFu on 2014-05-12
> **sudodus said:**
> It is well worth the time and cost to get a drive of the same size or bigger, and ***test that restore works***. Otherwise your backup/clone might give you a false peace of mind.

+100.

Until the restore is tested, it is just "hope." Hope is NOT a plan.

I've seen Fortune50 enterprises fail to get a restored system after 2 yrs of planning and implementing backups. After 3 days of trying on rented servers (expensive), they had to give up for another year and rework their processes.

The more times we practice anything, the better we become at it. That includes restores from whatever backup method is used.  Think back to when you were learning to tie your shoes. Did you get it right the first time or did it take lots of practice?  Restoring backups is at least that complex. Practice.

BTW, saw a deal on 4TB Hitachi cool-spin drives today - about $40 cheaper than I've seen them recently.

---

### Post by slooksterpsv on 2014-05-12
I backup my data to externals; the OS I used to use an app to make a backup of everything I had installed and that. Now, not so much.

---

### Post by sammiev on 2014-05-12
This is why I backup, this scan is from yesterday and I only visit a few sites like this site and Netflix.

---

### Post by QIII on 2014-05-12
I backup.  I don't bother cloning because I always have the latest install image.  Cloning reintroduces any screw ups that might have been part of the root cause of a crash.

It takes 30 minutes to reinstall and 30 minutes more to update and then restore my backed up files.

---

### Post by Old_Grey_Wolf on 2014-05-12
Due to the high speed of my Internet service I don't clone. I do back up my /home and /etc regularly. I have full and incremental backups. Sometimes an incremental backup has the oops and you need to go to an earlier backup to recover from the oops. Always test your backup solution to make sure it is doing what you think it is doing.

---

### Post by monkeybrain20122 on 2014-05-12
> **HermanAB said:**
> Just backup your data.

One day when your computer goes to pot and you get a new one, or fix it, you would like to install the latest version of Linux anyway, not an old stale version.

Well one day your hard drive may die accidentally. Or a bad update may hose your system or less drastically, breaks some applications. In case of a bad update reinstall won't help before the next update as you will be installing the same bad version.

Cloning is good for many things and not just as a backup. like creating multiple installations and experimenting with impunity (I mess with graphic drivers and stuffs when I have the time, if anything goes wrong just restore / in 10 minutes, instead of posting thread on the forums and wait for a few days to bump thread. :)

Because of my use case a flexible, fast cloning tool is very important. I use fsarchiver as it just clones the file system instead of sector by sector like clonezilla. Now with uefi unfortunately fsarchiver doesn't work with gpt.Backing up data is in general trivial and there are a gazillion ways to do it, it doesn't concern or interest me much.

---

### Post by buzzingrobot on 2014-05-12
> **TheFu said:**
> 

Until the restore is tested, it is just "hope." Hope is NOT a plan. 

Ain't that the truth.

I once worked for a business that generated and published about 100,000-plus words daily, every day.  It sold online access to those words. The servers crashed over an extended holiday.  The on-duty admins couldn't fix it.  The switch to the backup that was supposed to happen automagically did not happen. We were DOA for 4 days. *None* of the files on the primary backup hardware could be restored.  We had to restore more or less manually from the offsite backup we had, happily, created a few months earlier. (Weekly tapes in a vault.) Took about a month.

Few of the many backup howtos scattered around the net seem to explain how to actually restore the stuff.

---

### Post by monkeybrain20122 on 2014-05-12
Well in general if you have a customized installation with a lot of tweaks and changes in configuration files and third party applications cloning is a good idea.  But if you only use vanilla configurations then it doesn't make much of a difference. But still for something like an update screw up, or when you accidentally hit the distro upgrade button and abort (not uncommon around release time) it is a lot easier and faster to restore a clone than to reinstall,--and reinstall won't work in case a bad update breaks something since you can't reinstall the older version that worked.

---

### Post by monkeybrain20122 on 2014-05-12
> **sudodus said:**
> It is well worth the time and cost to** get a drive of the same size or bigger**, and ***test that restore works***. Otherwise your backup/clone might give you a false peace of mind.

Only if you use a tool like clonzilla. With fsarchiver (its previous incarnation is called 'partedmagic") you don't need a bigger driver or bigger partition, just big enough for the contents. I routinely restore to smaller partitions.

---

### Post by SurfaceUnits on 2014-05-12
> **linuxyogi said:**
> Hi,

Do you think its a good idea to clone the installation so that it can be restored later ? or 

Is it a waste of disk space coz Linux is stable and (almost) free of malware ?

Do you guys do it ?

Remastersys makes a bootable live image of your installed system. I use it to clone Xubuntu images I use for XP replacements (1.6GB images) and for my own installed system(2.7GB). It works, never failed.

---

### Post by oldos2er on 2014-05-12
> **linuxyogi said:**
> Hi,

Do you think its a good idea to clone the installation so that it can be restored later ? or 

Is it a waste of disk space coz Linux is stable and (almost) free of malware ?

Do you guys do it ?

No, I backup the data in my home folder, and that's all I really care about. The OS itself is on a separate partition and can be reinstalled relatively painlessly when and if it's necessary to do so.

---

### Post by The Spectre on 2014-05-12
> **linuxyogi said:**
> Hi,

Do you think its a good idea to clone the installation so that it can be restored later ? or 

Is it a waste of disk space coz Linux is stable and (almost) free of malware ?

Do you guys do it ?
I think it's a good idea to Clone/Image a hard drive if you have a lot of OS customization or a bunch of programs installed.

It can save you a tremendous amount of time restoring from a Clone/Image instead of having to reinstall every thing from scratch and getting everything back to the way you want it.

It is also handy if you want to upgrade your hard drive because you can just Clone the old hard drive to the new one.

I use Redo Backup & Recovery to create disk images...
[http://redobackup.org/](http://redobackup.org/)

And I use FreeFileSync to Synchronize all of my documents and files to Network Hard Drive...
[http://freefilesync.sourceforge.net/](http://freefilesync.sourceforge.net/)

---

### Post by monkeybrain20122 on 2014-05-12
> **The Spectre said:**
> I think it's a good idea to Clone/Image a hard drive if you have a lot of OS customization or a bunch of programs installed.


Well I have a few OS's on my hard drive and I think cloning the whole drive is rather unnecessary and time consuming. For example, I am having a big update in one OS which I think may be risky so I would want to make a backup first. But why would I want to clone the whole drive with a lot of unconcerned stuffs with tools like Redo Backup or Clonezilla which do sector by sector cloning? It is seriously inefficient.

Here is a much better solution [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)
I can just clone the / partition of the OS I want to backup, typically it is 15G max and therefore it is very fast to clone and even faster to restore. :)

And what if I just want to migrate one OS instead of the whole drive to a different hard drive or machine? :) Again with fsarchiver I can selectively clone and restore only the partitions involved and there is no restriction on the size of the partitions/hard drive to restore to as long as the targets are big enough to hold the contents of the sources.

---

### Post by sudodus on 2014-05-13
> **monkeybrain20122 said:**
> 
[QUOTE=sudodus;13021685]It is well worth the time and cost to** get a drive of the same size or bigger**, and ***test that restore works***. Otherwise your backup/clone might give you a false peace of mind.

Only if you use a tool like clonzilla. With fsarchiver (its previous  incarnation is called 'partedmagic") you don't need a bigger driver or  bigger partition, just big enough for the contents. I routinely restore  to smaller partitions.
[/QUOTE]

That's right. With ***fsarchiver*** and the ***One Button installer*** (that uses tarballs) you can restore to a smaller drive, as long as it is big enough for the contents. But the OP is interested in ***Clonezilla***, which is a general and well-known tool, that works also with GPT so with dual boot systems with Windows 8. And then it is necessary to restore to a drive of the same size or bigger.

---

### Post by linuxyogi on 2014-05-13
I just cloned my / just to test how Clonezilla works. The cloning process was pretty fast even on my low spec system. After the image was created there was an option saying something like this "Do yo want to test if the backup can be restored ? (Nothing will be written to your hard drive) ". I selected it and the process completed successfully.  I am not sure how Clonezilla is checking without writing anything to disk.

> Only if you use a tool like clonzilla. With fsarchiver (its previous   incarnation is called 'partedmagic") you don't need a bigger driver or   bigger partition, just big enough for the contents. I routinely restore   to smaller partitions.

My / partition is 30GB and the image made by Clonezilla is only 1.6 GB. The Clonezilla people have made some serious improvements in their latest release. I read about it on Twitter.

---

### Post by linuxyogi on 2014-05-13
> **SurfaceUnits said:**
> Remastersys makes a bootable live image of your installed system. I use it to clone Xubuntu images I use for XP replacements (1.6GB images) and for my own installed system(2.7GB). It works, never failed.

I have never used Remastersys but after knowing what it can do it seems awesome but there is one big problem. 

When I Googled about Remastersys I found that it works only on Debian/Ubuntu systems. If I want to try some other distro it wont work. IMO Arch Linux users must create a tool like Remastersys coz I heard because of its bleeding edge nature things often break.

---

### Post by sudodus on 2014-05-13
Yes, the Clonezilla image is small, but when you test restoring from it, you need a 'full size' drive.

---

### Post by The Spectre on 2014-05-13
> **monkeybrain20122 said:**
> Well I have a few OS's on my hard drive and I think cloning the whole drive is rather unnecessary and time consuming. For example, I am having a big update in one OS which I think may be risky so I would want to make a backup first. But why would I want to clone the whole drive with a lot of unconcerned stuffs with tools like Redo Backup or Clonezilla which do sector by sector cloning? It is seriously inefficient.

Here is a much better solution [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)
I can just clone the / partition of the OS I want to backup, typically it is 15G max and therefore it is very fast to clone and even faster to restore. :)

And what if I just want to migrate one OS instead of the whole drive to a different hard drive or machine? :) Again with fsarchiver I can selectively clone and restore only the partitions involved and there is no restriction on the size of the partitions/hard drive to restore to as long as the targets are big enough to hold the contents of the sources.
Redo Backup & Recovery does not Clone/Image the whole drive it only does the sectors with Data on it.

Redo Backup & Recovery is a front end to Partclone...
[http://partclone.org/features/](http://partclone.org/features/)

And Redo Backup & Recovery can Clone/Image individual Partitions...

[IMG]http://redobackup.org/media/screenshots/4.jpg[/IMG]

---

### Post by TheFu on 2014-05-13
I like fsarchiver, but only when I'm moving physical machines. Otherwise, cloning a partition is just too much hassle and completely unnecessary.  Limited backups can easily get everything we need, make the restore process relatively simple and either be 100% tied to a current release or let us migrate relatively easy to a new release.

When I see folks so insistent that cloning is the way, my subconscious screams "Windows-think."  And that people don't know where the modified files are located on Linux systems. The amount of time and wasted storage is HUGE with cloning.

Requirements for my backups:
* There are 2 kinds of backups. 
** Constantly changing files, settings, HOME stuff - needs to be daily, automatic, with restore from yesterday, last week, last month, perhaps last quarter.
** Large Media files - hardly ever changing - manually use rsync for these. DONE. Period. Never a concern about them again. Quarterly, yearly, whatever works.
* 100% automatic. I tried manually doing backups. For the first month, it was fine. By the 6th month, I'd lapsed. By 2 yrs, I hadn't done a backup in over a year. Since going 100% automatic, I haven't missed a day in ... er ... 7 yrs?
* Backups need to take less than 5 minutes.
* The last backup needs to look like a mirror. No more incremental/full schedules.
* Restore from the last backup is just a cp.
* Prior backups can require a tool, but should always be manually available. No proprietary file formats. Efficient storage is MORE important.
* Testing backups and testing restores should be relatively easy. Validating a backup is "good" needs to be built-in.
* Remote backups over encryption required.
* Ability to store to encrypted storage
* Simple command line (similar to rsync)
Guess that's it.

**rdiff-backup** is the answer for me. It isn't perfect, but hasn't cause any issues in years either.

I've restored full machines a few times.  My first post has a link with more information on how.
Happiness is:
```
# rdiff-backup --list-increment-sizes  mail
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Tue May 13 02:57:04 2014         12.8 GB           12.8 GB   (current mirror)
Mon May 12 02:57:19 2014         31.1 MB           12.9 GB
Sun May 11 02:57:31 2014         26.2 MB           12.9 GB
Sat May 10 02:56:57 2014         12.2 MB           12.9 GB
Fri May  9 02:56:48 2014         35.6 MB           12.9 GB
Thu May  8 02:57:00 2014         17.9 MB           12.9 GB
Wed May  7 02:57:23 2014         11.0 MB           13.0 GB
Tue May  6 02:57:26 2014         34.0 MB           13.0 GB
Mon May  5 02:57:05 2014         12.2 MB           13.0 GB
...
Wed Apr 16 02:56:49 2014         11.9 MB           13.4 GB
Tue Apr 15 02:57:17 2014         11.3 MB           13.4 GB
Mon Apr 14 02:56:54 2014         35.1 MB           13.4 GB

```
and I have that for about 30 other machines too.  30 days of backups for 1G more in storage? How can you possibly walk away from that?

---

### Post by monkeybrain20122 on 2014-05-13
> **TheFu said:**
> I like fsarchiver, but only when I'm moving physical machines. Otherwise, cloning a partition is just too much hassle and completely unnecessary.  


Maybe completely unnecessary for you :) it just saved me a lot of troubles tearing my hair out and/or reinstalling last night/this morning. 15 minutes later I was back in business even though I am still trying to figure out what happened. [http://ubuntuforums.org/showthread.php?t=2223932&p=13022802#post13022802](http://ubuntuforums.org/showthread.php?t=2223932&p=13022802#post13022802)

---

### Post by slooksterpsv on 2014-05-13
Actually I have a couple of scripts to backup my data, here's a python script I made that would check the timestamp and if the version on my drive was newer than what was backed up, it would back it up:
```

import os

#Change rootpath
#Change destpath
#change destcppath
#to fit your needs.

rootpath = "/home/shawn"
destpath = "/media/FreeAgent Drive"
destcppath = "/media/FreeAgent Drive"
sl = "/"

def getList(dir):
	tdx = []
	tdy = []
	tall = []
	skip = 0
	try:
		tall = os.listdir(dir)
	except Exception as inst:
		print "Exception processing " + dir
		skip = 1

	if skip == 0:
		for a in tall:
			if os.path.isdir(dir + sl + a):
				if os.path.islink(dir + sl + a):
					pass
				else:
					tdx.append(dir + sl + a)
			elif os.path.isfile(dir + sl + a):
				if os.path.islink(dir + sl + a):
					pass
				else:
					tdy.append(dir + sl + a)
			else:
				1 + 1
		return tdx, tdy
	else:
		return 0, 0

def checkMod(fil):
	filpath = fil[len(rootpath):len(fil)]
	if filpath[len(filpath)-1:len(filpath)] == "/":
		print "/"
	else:
		pass
	if os.path.exists(destpath + filpath):
		if os.path.getmtime(fil) > os.path.getmtime(destpath + filpath):
			print fil
			os.system("cp \"" + fil + "\" \"" + destcppath + filpath + "\"")
		else:
			pass
	else:
		if os.path.islink(destpath + filpath):
			pass
		else:
			fpath = filpath[0:filpath.rindex("/")]
			os.system("mkdir -p \"" + destpath + fpath + "\"")
			os.system("cp \"" + fil + "\" \"" + destcppath + filpath + "\"")

def process(dir):
	dirdx,filex = getList(dir)
	if dirdx == 0 and filex == 0:
		pass
	else:
		for b in filex:
			checkMod(b)
		for a in dirdx:
			process(a)

adir,afile = getList(rootpath)

for a in adir:
	process(a)

```

That's how I USED to backup my files.

---

### Post by TheFu on 2014-05-14
> **slooksterpsv said:**
> Actually I have a couple of scripts to backup my data, here's a python script I made that would check the timestamp and if the version on my drive was newer than what was backed up, it would back it up: 

...

That's how I USED to backup my files.

I suppose you discovered **rsync** (which does this automatically)?

Greatest human inventions (in order):
* fire
* wheel
* UNIX
* ssh 
* rsync

Ok, so I'm joking, but just slightly. 

UNIX has been around a long time. Chances are that if you are creating a script, there is already a fantastic solution, provided you ask the right question. Linux/UNIX are NOT MS-Windows, so doing things our way does take a slightly different way of thinking. After training your mind to think in the UNIX-way, you'll be frustrated with the Microsoft-way of doing things which feels limiting.  If you aren't doing anything with Windows - the UNIX tool is likely 500x better.

---

### Post by pretty_whistle on 2014-05-14
As to the original question I do backup my install though I'll probably only need to restore the image to a new computer when I buy one in a few years.  Nothing else happens to where I'd need to restore it. :)

---

### Post by Old_Grey_Wolf on 2014-05-14
> **TheFu said:**
> I suppose you discovered **rsync** (which does this automatically)...

I like rsync for servers and grsync for desktops, laptops, and netbooks. With grsync you still have rsync so you can use the command line if you need it.

---

### Post by rewyllys on 2014-05-16
> **Old_Grey_Wolf said:**
> I like rsync for servers and grsync for desktops, laptops, and netbooks. With grsync you still have rsync so you can use the command line if you need it.
And LuckyBackup combines the GUI of grsync with cron, thereby making it very easy to schedule backups.  I use it to do a daily backup, at 0100 hours, of my /home directory (which, BTW, is on a partition of its own). 

 LuckyBackup hasn't missed a beat for me in over 2 years of use.

---

### Post by SurfaceUnits on 2014-05-17
But do you clone your installation?

---

### Post by TheFu on 2014-05-17
> **SurfaceUnits said:**
> But do you clone your installation?

I DO NOT clone any Linux installations.
* run RAID, where that is needed
* run daily backups (versioned!!!) of everything necessary to recreate an installation in about 30-45 min.

---

### Post by ibjsb4 on 2014-05-17
> **rewyllys said:**
> And LuckyBackup combines the GUI of grsync with cron, thereby making it very easy to schedule backups.  I use it to do a daily backup, at 0100 hours, of my /home directory (which, BTW, is on a partition of its own). 

 LuckyBackup hasn't missed a beat for me in over 2 years of use.

LuckyBackup has been around for years and time proven.

Myself, I use to clone.  These days I use a data partition to save everything important to me and back this up.

---

### Post by Old_Grey_Wolf on 2014-05-17
> **rewyllys said:**
> [QUOTE=Old_Grey_Wolf;13023754]I like rsync for servers and grsync for desktops, laptops, and netbooks. With grsync you still have rsync so you can use the command line if you need it.And LuckyBackup combines the GUI of grsync with cron, thereby making it very easy to schedule backups.  I use it to do a daily backup, at 0100 hours, of my /home directory (which, BTW, is on a partition of its own). 

 LuckyBackup hasn't missed a beat for me in over 2 years of use.[/QUOTE]

People need to backup/clone for various reasons. My preference will not work for everyone.

It is true that rsync and grsync don't have scheduled backups without using cron, at least with the version I have. LuckyBackup does provide that with a GUI interface, which I used for a while, and that is a nice feature. 

However, after retiring, I don't leave my desktops, laptops, or netbooks running 24 hours a day 7 days a week. I turn them off when I am not using them. 

It doesn't take very long to do backups to a HDD on my LAN, and I can use them while the backup is occurring. I do a backup when I get a notification of available updates, or I have new email I don't want to loose, or I edited/made new files I don't want to loose.

---

### Post by monkeybrain20122 on 2014-05-17
I am not really  that interested in file backup software, there are so many of them and most work more or less the same. I use unison for file backup, but can easily use something else like rysnc. Backing up data is not that big a deal as long as you do it. I find cloning system a lot more useful and interesting.

---

### Post by The Spectre on 2014-05-18
> **monkeybrain20122 said:**
> I find cloning system a lot more useful and interesting.
Disk imaging/cloning definitely has it's advantages.

If you have bad update, user error or a power failure that causes the OS to become corrupted you can easily and quickly get your system back to exactly as it was the day the disk image was made.

---

### Post by Kurt_Alan on 2014-05-29
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**


Definitely! For one principal reason: Config Time.  If the time spent on install is arithmetic , the time spent on OS config is exponential--if you count every last install, de-install, tweak, and personal preference.

This is the time that a clone saves.  After a clean install of 14.04, I tested both cloning and restore.  I wanted living proof that a restore would succeed.  It did.  I did this test after only a small amount of config.  Now that I have finished my complete config, one month later, I have done another clone to flash drive.

clonezilla.org  There's a few "gotchas" but once these are worked out, it works like a charm. (Gotchas: You need two flash drives for a clone, one for clonezilla and one for repository; the screenshots that explain clone and restore start off the same for these two different functions, which is confusing at first.  The difference is that for cloning you must pick the advanced option or you will bypass the necessary menus).

---

### Post by sudodus on 2014-05-29
Well, I have managed running Clonezilla in the ***beginner mode*** except one case, where I saved the command line and made a script file.

In this case there are several disks, and I want to make images of some partitions. But the biggest partition for multimedia iso files etc contains compressed files, and it is better to use another method to back it up.

---

### Post by linuxyogi on 2014-06-07
Recently I tried to install pclinuxos as dual boot with Lubuntu but pclinuxos didnt add Lubuntu to grub and the most pathetic thing is pclinuxos still uses grub legacy.

I know how to restore grub using the Lubuntu live cd but I thought lets restore Lubuntu using clonezilla and see if it restores grub too but it didnt. Most probably it was not supposed to.

I guess to fix grub image of the entire drive is needed not just the /.

---

### Post by LastDino on 2014-06-08
> **linuxyogi said:**
> Recently I tried to install pclinuxos as dual boot with Lubuntu but pclinuxos didnt add Lubuntu to grub and the most pathetic thing is pclinuxos still uses grub legacy.

I know how to restore grub using the Lubuntu live cd but I thought lets restore Lubuntu using clonezilla and see if it restores grub too but it didnt. Most probably it was not supposed to.

I guess to fix grub image of the entire drive is needed not just the /.

You've  a separate /boot or grub2 is installed somewhere other than /? If yes, then you need image of that too.

---

### Post by sudodus on 2014-06-08
> **linuxyogi said:**
> Recently I tried to install pclinuxos as dual boot with Lubuntu but pclinuxos didnt add Lubuntu to grub and the most pathetic thing is pclinuxos still uses grub legacy.

I know how to restore grub using the Lubuntu live cd but I thought lets restore Lubuntu using clonezilla and see if it restores grub too but it didnt. Most probably it was not supposed to.

I guess to fix grub image of the entire drive is needed not just the /.

> **LastDino said:**
> You've  a separate /boot or grub2 is installed somewhere other than /? If yes, then you need image of that too.

If you have only a root partition for Lubuntu and restore that, you need also restore the bootloader (at the head of the drive). Not in a general repair case, but in this case it was overwritten when pclinuxos was installed, and also if you want to restore/clone your system to a new drive.

It is small and fairly simple to restore manually

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

but will certainly be restored from a Clonezilla image of the whole drive. (I have done it.)

---

### Post by TheFu on 2014-06-08
Couldn't he boot off a LiveCD/Flash drive and run grub-install /dev/{insert-root-drive-device-here} to install grub2? Then from inside the Lubuntu boot, run sudo grub-update (or is it update-grub?) to get the other bootable OSes found/discovered?

I could be wrong.  Generally, I do a fresh install of a minimal OS, then restore everyone from backups including the list of installed packages.

---

### Post by CharlesA on 2014-06-08
> **TheFu said:**
> Couldn't he booting off a LiveCD/Flash drive and run grub-install /dev/{insert-root-drive-device-here} to install grub2. Then from inside the Lubuntu boot, run sudo grub-update to get the other bootable OSes found.

I could be wrong.  Generally, I do a fresh install of a minimal OS, then restore everyone from backups including the list of installed packages.

That should work, but I've only had to do that once or twice, so I don't really have much experience with it.

---

### Post by linuxyogi on 2014-06-08
Restored grub using the Lubuntu live CD, deleted the pclinuxos partition and merged it with the existing /home partition using Gparted.

---

### Post by monkeybrain20122 on 2014-06-08
Once again good that I have cloned my system or I would be tearing my hair out and cursing by now. Instead I 'fixed' the problem in less than 5 minutes.
[http://ubuntuforums.org/showthread.php?t=2224346](http://ubuntuforums.org/showthread.php?t=2224346)

---

### Post by TheFu on 2014-06-08
> **monkeybrain20122 said:**
> Once again good that I have cloned my system or I would be tearing my hair out and cursing by now. Instead I 'fixed' the problem in less than 5 minutes.
[http://ubuntuforums.org/showthread.php?t=2224346](http://ubuntuforums.org/showthread.php?t=2224346)

5 minutes?  So you did **sudo grub-install** and **sudo update-grub** as explained here: [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) ?  

Restoring a 20G cloned partition probably isn't 5 minutes, especially if slower USB2 HDDs are used. Though I will give you that it is 40 seconds of "human time" - the time that a human needs to spend connecting, mounting, and running the **ddrescue** command against the hardware.

The important thing is getting it restored and there are 50 different ways.

---

### Post by monkeybrain20122 on 2014-06-08
My problem has nothing to do with grub, but unity update. I don't restore all 15G, only 8G or so is actually used and I use fsarchiver just to image and restore the file system, not something inflexible like clonezilla. I could restore that to a partition of 10G if I wish (say suppose I shrink my / partition, clonzilla wouldn't allow that since the original partition is 15G) It took about 3 minutes actually, may be less.

---

### Post by leclerc65 on 2014-06-08
I symlinked on my home folders to a separate (NTFS) data partition. No separate '/' and /home , cloning takes less than 5 min, restore is even faster.
Maybe that makes me a bad Linux user because I rarely attempt to fix my system when something goes wrong, just restore the latest image.

---

### Post by CharlesA on 2014-06-08
> **leclerc65 said:**
> I symlinked on my home folders to a separate (NTFS) data partition. No separate '/' and /home , cloning takes less than 5 min, restore is even faster.
Maybe that makes me a bad Linux user because I rarely attempt to fix my system when something goes wrong, just restore the latest image.

You store your home directory on a NTFS partition?

---

### Post by buzzingrobot on 2014-06-08
> **leclerc65 said:**
> I symlinked on my home folders to a separate (NTFS) data partition. No separate '/' and /home...

This is confusing.  You say you have multiple "home folders" (as you would if you have more then one user), then that you have no '/' or '/home'.  

What drive boots Linux?  What, exactly, is linked to the NTFS drive? How does that substitute for a backup, since creation of a link in Linux does not see any files/data being copied. NTFS, I know, allows links of some sort, but I'm pretty sure it does not understand Linux links.

---

### Post by deadflowr on 2014-06-09
I think home folders means the folders in home, like Videos and Pictures and such.
I think I've seen this idea before.
You create an all-in-one partition for the distro(simply /) but then you create links to the folders on your data partition.
But you only link your personal data, like Videos or Music. But not to the configuration files and folders.
Or something like that.

Adding: You then repeat this process for any other distro's on the machine, me thinks.
NTFS probably means a dual-boot machine with windows(something-something)
So setting that partition as the one to share makes sense, since linux sees it, and windows stinks at seeing anything but it's own.

Though, come to think about it, I don't really see it as a backup solution.
Since if the NTFS partition blows up, there's nothing saved anywhere else.
I guess...

---

### Post by buzzingrobot on 2014-06-09
Right, I hadn't considered a dual-boot scenario:  One Linux partition, '/', with /home as a directory in it, and the usual directories found in /home (none of which are required) are actually links to real directories on the NTFS partition. They'd be visible to either OS.

It's more a method of isolating those data folders from breakage on the Linux side than a backup, since they aren't backed up.

---

### Post by leclerc65 on 2014-06-10
Deadflowr got me right.
My /home/me/Videos is a symlink to /media/Data/Videos...
Occasionally I copy 'Data' partition to an external hdd for security. Maybe to confuse you more, I use Total Commander run inside a Virtualboxed XP to do the task, because there is no Linux equivalence to do 'Overwrite all older...'.
The Data partition is mounted:

```

UUID=xxxxxxxxxxxxxxxxx 	/media/Data 	ntfs-3g #defaults,umask=007,locale=en_CA.UTF-8,uid=1000,gid=1000,windows_names 0 0

```
and it is used by my Windows 8 (readonly), Ubuntu 12.04, Mint 13 Mate, VB Win XP (readonly). I never upgrade, just install new distros then fix the symlinks.
There is no problem so far...maybe because I keep my sensitive informations on a very old laptop running Lubuntu 10.04 only.

---

### Post by sudodus on 2014-06-10
> **leclerc65 said:**
> Deadflowr got me right.
My /home/me/Videos is a symlink to /media/Data/Videos...
Occasionally I copy 'Data' partition to an external hdd for security. Maybe to confuse you more, [COLOR=#0000ff]I use Total Commander run inside a Virtualboxed XP to do the task, because there is no Linux equvalence to do 'Overwrite all older...'.[/COLOR]
The Data partition is mounted:

```

UUID=xxxxxxxxxxxxxxxxx     /media/Data     ntfs-3g #defaults,umask=007,locale=en_CA.UTF-8,uid=1000,gid=1000,windows_names 0 0

```
and it is used by my Windows 8 (readonly), Ubuntu 12.04, Mint 13 Mate, VB Win XP (readonly). I never upgrade, just install new distros then fix the symlinks.
There is no problem so far...maybe I because I keep my sensitive informations on a very old laptop running Lubuntu 10.04 only.

I use symlinks like that too. It works well for me.

I have an old licence of Total Commander. It works with Wine, but it belongs to the Windows world, and I don't use it much nowadays. Total Commander is nice, but I think that you can use ***rsync*** to do 'whatever is possible in Total Commander' at least concerning file transfer tasks. And I prefer rsync today.

From ```
man rsync
```

Is this what you want?

```
       -u, --update
              This forces rsync to skip any files which exist on the destination and have  a  modified
              time that is newer than the source file.  (If an existing destination file has a modifi&#8208;
              cation time equal to the source file’s, it will be updated if the sizes are different.)

              Note that this does not affect the copying of symlinks or other special files.  Also,  a
              difference  of  file  format  between the sender and receiver is always considered to be
              important enough for an update, no matter what date is on the objects.  In other  words,
              if the source has a directory where the destination has a file, the transfer would occur
              regardless of the timestamps.

              This option is a transfer rule, not an exclude, so it doesn’t affect the data that  goes
              into  the  file-lists,  and  thus it doesn’t affect deletions.  It just limits the files
              that the receiver requests to be transferred.

```

I often use

```
rsync -Havn
``` or ```
rsync -Havun
``` to test, 'dry run', and then remove the option ***n*** to perform the action.

---

### Post by TheFu on 2014-06-10
Yeah - **rsync** is one of those tools that every Linux/UNIX user should know.
* Fire
* Wheel
* UNIX
* ssh
* rsync
Mankind's greatest discoveries/inventions.  ;) It is THAT good.  Pretty much every modern backup tool is based on rsync (librsync really).

---

### Post by leclerc65 on 2014-06-10
I have been burnt by Rsync a few times, now I won't touch it with a 10' pole. 
I use Grsync, go one way (from Data to the HDD), somehow it messed up my 'Data' partition real good.
It's hard to teach an old dog new tricks.

---

### Post by Erik1984 on 2014-06-10
> **leclerc65 said:**
> Deadflowr got me right.
My /home/me/Videos is a symlink to /media/Data/Videos...
Occasionally I copy 'Data' partition to an external hdd for security. Maybe to confuse you more, I use Total Commander run inside a Virtualboxed XP to do the task, because there is no Linux equivalence to do 'Overwrite all older...'.
The Data partition is mounted:

```

UUID=xxxxxxxxxxxxxxxxx     /media/Data     ntfs-3g #defaults,umask=007,locale=en_CA.UTF-8,uid=1000,gid=1000,windows_names 0 0

```
and it is used by my Windows 8 (readonly), Ubuntu 12.04, Mint 13 Mate, VB Win XP (readonly). I never upgrade, just install new distros then fix the symlinks.
There is no problem so far...maybe because I keep my sensitive informations on a very old laptop running Lubuntu 10.04 only.

I have a similar setup, although more simpel because I only boot one version of Ubuntu and Windows 8.1. Thanks for posting your mount line some useful stuff in there regarding the persmissions. I still have to fix that.

---

### Post by onapthanh on 2014-06-13
I have done with my computer and see that A fresh install takes 15 min, restoring my settings and files another 15  min.  rdiff-backup is amazing at being efficient with storage for many  versions of daily backups

---

### Post by Niets on 2014-06-13
We clone each of our machines on to a 6 TB "media" server on the network.  Backup and restore just doesn't seem to get all the VPN, RDP, FTP, email, etc., etc. settings quite right and is at minimum an all day process.  But, cloning combined with cloud storage for daily redundancy makes our restores a snap.

---

### Post by Roasted on 2014-06-13
My process:

Each system that boots up runs the same (but may be slightly tailored differently) rsync script with ssh keys set up, which is as follows:

#!/bin/bash
set -e
rsync -a /home/jason --exclude=.gvfs jason@192.168.1.20:/media/storage/backups/jason/pm_ubuntu_xps/
zenity --info --text "Backup Complete"
exit

This script I keep stored in /usr/local/share, and in startup applications it runs the command "bash /usr/local/bin/backup" to kick it off. Each time a system is restarted, boom, backup of home directory takes place.

As far as imaging, I don't mess with it much anymore. I take regular image backups of my wife's laptop, but as far as my systems I really just take one a few days after I set up a new system. I can run with the punches of filling in the gaps of what's changed on my system from a 6 month old backup image crazy fast, so doing consistent images for me isn't a big deal. The real meat and potatoes is the data.

The storage location in question resides in my low powered i3 server that runs 24/7. This serves me local content for local video/music streaming to the HTPC, records video surveillance feeds via Motion, serves up ownCloud for me, etc. It's running a pair of 3TB WD Reds that are filling up quite fast anymore. At 3 am every night, my server runs a backup script:

#!/bin/bash
set -e
wakeonlan 00:11:22:33:44:55
sleep 5m
rsync -a /media/storage/documents jason@192.168.1.21:/media/storage/pluto/
rsync -a /media/storage/music jason@192.168.1.21:/media/storage/pluto/
rsync -a /media/storage/pictures jason@192.168.1.21:/media/storage/pluto/
rsync -a /media/storage/public jason@192.168.1.21:/media/storage/pluto/
rsync -a /media/storage/owncloud jason@192.168.1.21:/media/storage/pluto/
rsync -a --delete /media/storage/backups jason@192.168.1.21:/media/storage/pluto/
sleep 1m
ssh jason@192.168.1.201 sudo shutdown -h now
exit

As you can see in the script, it kicks on a secondary backup system via wake on LAN. It pauses 5 minutes just in case a disk check kicks in on the backup system, then fires up the rsync process. Once done it remotely shuts it down (I edited sudoers on the 2nd backup server so it can do so without the need for a password). This script runs 6 days a week. On Sundays it runs the same script but with --delete appended to each command. That way Sunday is like a full "mirror resync" process where what is on the backup server is 100% what is on my main server. During the week since I don't have --delete on each field, if I take a folder named "Pink Floyd" and rename it "Pink Floyd Music", both will reside on the backup server until Sunday when the --delete flag kicks in, meshing the backup server to be a clone of the main rig.

It's a pretty nice automated setup. Tie in an external drive that I bring home from work monthly and re-sync up and you have our family's most important data sitting on 4 drives across two systems on site and one location offsite. I dig. Not so much imaging being done anymore, I just don't have a need for it that I once had on Windows, but regardless of the OS, the data is always the real gold that you want to guard.

---

### Post by mbott on 2014-06-15
I image-off all my systems to external HDs with Clonezilla: 2 Linux boxes and a Windows box.  It's just easier for me to do it this way and I feel the most comfortable with this routine.

-- 
Mike

---

