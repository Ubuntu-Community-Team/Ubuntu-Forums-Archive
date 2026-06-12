---
title: "Back up solution."
date: 2011-04-20
forum: Server Platforms
---

### Post by nbrochu on 2011-04-20
Hello all. i just got thrown into ubuntu administration and i was wondering whats the best way to set daily backups of the entire drive to another local drive? would rsync and crontabs work? if so how would i go about this? Thank you all.

---

### Post by usatonycuba on 2011-04-20
> **nbrochu said:**
> Hello all. i just got thrown into ubuntu administration and i was wondering whats the best way to set daily backups of the entire drive to another local drive? would rsync and crontabs work? if so how would i go about this? Thank you all.
Note: Backup is not Just Back-it-up you system (server)..  there are many rules that you may wanna (take care off) when you set your backup strategy.. as you said it.. it most be a "diferent drive" ..  that separate drive it might have >> his own separate system .. do not mixed you software-runnin-apps-Databases- etc, with the Backup drive.. it will a waste of time  (if) crisis-time  comes.

You can use tool name *dd* ... Said that you had two local drives..?  identical size?, */dev/sda* and */dev/sdb*, here is the command to image sda to sdb:
```
$ sudo dd if=/dev/sda of=/dev/sdb
```

**Pd:** Take a look at  [BackupPC]("http://backuppc.sourceforge.net/") it may helps

---

### Post by nbrochu on 2011-04-20
The drives are not the same size. I want to back up the main system to the added drive. Can you make a cronjob to run r sync daily but only back up files that have changed like an incremental to the new hard drive?

---

### Post by collisionystm on 2011-04-20
That is exactly what Rsync does. It only backs up changed files. It doesnt do a new backup every day, just adds the changed file information to the existing.

---

### Post by collisionystm on 2011-04-20
What you would should really look into is Rsnapshot.
 
It does one entire backup of the drive, and then creates folders for each day following. Day1, Day2...etc... inside these day folders are just the files that changed durring that backup. So you only ever do a full system once, and you still have the ability to put back previous files if someone breaks something. You can choose how long you want to span the files for too, you can do a week, a month's worth...etc.

---

### Post by usatonycuba on 2011-04-20
> **nbrochu said:**
> Hello all. i just got thrown into ubuntu administration and i was wondering whats the best way to set daily backups of the entire drive to another local drive? would rsync and crontabs work? if so how would i go about this? Thank you all.
@nbrochu... Yes **rsnapshot** / **rsync** will do the job.. but if you are getting into sys-admin (as you mention before).. Backing-up your system into a **local drive**?
[I]
Ideal solution will be a Backup all your  data to a separate system drive, tape, or  completely separate host. (not locally)... The point is not to back up data on a locally drive. You really want your backups to be as far removed from the system as possible&#8212;even for your personal data at home you most have a backup system in place to copy your most important files to a server out of state. That way, if your house burned down or serious file system corruption hit your server, all important data would still exist.
[/I]

PD:
When I referred to the same size, is the ability of support that Original-Backup-data-size is equal on your newer-disk space (not less)..

---

### Post by collisionystm on 2011-04-20
> **usatonycuba said:**
> @nbrochu... Yes **rsnapshot** / **rsync** will do the job.. but if you are getting into sys-admin (as you mention before).. Backing-up your system into a **local drive**?
 
 
I agree....
 
My stuff goes to the other shop off site. It has an old pc running ubuntu server with a Buffalo Raid 5 storage unit attached. You dont need alot of horsepower to do a backup with ssh. Just grab an old computer, throw in a drive with server, and add a storage unit.

---

### Post by Vegan on 2011-04-20
I went to the trouble to use a shell script to backup my Linux box.

I use my machine as a web appliance so I have a database to contend with along with the web folders.

The script has evolved over time as I learn more about shell programming.

After making a dump of the database I even go as far as to compress it. Same for the web folder that I backed up with tar.

I put a symbolic link to /etc/cron.daily and every day the machine is backed up.

