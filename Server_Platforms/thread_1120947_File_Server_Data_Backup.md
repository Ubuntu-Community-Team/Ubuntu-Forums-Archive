---
title: "File Server Data Backup"
date: 2009-04-09
forum: Server Platforms
---

### Post by nobull on 2009-04-09
I have a file server with about 520G worth of space on ext3 partitions.  I been researching ways to have all of my data redundant.  I would really like to get a RAID setup but that is not an option right now.  The easiest thing for me right now is to get an external USB hard drive.  My concerns are:

Amount of time to backup.  It would be impossible to copy that quantity of data over in a reasonable amount of time at any frequency.

Files would need to be in a format that is readily available.  For example not in a an archive.

Backup could be performed on a FAT32 or other partition that can be read and written to by a Windows OS.

Reliable.

I have briefly looked into rsync and it looks like it might be an option.  If anybody can provide any information on this topic I would appreciate it...Thanks.

---

### Post by cariboo on 2009-04-09
I use an external 750Gb drive to backup my files server. I use rsync to do the backups. the first time it takes several hours, but after that it just backs up the changed files. I never pay attention to how long it takes after a full backup, because it works in the background, it would guess it takes less then 20 minutes for a daily backup. My server is in my garage, so everything is run remotely.

Have a look at this [thread=639979]howto[/thread]

Jim

---

### Post by MrWES on 2009-04-10
> **cariboo907 said:**
> I use an external 750Gb drive to backup my files server. I use rsync to do the backups. the first time it takes several hours, but after that it just backs up the changed files. I never pay attention to how long it takes after a full backup, because it works in the background, it would guess it takes less then 20 minutes for a daily backup. My server is in my garage, so everything is run remotely.

Have a look at this [thread=639979]howto[/thread]

Jim

Rsync will do a 'smart' backup on only changed file on a FAT32 partition? I thought there was a limitation on that -- and it backed up all files everytime on a FAT32 partition.

Using the --modify-windows=2 might solve that.

[http://ubuntuforums.org/showthread.php?t=886048]("http://ubuntuforums.org/showthread.php?t=886048")

---

