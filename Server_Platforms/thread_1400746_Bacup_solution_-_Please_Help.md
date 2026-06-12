---
title: "Bacup solution - Please Help"
date: 2010-02-07
forum: Server Platforms
---

### Post by dv310p3r on 2010-02-07
Hello all. I need a simple solution that will backup some files up. Here's what I need.

I have an external USB 160GB drive that is connected, automounted, partitioned, and formatted already. 

I have several directories of files that I want to make backup to my external drive on a regular basis. Preferably incremental backups so as to not eat up all the space in a few backups.

I've read a lot about backing up so far, but I can't seem to find any tutorials on how to do one as simple as this. They're all about backing up to NFS shares, or backing up using UTF-8 encoding, or backing up you're whole system. 

All i need to back up is my home directory, my var/www directory and my MySQL databases.

All help would be much appreciated and if there's any more information you need, please let me know.

Thanks,

---

### Post by HandyAndy on 2010-02-07
Have a look at [Simple Backup]("http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")

I use it in just the same way as you intend and it's always worked well for me.

It's in the repositories as **sbackup**

---

### Post by dv310p3r on 2010-02-07
Can sbackup be used strictly through the command line?

---

### Post by amac777 on 2010-02-07
If your external USB drive is ext3 or ext4, also check out rsnapshot:

```
sudo apt-get install rsnapshot
man rsnapshot

```
And if your external USB drive is NTFS, also check outr rdiff-backup:

```
sudo apt-get install rdiff-backup
man rdiff-backup

```

Both of those scripts allow you to make periodic snapshots and don't waste space saving stuff that hasn't changed since previous backups. They both also allow you to export MYSQL databases automatically before the backup is run.

---

### Post by falconindy on 2010-02-07
If you're backing up SQL databases and want true incrementals, you'll need to generate transaction logs from the DB server. Letting a filesystem level backup utility create the diff will just duplicate the **entire** database on each incremental if there are **any** changes.

---

### Post by dv310p3r on 2010-02-07
> **amac777 said:**
> If your external USB drive is ext3 or ext4, also check out rsnapshot:

```
sudo apt-get install rsnapshot
man rsnapshot

```And if your external USB drive is NTFS, also check outr rdiff-backup:

```
sudo apt-get install rdiff-backup
man rdiff-backup

```Both of those scripts allow you to make periodic snapshots and don't waste space saving stuff that hasn't changed since previous backups. They both also allow you to export MYSQL databases automatically before the backup is run.

I've formatted the drive to be ext3. 

I've installed the rsnapshot and i've read through the man a bit, but I'm still having some issues. 

Could you maybe explain a bit about setting up the rsnapsho.conf file. I've looked into the file, but I don't get it. Do I make the snapshot_root path to the place I want my backups to be, or is the snapshot file itself only the catalog index. 

Then the no_create_root 1, it says this is particularly useful if backing up to usb drive. This is where I got totally lost.

Thanks for any help.

---

### Post by apmcd47 on 2010-02-07
I've written a shell-script which uses unix dump (in the repositories) to back up monthly/weekly/daily increments (monthly is a full backup) from cron onto a disk.

If you are interested in trying that I can post it. My script backs up whole partitions but if I remember correctly it can back up just parts of the filesystem.

Andrew

---

### Post by amac777 on 2010-02-07
> **dv310p3r said:**
> Do I make the snapshot_root path to the place I want my backups to be, or is the snapshot file itself only the catalog index. 

Then the no_create_root 1, it says this is particularly useful if backing up to usb drive. This is where I got totally lost.