Simpler then you think once you have all of the basic functions figured out.

---

### Post by usatonycuba on 2011-04-20
> **Vegan said:**
> I went to the trouble to use a shell script to backup my Linux box.

I use my machine as a web appliance so I have a database to contend with along with the web folders.

The script has evolved over time as I learn more about shell programming.

After making a dump of the database I even go as far as to compress it. Same for the web folder that I backed up with tar.

I put a symbolic link to /etc/cron.daily and every day the machine is backed up.

Simpler then you think once you have all of the basic functions figured out.

( mysqldump ) do the job... that tool dumps an entire database or databases to the screen. you can even redirect the output to a file or pipe it to a tool like gzip to compress it first .

...I have heard to various system administrators who find this method quite effective .. since you can Backup individual (sys-admin user) databases of the same system/server (specifying the user and password to use).

---

### Post by nbrochu on 2011-04-21
So if i just make a cron job * 0 * * * rsync / /media/New Volume       it will copy everything on the main drive to the new volume every day at midnight, and everyday, it will only copy the files that have changed correct?

---

### Post by nbrochu on 2011-04-21
I just need to have the back ups for now. I will do research and convince my boss to buy more drive so we can have a dedicated backup server.

---

### Post by collisionystm on 2011-04-21
> **nbrochu said:**
> So if i just make a cron job * 0 * * * rsync / /media/New Volume it will copy everything on the main drive to the new volume every day at midnight, and everyday, it will only copy the files that have changed correct?
 
 
 
 
0 0 * * * rsync -rqa /* /media/NewVolume/
 
yes, only changed files.
 
You may want to do this first
 
0 0 * * * rsync -rqa --exclude /proc /* /media/NewVolume/
 
The /proc folder can be time consuming. I am not sure how much data you are copying so I suggest the first night do it with exclude, and the second include it. That way your backups dont overlap.

---

### Post by Paul41 on 2011-04-21
I use this for my home server, don't know if it will work for your proposes or not.

[http://simplebashbu.sourceforge.net/](http://simplebashbu.sourceforge.net/)

---

### Post by collisionystm on 2011-04-21
> **collisionystm said:**
> 0 0 * * * rsync -rqa /* /media/NewVolume/
 
yes, only changed files.
 
You may want to do this first
 
0 0 * * * rsync -rqa --exclude /proc /* /media/NewVolume/
 
The /proc folder can be time consuming. I am not sure how much data you are copying so I suggest the first night do it with exclude, and the second include it. That way your backups dont overlap.
 
 
If you mirror everything like this to your second drive, 
 
If you have a disaster, all you have to do is make it your primary, run a live Cd and install grub. You then have a fully restorable system.
 
Although you may want to use rsync -rqaHpEAXogt
 
check rsync --help for command switch options

---

### Post by nbrochu on 2011-04-21
> **collisionystm said:**
> 0 0 * * * rsync -rqa /* /media/NewVolume/
 
yes, only changed files.
 
You may want to do this first
 
0 0 * * * rsync -rqa --exclude /proc /* /media/NewVolume/
 
The /proc folder can be time consuming. I am not sure how much data you are copying so I suggest the first night do it with exclude, and the second include it. That way your backups dont overlap.

so run the second cmd you posted first then make a cronjob with the first command you posted? Sry for the newbishness.

---

### Post by collisionystm on 2011-04-21
Crontab it. If you run it in terminal and your terminal closes, it stops the job. But set it to run as close to business close as possible, the first run takes quite a while.
 
When you come in the next morning, edit the crontab and remove the --exclude /proc and set your time for whatever you choose.
 
you can use the command
 
```

 
df
 

```
 
to check your disk space
 
 
You can also 
 
```

 
cd /
 
du -chs
 

```
 
to check how large your drive is
 
Then 
 
```

 
cd /media/newvolume
 
du -chs
 

```
 
to see if it matches the same size of your main drive and let you know it got everything.
 
You may want to use 
 
```

 
rsync -rqaHpEAXogt
 

```
 
 
check 
 
```

rsync --help

```
 
In terminal to see what command switches you prefer

---

### Post by nbrochu on 2011-04-21
Thanks so much i just did that and i will check it in the morning. As a newb, i find it hard to remember all the switches for different commands and what they do. Does that knowledge come over time or do advanced users like you guys still use man pages?

---

### Post by collisionystm on 2011-04-21
I dont use man pages. I google and use the --help when its available. Googling is faster than these forums.

---

### Post by usatonycuba on 2011-04-21
> **nbrochu said:**
> So if i just make a cron job *** 0 * * *** rsync / /media/New Volume       it will copy everything on the main drive to the new volume every day at midnight, and everyday, it will only copy the files that have changed correct?
I guess it is more tricky than that.. why you do not make  implementation with a full potential?.. take a tour at Mikes tutorial >> [Easy Automated Snapshot-Style Backups with Linux and Rsync]("http://www.mikerubel.org/computers/rsync_snapshots/").. it is old, but you will have a sufficient bases to get your solid-ground.. IMHO

Anyway.. a rsync cron job basicly is just like :  *rsync -a source/ destination/*... The string to use a "daily" back up it will be [COLOR="DarkRed"]@daily[/COLOR] Wich Runs once a day >>>>  [COLOR="DarkRed"]0 0 * * *[/COLOR], also you have  [COLOR="DarkRed"]@midnight[/COLOR] (wich runs same as [COLOR="DarkRed"]@daily[/COLOR])... it will be something like:

    
```
crontab -e
0 0 * * * rsync /data/backups/*  /media/New Volume/backups -avz
```
> **nbrochu said:**
> I just need to have the back ups for now....
Why then you just do "make".. a complete image of your drive..?

---

### Post by nbrochu on 2011-04-21
what software is recommend to do this?

---

### Post by usatonycuba on 2011-04-21
> **nbrochu said:**
> what software is recommend to do this?
As I posted:
> **usatonycuba said:**
> Note: Backup is not Just Back-it-up you system (server)..  there are many rules that you may wanna (take care off) when you set your backup strategy.. as you said it.. it most be a "diferent drive" ..  that separate drive it might have >> his own separate system .. do not mixed you software-runnin-apps-Databases- etc, with the Backup drive.. it will a waste of time  (if) crisis-time  comes.

You can use tool name *dd* ... Said that you had two local drives..?  identical size?, */dev/sda* and */dev/sdb*, here is the command to image sda to sdb:
```
$ sudo dd if=/dev/sda of=/dev/sdb
```

