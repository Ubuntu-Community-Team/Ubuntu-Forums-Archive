---
title: "You and rsync - what's your backup use"
date: 2023-03-07
forum: Ubuntu, Linux and OS Chat
---

### Post by BBQdave on 2023-03-07
Long story short: A long long time ago I had a salvaged 500GB HD that I put in a USB Case. I copy **Documents** folder and other data to that HD - drag and drop. Over the years of doing that I have several (time labeled) folders of data. An example would be *DOCs230228* which is **Documents** folder from 2023-02-28.

After years of this, I have multiple time labeled folders of data, most the same data recopied. I am still not even close to using 1/4 of that HD.

So would rsync benefit me? Copy and sync only changed data? Or keep on keeping on with time labeled folders and data saved for that time period?

Your thoughts and experiences appreciated :)

---

### Post by TheFu on 2023-03-07
This is why a backup tool that handles versioning would be better for you.  rdiff-backup works using librync, and the command really isn't THAT different.

With just a little more planning, you can get a much better backup that is useful for rebuilding the system in less than 30-45 minutes to be just like it was before. [https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432) has a simple script.  The only things I'd change in that script now, for a really simple backup, are
```
[s]/usr/bin/rdiff-backup  --exclude-special-files  ....[/s]
```
becomes
```
/usr/bin/rdiff-backup  --exclude-sockets --exclude-device-files --exclude-fifos ...
```
"special files" also includes symbolic links, so excluding those isn't good for everyone.

And I'd add 
```
/usr/bin/apt-mark showauto > /root/backups/apt-mark.showauto
```
with the other apt-mark command. Turns out that both list of packages can be needed due to the way that APT dependencies happen.

---

### Post by BBQdave on 2023-03-07
Appreciate the information TheFu. More to read, more to explore :)

---

### Post by TheFu on 2023-03-07
> **BBQdave said:**
> Appreciate the information TheFu. More to read, more to explore :)

When testing new backup methods and tools, can I suggest using /etc/ as the directory?  It has files that need to have specific permissions, specific owners and specific groups, while being relatively tiny.  Modifying a file in /etc/ can be done with little risk to see how versioning backup tools handle it.  Adding a line with a comment in /etc/hosts is an easy thing, right?  Adding a new file is also easy.

So, with just a few backups ... perhaps 3-5, and minor changes between each backup set, we can see how those changes are handled to gain comfort with each tool.

At restore time, we can easily fine 50MB of space under /tmp/ to restore into and see that owners, groups, permissions, ACLs, xattrs are all maintained. Heck, add a few symbolic links (/etc/resolv.conf is usually a symlink) and you have a test for everything important.  If your backup tool handles /etc/ well, it will handle your HOME well too, probably.

One of the main reasons I like rdiff-backup is because the most recent backup seems just like an rsync mirror.  When I need to restore a file, 99% of the time, I need the most recent backup from last night, so the restore is just a copy or scp or sftp. Easy for anyone to understand.  If I need older versions, only then do I need to look up the **rdiff-backup -r {timespec}** command timespec.  It is very flexible - last week, 13 days ago, 2 months ago, 2 backup-sets ago, or an exact date in yyyy-mm-dd format, if that's needed.

Backing up /etc/ is just one of those things that is extremely useful even if we can't directly restore everything there.  Having those files as reference on a new system **is** useful and if you put comments with specific tags in the config files that you've modified over the days, weeks, years under /etc/, then you'll be able to relocated those files and changes again quickly.  
```
$ cd /etc/
$ sudo fgrep -ril   thefu  * |more
aliases
aliases.db
chrony/chrony.conf
cron.daily/00logwatch
fstab
hosts
logwatch/conf/services/zz-disk_space.conf.53475.2023-03-06@10:28:27~
NetworkManager/system-connections/Wired connection 1.nmconnection
postfix/main.cf
resolv.conf
samba/win7lap-D.credentials
ssh/sshd_config
ssl/certs/ca-certificates.crt

```
So I don't have to hunt down too many files in /etc/ thanks to tagging I've done on that system.  I do use ansible, so many files in /etc/ don't have specific tags added, but are custom. Rerunning the ansible devops tool will fix those. Sadly, the systemctl commands used to mask 20 things don't get captured. Sigh.  
That's a relatively new system, less than a month old, so only the core stuff is there.

---

### Post by maglin2 on 2023-03-08
I've used luckybackup for a few years.
It's just a frontend for rsync, but it makes like easier for numpties like me.
Most of my data is static, so each run takes a few seconds. 
I used to run backintime (which I think was based on rdiff-backup), and was very happy with it till it stopped working, and it was beyond me to figure out why. Don't know what it's like now.
Edit - it seems backintime was based on rsync too.

---

### Post by TheFu on 2023-03-08
back-in-time uses hardlinks for the different backup sets.  This is very different from how rdiff-backup works, which uses reverse differential files that are compressed to minimize the storage needed for file differences.
The hardlink method of backup versioning, as used by rsnapshot, back-in-time, and 500 other script front-ends, has been around for 30+ yrs and it works well, with a few liabilities. Almost every Unix Admin book has a script that uses hardlinks in an appendix.

Almost all the free backup tools on Unix-like OSes are based on librsync.  rsync is a great tool.  I use it multiple times every day, but not for backups where I need versioning. There are better, easier, tools, for that.