There are also some tutorials on the rsnapshot website as well: [http://rsnapshot.org/](http://rsnapshot.org/)

Anyway, yes, the snapshot_root path is where you want your backups to go. So this should specify a directory somewhere on your USB drive.

Example:

```
snapshot_root	/media/Backups/rsnapshot/
```

With your USB drive plugged in and mounted, you can also pre-create this directory by running the command:

```
sudo mkdir /media/Backups/rsnapshot
```

Note, change the path in the above two to match your specific setup.

The no_create_root 1 is useful so that if your USB drive is not plugged in when you start a backup, rsnapshot will just give an error message that the snapshot root does not exist and it won't create it.

Also, as it mentions in the comments, you can uncomment this command to have rsnapshot since you are running linux:

```
cmd_cp		/bin/cp
```

For the backup intervals, I keep mine very simple and just do a weekly backup. I also don't want rsnapshot to ever delete old snapshots as I plan to just buy a new external USB when this one finally does get full. So my intervals look like this:

```
interval	weekly	900
```

That 900 means it will keep 900 hundred snapshots, which is well above what I'll ever get to before I buy a new USB drive.

Hope that helps a bit. The documentation is really easy to understand and not that long so you might want to just read through everything as well.

---

### Post by dv310p3r on 2010-02-07
Thanks a million, I'll let you know how it goes.

---

### Post by dv310p3r on 2010-02-07
I actually went wtih a script that uses cp for backing up, it was something I was more familiar with, it went something like this. 

Do you know if this is a bad idea?

sudo cp -r -u -x -v [source dir] [dest dir]

I'm going to create a cron that will run this every so often. 

What do you think? I got it from [http://aikiwolfie.blogspot.com/2009/09/ubuntu-tip-simple-backup-command-using.html](http://aikiwolfie.blogspot.com/2009/09/ubuntu-tip-simple-backup-command-using.html)

Thanks
****

---

### Post by amac777 on 2010-02-07
Well, the problem with that solution is it won't preserve the older versions of files.

Example:

1. You edit an important document called critical.txt and delete some critical information by mistake but don't notice it right away.

2. Your cron job comes on and updates (synchronizes) your backup

3. You realize critical.txt is missing that critical information and you hope your backup still has the old version of the file before you edited it.

4. Sorry, the backup does not help you.

---

### Post by dv310p3r on 2010-02-07
If i'm ok with losing older versions, as I don't make that many changes to the files, would the solution I used be sufficient?

---

### Post by nobrac on 2010-02-07
> **dv310p3r said:**
> Can sbackup be used strictly through the command line?


Most of the solutions you'll see use rsync. Snapshots can be generated using hard links. At work I'm backing up hundreds of remote partitions using a method I came across at [http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/").

---

### Post by amac777 on 2010-02-08
> **dv310p3r said:**
> If i'm ok with losing older versions, as I don't make that many changes to the files, would the solution I used be sufficient?

Maybe. It's certainly better than nothing. Another problem with just synchronising files for backups is if a file gets corrupted and then that corruption gets propagated over to your backup as well.

---

### Post by dv310p3r on 2010-02-08
That's something that I didn't think about. I'll have to rethink my backup solution. Working in command line is difficult for me, as I've been raised around seeing the things as they are done. None of the backup solutions i've seen seem easy enough for me to undertake, and since there's no GUI, I can't SEE the results and ensure that it's working. 

Anyhow thanks for the advice and I'll try something new and let all know how it goes.

---

### Post by amac777 on 2010-02-08
That rsnapshot script should be pretty easy to "see" that it is working once you get the config file setup. You'll end up with a directory full of snapshots like:

weekly.0
weekly.1
weekly.2
etc

Each of those directories will be a full snapshot, and you can go into them (use "cd" command) and see all your files as backed up at that date. The .0 one is always the most recent backup, and they get older as the number increases (but you can also just look at the date by doing "ls -l").

To make the backups occur automatically, setup cron to run "rsnapshot weekly" once a week.

Of course, you can run the script more often than once a week if you like.

---

### Post by amac777 on 2010-02-08
> **nobrac said:**
> Most of the solutions you'll see use rsync. Snapshots can be generated using hard links. At work I'm backing up hundreds of remote partitions using a method I came across at [http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/").

The rsnapshot script uses this exact same method (rsync + copying with hard links). In fact, according to [rsnapshot.org]("http://rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html#intro"), it's based on that method:

> I originally used Mike Rubel's shell scripts to do rsync snapshots a while back. These worked very well, but there were a number of things that I wanted to improve upon. I had to write two shell scripts that were customized for my server. If I wanted to change the number of intervals stored, or the parts of the filesystem that were archived, that meant manually editing these shell scripts. If I wanted to install them on a different server with a different configuration, this meant manually editing the scripts for the new server, and hoping the logic and the sequence of operations was correct. Also, I was doing all the backups locally, on a single machine, on a single hard drive (just to protect from dumb user mistakes like deleting files). Never the less, I continued on with this system for a while, and it did work very well.

---

