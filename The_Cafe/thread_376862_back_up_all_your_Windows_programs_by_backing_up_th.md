---
title: "back up all your Windows programs by backing up the registry + programs??"
date: 2007-03-05
forum: The Cafe
---

### Post by billdotson on 2007-03-05
Would it be possible to backup a Windows system, that is all the programs that are on it and their configurations (one that has the registry, ie: XP or Vista) by simply backing up the enitre registry and copying the entire program folder over to an external HDD?  Then all you have to do after a clean install of XP is to copy your program files folder back over and then restore your registry from that registry backup file.  Wouldn't that be an easy way to completely back up all your Windows programs?  Or would there be other things that you would have to do that would make backing up your programs that way too complicated to mess with? 

I know that with many programs you can install them to some external media because they don't have to write to the registry or they simply don't write to the registry.  Even if they do most programs have a backup way to save configuration files (as I am told).

So shouldn't backing up your registry and your program files folder be an easy way to back up a Windows system?  Someone asked me recently about what he needed to do to backup his current Windows stuff because he is getting a new HDD and I wondered if something like this would actually work.  If it will that is an extremely easy way to back things up and would save people the time of having to reinstall their programs and configure them when they have to reinstall Windows for whatever reason.

---

### Post by Crashmaxx on 2007-03-05
No, Windows is notoriously messy with the program and system files. You will need a lot more then that to backup anything worthwhile.

The best way to backup Windows for something like a HDD replacement, and in general really, is a ghost partition image.

You can do it with a Linux Live CD that has Partimage to an external HDD very easily. You can do it with the Ubuntu Desktop CD as long as you have access to the repositories with it. But you can do it with any distro and I recommend System Rescue CD as it has Partimage and many other nice tools built in. It is CLI only, but its all you need.

With Ubuntu you will need to do:
```
sudo apt-get install partimage
```
You may need to enable Universe and I think you need internet access. And don't worry, it is just installing it to RAM not the system.

With System Rescue CD or other distro with Partimage and after apt-get for Ubuntu do these steps:
```
mkdir /backup
fdisk -l
*See what your external drive is called, probably sda1 or similar and put into the below command*
mount /dev/*sda1* /backup
partimage

```
Now you just need to choose what partition Windows is on and tell it to backup to /backup and select your other settings. Then just let it go, it will take a while depending on the size. It should tell you when its done and if it worked.

And that is it, you now have an exact copy of Windows as it was. To restore it on the new drive, just make a new partition **and make sure it is the same size and properties as the original,** this is very important, cause it will cause you problems if you try to restore it to a different partition.

For Windows specifically, I recommend getting Windows organized, cleaned, and setup as you want it for a default system with everything install. That way, you have a clean copy to go back to when Windows breaks or dies. This is really handy and what partimage is most useful for. Anyway, make sure you defrag and check the partition first to prevent errors. 

Hope that helps. It might sound a little complicated, but once you get the hang of it, you can fully restore in around 10 min, and backup only a little longer.

---

### Post by Enki on 2007-03-05
Programs under windows often store data under "\Documents and settings". Thing like start menu's are also here. Just copying this folder between installations/users doesn't work very well (I've had to do this this myself when XP b0rked my user data). Also, hashed licence keys could be stored in the reg. and these could be dependent on features of that specific installation.

So the short answer is no. Making an image of the windows partition would be better. You could do this from Linux using [ntfsclone]("http://packages.ubuntu.com/warty/otherosfs/ntfstools").

---

### Post by Enki on 2007-03-05
Partimage had some [issues]("http://www.partimage.org/forums/viewtopic.php?t=5") with NTFS in the past. Not sure if this has been fixed.

---