**Pd:** Take a look at  [BackupPC]("http://backuppc.sourceforge.net/") it may helps
[BackupPC]("http://backuppc.sourceforge.net/") is one of my favors..

Remember, Imagin is not a really Backup strategy IMHO, but as you stated tha *just need to have the back ups for now..*..  [COLOR="DarkRed"]**IMPORTANT**[/COLOR]...while you are (goin to) imaging a drive, make sure that the drive not be in use, so be sure that any file systems on a drive are unmounted.

---

### Post by nbrochu on 2011-04-21
ok cool. What we want to do is make it so that if the server drive fails, we can swap in a backup drive so no information, shares, or applications are lost. 
Would making a drive image and the also running daily backups on a separate drive be idea for that?

---

### Post by usatonycuba on 2011-04-21
> **nbrochu said:**
> ok cool. What we want to do is make it so that if the server drive fails, we can swap in a backup drive so no information, shares, or applications are lost. 
Would making a drive image and the also running daily backups on a separate drive be idea for that?
An image is a complete bit-for-bit copy of a drive... like the original one, I wanna call it a >> CLONE.. so?..  ...but as 	I said *Imagin is not a really Backup strategy*.. it works as One Time fully Secure Backup, of your complete Driver.. as a Clone... ...But as other user are mention, if you planning to do your regular system Backups (As you might be).. you have to use (implement) different tools, sofftware, etc..

