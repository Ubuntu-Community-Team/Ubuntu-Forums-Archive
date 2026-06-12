---
title: "Home directory"
date: 2021-03-20
forum: Ubuntu/Debian BASED
---

### Post by Disabled20241022 on 2021-03-20
I am on PopOS and i was wondering if it is a good idea to move the entire Home directory to my other partition and if this is ok how do i do that?

---

### Post by Hagar Delest on 2021-03-20
Personally, I keep the /home in the same partition as /.
However, my data are on a separate partition and they are linked with symlinks that I put in my user profile.

The point being that when I upgrade, I install from scratch, with a brand new /home so that no former configuration file can interfere with the new flavor.

---

### Post by Disabled20241022 on 2021-03-20
Yes that is what i was thinking to, right now i have my files on the second partition but when i do a clean install i would like to have my settings, menu etc already there.
Any suggestions?

---

### Post by oldfred on 2021-03-20
That is what backups are for. So when hard drive fails, it becomes easy to restore your system from your backup.

You can move all of /home to new partition and reuse it, but that still needs backup.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

And you can move just the data folders to new partition(s) and link the folders back into /home. Then /home is tiny - 358M and real easy to backup, just the hidden user settings. I also move some larger hidden folders like Firefox & Thunderbird profile.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo du -hx --max-depth=1 / 2> /dev/null [/COLOR]
[sudo] password for fred:  
108K    /mnt 
8.0K    /media 
561M    /var 
4.0K    /opt 
4.0K    /srv 
1.1M    /root 
6.1G    /usr 
16K     /lost+found 
[COLOR=#ff0000]358M    /home [/COLOR]
9.1M    /etc 
197M    /boot 
4.0K    /cdrom 
8.6G    /
[/FONT]
```

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by TheFu on 2021-03-21
> **ayudha said:**
> I am on PopOS and i was wondering if it is a good idea to move the entire Home directory to my other partition and if this is ok how do i do that?

Sometimes yes.
Sometimes it isn't worth the hassle.
Answer: It depends.

On typical desktop systems with users, I generally place HOME onto different partitions to prevent a bad user process from filling up the OS partition and crashing the computer.
On most servers, where no end-users are allowed, I don't bother. Typically, the first userid created may have 50MB of files in their HOME and nothing else, so it isn't worth the trouble.

oldfred linked to the ubuntu wiki for how to move /home to other storage.  This gets into some details, but don't lose the overall goal for all those details.  As long as the location in the logical directory structure, owners, groups, and permissions appear the same after you are done, then what storage is used underneath doesn't matter.  
You can change file systems in this process, if you like, though HOME directories cannot be placed onto non-Linux-native file systems.  I.e. don't try to use NTFS or FAT32 or exFAT, but ext3/4, xfs, zfs, f2fs, and a bunch of others are 100% fine. Typically, I use ext4 unless there is a good reason for some other file system.  
On a raspberry pi, running from a microSD card, f2fs might be a better choice to keep the write counts down on the flash storage.  
Really new versions of Android support f2fs for the external microSD card too. That's handy.

So ... it depends.

---

### Post by Disabled20241022 on 2021-03-24
Perhaps it is easier to just copy and paste the files needed when doing a backup. cause i don't like extra software and i could not make a script for this proces in the past.
Now to figure out where the settings are saved.

---

### Post by TheFu on 2021-03-24
> **ayudha said:**
> Perhaps it is easier to just copy and paste the files needed when doing a backup. cause i don't like extra software and i could not make a script for this proces in the past.
Now to figure out where the settings are saved.

Copy/paste would work for files in your HOME, but only if the target storage supported POSIX - so not NTFS or FAT-whatever. Don't use those for backups - ever.  Some permissions could be lost in the copy process and that could break some software that really cares about security, even if you do not.

Copy/paste outside the HOME, loses the permissions, owner, group, ACLs, xattrs and could expand drastically any *sparse files*. Normally, ACLS, xattrs and sparse files aren't used too much, but if they are, that's a bunch of important data that will be gone.

One of my systems has a **sparse file** that is about 5MB in size on disk, but claims to be 50GB.  Copying it (or using a backup tool that doesn't support sparse files) expands that file to 50GB.  Sparse files are commonly used for virtual machine storage, but also for other needs. They are kewl and troubling.

---