Everyone talks about backups and that's good, but backups without the ability to restore are useless.  That's where looking at the backup stroage areas and understanding how the files are actually stored makes a huge difference.  I like to see the files, see they are there, obviously correct with the right owner, group, permissions, ACLs and xattrs, because when restoring system files, all those things are critical.  A simple copy doesn't handle those details correctly.  
There are backup tools that throw data into specific chunk sizes unrelated to the actual files included in the backup. They capture all the other stuff beyond just the file and they can even encrypt those chunks so each can be stored safely on someone else's computer disks.  That's how duplicity, Deja Dup, Duplicati work.  But without one of those tools, there's no getting the data back.  Whereas with back-in-time or rdiff-backup, the files are stored in what turns out to be a mirror of the source directory tree.  Restoring a file is a copy or ... an rsync. Which every is easier.  For me, that's a key difference.  The fact that rdiff-backup commands look very much like rsync commands is another bonus.

---

### Post by zebra2 on 2023-03-08
For me LuckyBackup works just fine.   I will have to admit that during the Wayland transition when LuckyBackup had  compatibility problems rsync served me pretty well but I never did get it doing exactly what I wanted. With rsync I was spending too much time on management without the best results. Years back when I was a hotshot brainiac I probably would have been ok with rsync. Not today.

---

### Post by BBQdave on 2023-03-08
Thanks again all for the information and experience.
I am researching and gaining an education :)

---

### Post by aljames2 on 2023-03-08
+1 for rdiff-backup.  Love it.  

I don't like image type backup solutions for anything, seldom do they restore correctly, especially if your hardware has changed, and with most of them you cannot go retrieve a file without restoring or upacking the entire image. As stated, rdiff-backup allows you to restore from previous versions, or you can just go get the most recent version of a single file you may need.

@TheFu... very cool idea to place a unique # comment in all custom files, scripts, etc. and using that nifty search idea.  Simple and awesome!  Thx for that!

---

### Post by maglin2 on 2023-03-09
By the way, bit of an eggs in one basket paranoia thing I suppose, but I also run the default deja dup backup to a separate drive (as well as luckybackup).
It's a useful fallback, but its product is not readily inspectable just from a file manager. The luckybackup product is. I usually know what file I most recently added/modded and always check for that in backup after running.

---

### Post by jajodo on 2023-03-10
I have found a combination of lucky backup and hard link backup useful, quick and it takes up little space.
Lucky backup runs and differentially copies my files to a directory "current"
Lucky backup then executes my one line script that makes hard links of files in current to a directory automatically named date and time:
So directory "current" is my latest backup and I have full backups from multiple dates each only taking up the space and time of a differential backup.

cp -alr /path/to/current /path/to/backup-`date +%Y%m%d--%T`

---

### Post by jajodo on 2023-03-10
I just looked at screenshots of back in time.
The backups are named very similarly to what you get if you use the cp command I use

---

### Post by TheFu on 2023-03-10
> **jajodo said:**
> I just looked at screenshots of back in time.
The backups are named very similarly to what you get if you use the cp command I use

Back-in-time is using the normal rsync+hardlinked version method. What makes back-in-time very great is that it does hourly backups with hardlinks and deletes more and more of those backup sets as time moves forward  So, for the last 48 hours, we have 1 backup set for each hour. More than 48 hours ago, we have 1 backup set for each day.  More than a week ago and we have just 1 weekly backup.  More than a month ago and we have 1 backup per month.  

That selective deletion of older backup setups is very powerful.

Alas, all hard-link based versioned backups have a failure.  The owner, group and permissions aren't also versioned.  It doesn't usually matter, until it does. then it is the difference between a usable backup and lots of data that isn't very useful.  For HOME directories, it usually doesn't matter, but for system level backups over many months, it may become a problem.

Don't believe me. Test it yourself.
```
# work in /tmp/
cd /tmp/
# create a hardlink for /etc/hosts as /tmp/hosts
ln /etc/hosts
# Check the permissions
ls -l /etc/hosts /tmp/hosts
-rw-r--r-- 2 root **root** 270 Mar  6 10:46 /etc/hosts
-rw-r--r-- 2 root **root** 270 Mar  6 10:46 /tmp/hosts

# change the group on /tmp/hosts
sudo chgrp $USER /tmp/hosts
# Check the permissions, again
$ ls -l /etc/hosts /tmp/hosts
-rw-r--r-- 2 root **tf** 270 Mar  6 10:46 /etc/hosts
-rw-r--r-- 2 root **tf** 270 Mar  6 10:46 /tmp/hosts

```

See how both have the wrong group now?  You could change the permissions too, but that isn't safe.

```
# Be certain to put the group back to 'root' on the file.
sudo chgrp root /tmp/hosts
# And clean up that temp file
sudo rm /tmp/hosts
```

I've been burned by this problem.  This is why I use rdiff-backup. It handles versioning of the owner, group, permissions, ACLs, and xattrs correctly.

---

### Post by jajodo on 2023-03-10
> I've been burned by this problem.  This is why I use rdiff-backup. It handles versioning of the owner, group, permissions, ACLs, and xattrs correctly.

I see your point.  Preserving old, in my case undesired, permissions and groups is definitely not my use case.

I don't know much about rdiff-backup.  If that handles versioning the way you need could you use rdiff-backup followed by the cp hard link command to avoid the whole "need to look up the rdiff-backup -r {timespec} command timespec" issue?

---

### Post by TheFu on 2023-03-10
> **jajodo said:**
> I see your point.  Preserving old, in my case undesired, permissions and groups is definitely not my use case.

I don't know much about rdiff-backup.  If that handles versioning the way you need could you use rdiff-backup followed by the cp hard link command to avoid the whole "need to look up the rdiff-backup -r {timespec} command timespec" issue?

No need. That would be extremely inefficient when rdiff-backup is already more efficient than the hardlink method.  Plus, don't touch files with any other tools inside a backup storage area. That's a mandated rule.  Copying files out is fine - rsync, cp, whatever. Viewing and grepping is fine too. Just don't change anything under the backup tool's control, unless you want to corrupt things.

---