Pd: I do not recommend that you use more than one at the same time.. lets said that *Imagin is not a really Backup strategy, and is Just a One Time fully Secure Backup* .. so, if you try to make a image, Do not do it along with your permanent (daily, hourly, etc..) Backup tool/soft.. etc.

EDITED: take a look at this thread [http://ubuntuforums.org/showthread.php?t=1734688]("http://ubuntuforums.org/showthread.php?t=1734688")

---

### Post by nbrochu on 2011-04-22
0 0 * * * rsync -rqa --exclude /proc /* /media/NewVolume/

i entered this into my crontab last night, and when i went to check the backup today, it did not happen. any ideas?

also is there a special file name i need to save this as?

---

### Post by collisionystm on 2011-04-22
> **nbrochu said:**
> 0 0 * * * rsync -rqa --exclude /proc /* /media/NewVolume/

i entered this into my crontab last night, and when i went to check the backup today, it did not happen. any ideas?

also is there a special file name i need to save this as?

If you change directory to that volume

```

cd /media/NewVolume

```

There is nothing there?

Are you sure your drive is called NewVolume?

Is it formatted?

---

### Post by nbrochu on 2011-04-22
yes it is formated with ext4 and partitioned.
and the only thing there is a lost and found folder thats locked down. I have no idea what that is.

---

### Post by collisionystm on 2011-04-22
Instead of SDA1 just do SDA

---

### Post by usatonycuba on 2011-04-22
Wondering... Have you installed Rsync?  *sudo apt-get install grsync*
[QUOTE=nbrochu]..yes it is formated with ext4 and partitioned.[/QUOTE]
You migth wanna take look at your /etc/fstab (static file system information).. an see if your /dev/sda1 << where your file system are supposed to be Mounted on.. has  ext3 or ext4..?

OK, @nbrochu .. IMHO... you mentioned that you need a **ups backup** of your system .. if that were my case .. then what I do is an image of my hard drive ..?

Now, if you need to make your your daily backups.. there are few  softwares/tools that will had the job done for you...  ...then I think implementing a cron job, script, or anything also (by hand) I guess is not as efficient as your're looking for .. You can use software to do all the work for you, and you do not have to be mess around with the command line.

But as I said IMHO ..GL

---

### Post by collisionystm on 2011-04-22
> **collisionystm said:**
> Instead of SDA1 just do SDA

WOW, sorry about that. I replied to the wrong forum lol.

Do this,

Manually run the rsync command in a terminal and see what the output is. 
You can stop the process with CTRL+C
Verify its running correctly.

Just make sure you remove the -q ( Q ) from your rsync command and include --progress so you have a visual.

---

### Post by TheFu on 2011-04-23
> **nbrochu said:**
> So if i just make a cron job * 0 * * * rsync / /media/New Volume       it will copy everything on the main drive to the new volume every day at midnight, and everyday, it will only copy the files that have changed correct?

This works for regular files, but it is dangerous for DBMS files.  For MySQL, it is ususally just easiest to dump the DB to text files and perform regular file-based backups. During recovery, you'll need to import that data into the DBMS file(s) since those files will probably be corrupted.

For backups, rsync is NOT the best answer.  Like others have suggested, rsnapshot or rdiff-backup will provide incremental backups, while still being storage efficient and FAST.

If you need a GUI, Back-In-Time uses hardlinks to store many versions of your system over time (after the first full copy is made to alternate media).  Highly recommended for new users. The GUI isn't needed after it is setup.

As you become more advanced, you'll probably migrate to Amanda for backups.

Duplicati is another backup tool with a GUI.  It works like legacy tape backup tools do, which can be a major hassle.

We use rdiff-backup since the command is almost the same as rsync, but the features far surpass what you get with rsync. The latest backup appears like an rsync mirror, but you can go back days, weeks, or months with a simple restore command. Here we keep 30 days of incremental backups and that adds just 10% added storage to the backup areas. Why wouldn't you do that for 1.10x the storage of the original?

---

