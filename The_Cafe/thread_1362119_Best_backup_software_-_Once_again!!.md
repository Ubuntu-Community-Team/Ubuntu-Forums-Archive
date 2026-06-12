---
title: "Best backup software - Once again!!"
date: 2009-12-22
forum: The Cafe
---

### Post by donniezazen on 2009-12-22
What is your favorite backup software if you want to sync/transfer all your data from your home folder to external drive?

I have have tried Grsync, Unison, and Simplebackup.

Grsync- superfast but i don't know how to exclude and include the folders.

Unison - i like it but its extremely slow. 

sbackup - didn't like it.

One of the problem with backup is if you change the name of files the software has to transfer it (redundancy).

What's your opinion and suggestions?

---

### Post by Marvin666 on 2009-12-22
My backups are just make an iso of the drive, and store it on an external hard drive.
I probably need to get a 1TB external drive soon...

---

### Post by FuturePilot on 2009-12-22
You can exclude files using grsync by adding something like "--exclude-from=".grsync/exclude"" in the Additional options field under the Advanced Options tab. Then just make a file in ~/.grsync called "exclude" and put path and or file names to exclude in the file, 1 per line.

To answer the question, I used to like Sbackup, but I found it to be slightly buggy and not a very active project. I recently came across a really nice backup program called [Déjà Dup]("https://launchpad.net/deja-dup"). I only have 2 minor complaints about it. 1) since it doesn't run as root it can't handle situations where you don't have permissions to access a file, though I hear this may be planned for a future release. And 2) it doesn't seem to compress the on-disk data. For a single user system it works really good. If you're looking for something for a multi-user system it probably won't work as well.

---

### Post by Warpnow on 2009-12-22
Just rsync.

---

### Post by scouser73 on 2009-12-22
Pybackpack

---

### Post by handy on 2009-12-22
I built a FreeNAS system on couple of drives, FreeNAS boots from a 2GB drive & all files are stored on a 1TB drive.  They are in drive drawers that I install in my tower when I want to back up, after which I shut down No.2. box & remove the drives to protect them from any kind of power spikes.

The other software that I've recently used to clone a 320GB (to a 1.5TB drive that went back into the iMac as an upgrade) that had fat32, HPS+, Ext3 & JFS filesystems on it was Clonezilla, it did a perfect job.

Clonezilla has many options, is really easy to use from its LiveCD & is what I would use if I was cloning images of partitions for backup.  Which I will do one day, when I get around to buying a 2TB external drive.  

I will clone the 6 or so systems we have here onto it, & then continue to use FreeNAS for backing up the data.  Then I'll have a really quick reinstall solution if one of the systems becomes unrepairable or the drive fails.

---

### Post by CharlesA on 2009-12-22
> **Warpnow said:**
> Just rsync.

This is what I use. No GUI to use grsync. Unless it's web-based. (My other admin tools are web-based)

---

### Post by TheNessus on 2009-12-22
I just use copy paste. Why go through all the hassle of a program to simply copy files?

---

### Post by handy on 2009-12-23
> **TheNessus said:**
> I just use copy paste. Why go through all the hassle of a program to simply copy files?

That's what I do with FreeNAS, I just use Worker, the two pane dirutil, so I can see my source & destination directories (in this case workstation & FreeNAS) & any details that may interest me regarding date/time, permissions & such. Select the files/directories that I want to move or whatever...

I personally prefer the visual method it makes it a lot less likely that I'll make a mistake, or miss something.

If I was dealing with a lot of data, I would probably be using rsync or something of that ilk; as it is I don't have to spend much time keeping up to date backups in our home.

---

### Post by donniezazen on 2009-12-23
> **FuturePilot said:**
> You can exclude files using grsync by adding something like "--exclude-from=".grsync/exclude"" in the Additional options field under the Advanced Options tab. Then just make a file in ~/.grsync called "exclude" and put path and or file names to exclude in the file, 1 per line.

To answer the question, I used to like Sbackup, but I found it to be slightly buggy and not a very active project. I recently came across a really nice backup program called [Déjà Dup]("https://launchpad.net/deja-dup"). I only have 2 minor complaints about it. 1) since it doesn't run as root it can't handle situations where you don't have permissions to access a file, though I hear this may be planned for a future release. And 2) it doesn't seem to compress the on-disk data. For a single user system it works really good. If you're looking for something for a multi-user system it probably won't work as well.

Thanks the above command worked for me. How about if i want to add an include from command?

Thanks,
SK.

---

### Post by kzlazy on 2009-12-23
I do not know if that will meet your need, but I would also propose "meld" (it is in the repos).

Meld is a tool which allows the user to see the changes in, and merge between, either two files, two directories, or two files with a common ancestor.

It is a classic two panel tool and allows you to exclude, include or ignore files to be transfered (maybe wrong but I am not sure that unison does), before it all starts.

---

### Post by beercz on 2009-12-23
[http://rsnapshot.org]("http://rsnapshot.org/")

Run as a cron job on a server, pulling the backup data from my client laptop 4 times a day.

I've been doing this for 3 years, simple, automated, reliable and stress free!!

---

### Post by CharlesA on 2009-12-23
> **beercz said:**
> [http://rsnapshot.org]("http://rsnapshot.org/")

Run as a cron job on a server, pulling the backup data from my client laptop 4 times a day.

I've been doing this for 3 years, simple, automated, reliable and stress free!!

Thanks for the link, sounds like a useful program.

I stick with rsync, since I just backup my data to an external drive. I don't exactly have multiple backups tho (Mon-Fri).

---

### Post by PartisanEntity on 2009-12-23
rsync is my favorite, never had problems with it and in verbose mode I can easily see if there were any problems copying any files or folders.

---

