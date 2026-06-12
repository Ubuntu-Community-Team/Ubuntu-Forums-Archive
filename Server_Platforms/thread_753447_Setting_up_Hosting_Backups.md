---
title: "Setting up Hosting Backups"
date: 2008-04-12
forum: Server Platforms
---

### Post by girasquid on 2008-04-12
Hello, all.

I currently have a server configured with Ubuntu 7.10 Server - but no backups(yet).

It has 3 80GB drives inside of it - 2 SATAs, and one IDE. The 2 SATAs are mirrored to each other, and the IDE drive is intended as a drive to store my nightly/weekly backups on. This is what **sudo fdisk -l** spits out:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076ac1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9401    75513501   83  Linux
/dev/sda2            9402        9729     2634660    5  Extended
/dev/sda5            9402        9729     2634628+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62a3fa1b

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076ac1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9729    78148161   83  Linux

```
Now, I would like to set up some sort of backups, so that they are available any time I need to roll my server back to a particular state, or just in case one of the drives fails. I am writing this post to try and get a comprehensive backup solution figured out.

I was thinking that in order to keep my MySQL databases backed up, I could run **mysqldump** every 3 hours, and then write some logrotate rules to rotate my mysqldumps - would this do the trick for keeping my database backed up?

I am not sure what other folders I need to back up. All of the sites I am hosting have users on the system, so all of their logs and site content is stored within **/home/foo** - which means I definitely need to back up **/home**. But what else do I need to back up?

I am not sure how to set up my IDE drive with the proper partition scheme for me to be able to keep my backups on it - ideally, what I would like to have is another folder available on the root called something like **/backups**, which would then have folders like **/mysql, /sites**, and so on. Inside those folders, I'd like to have something like **/hourly** for mysql, and **/nightly** for my other folders. 

Does this seem like a good backup plan? How would I set up my IDE drive to accomplish what I'm looking for? Does anyone know which folders I've missed that I will definitely need to keep backed up? What could I use to keep nightly backups of particular folders, and what could I use to rotate my backups?

Thanks for all the help.
Girasquid

---

### Post by tamoneya on 2008-04-12
try to back them up to a different physical computer.  Currently if you have a fire or something you loose everything.  Try to put a computer at a friends house or at work or something and you should place your backup files on there instead via ssh/scp.

---

### Post by hyper_ch on 2008-04-12
well, do you just want to backup the data or imaging the drive?

---

### Post by girasquid on 2008-04-12
Right now I'm primarily interested in backing up the data.

Backing up over ssh/scp is definitely something to look into later - but at the moment, I don't have another machine/area to keep more drives in, and I can't afford to buy any more. I'm primarily concerned with just having **some** sort of backup solution in place for the time being.

---

### Post by hyper_ch on 2008-04-13
then I would use rsync

---

### Post by andguent on 2008-04-13
If you simply are interested in keeping another copy on another drive, then your directory structure really doesn't matter as long as you keep it organized and it makes sense.

* Always always always backup the /etc directory. There is a lot of good stuff in there. 
* If running apache, make sure you grab /var/www. 
* If using samba, then backup /var/lib/samba. 
* Hopefully you aren't keeping much in /root, but I sometimes back it up anyway in case I'm leaving notes for myself there or those silly .conf.bak.bak.old.bak files.
* I save all of my custom scripts to /usr/local/bin, make sure you back those up too. Backing up your backup scripts will help you decode what data goes where if you ever have to fall back on these backups.

To find out what files a daemon is using, try this: 
lsof |grep ^apache


As for directly above, I agree that rsync is definitely handy for making effecient backup scripts. When you do get that second box, rsync will very easily migrate from a destination of /opt/backup to server2:/opt/backup. SSH keys make this possible.

The next tier up from rsync would be the boxbackup project or something similar. Boxbackup can be a bit complicated to setup, but invaluable if configured right. I've gotten the call that confirmed the worst -- server is down, single hard drive is dead. We then installed boxbackup to a spare machine, pulled down the latest snapshot of the data, and had a replacement server up and running in 4-6 hours.

---

### Post by girasquid on 2008-04-14
Thanks for the recommendations, rsync is probably what I will be doing for now.

So I'll need to backup /etc, and /home - I don't need to worry about /var/www, as I've tweaked Apache and my virtualhosts to store all sites within /home directories. All of my custom scripts are within /usr/share - do I need to backup the entire /usr directory?

I know how to write a script to do my backups for me and setup a cronjob to run it - can anyone tell me what I need to do to partition/format my IDE drive(without wiping my SATA raid'd drives) so that I can use it as a backup drive, and auto-mount it to /backup? (Last time I partitioned/formatted, I partitioned the wrong drive and ended up losing everything)

Thanks Again,
Girasquid

---

### Post by andguent on 2008-04-14
/usr is full of installed programs. Assuming that archive.ubuntu.com doesn't get hit by a meteor, you can ignore the rest of that directory. Grab anything you have customized manually, and /home + /etc is 98% of that.

According to your fdisk dump, you already have it partitioned correctly. Have you tried just doing a 'mount /dev/hdb1' or maybe a 'mkdir /opt; mount /dev/hdb1 /opt'?

---

### Post by girasquid on 2008-04-14
Great, it looks like mounting that drive worked fine. It's got the lost+found file, but that's all - is that fine? Will I be able to pull files off of that drive if, at some later time, I need to recover something?

Do you know what I would need to put into my fstab to make it easier to mount to /backup?

Also, this is a bit of a wear-and-tear question: do I stand to gain anything by leaving the IDE drive unmounted until the times when I move backups to it, and unmounting it afterwards? Or are the gains so small it'd be fine to just leave the drive mounted constantly? It will only be getting accessed for backups.

---

### Post by andguent on 2008-04-14
Yes. Having a lost+found directory and nothing else means it is a fresh drive for use. Lost+found always shows up on all drives. If files appear in lost+found, they were damaged and a disk scan found partial files.

This mount command can be used any time, and files saved there will be saved there until deleted, formatted, or until the drive dies.

I personally would say leave it mounted all the time. Unless it is a removable or external drive, there really isn't any advantage to unmounting. It will still be powered on even if you don't have it mounted.

Add this line to the bottom of fstab, AND MAKE SURE TO NOT MODIFY ANY OTHER LINES:
```
/dev/hdb1 /backup               ext3    defaults,errors=remount-ro 0       1
```

Then try these commands:
umount /dev/hdb1
mount (visually search for anything hdb1)
mount -a

That last command, 'mount -a' should automatically try to mount everything in /etc/fstab that currently isn't connected. If that mounts /backup correctly, then it should automatically connect to hdb1 on reboot. Feel free to test that too.

---

### Post by girasquid on 2008-04-14
Great - I tested it out, and it **does** mount /backup properly, on reboot as well.

Right now my plan for rsync is to write a Perl script that will go through my /etc, /home, and /usr/share directories and use **rsync -tra <directory> /backup/nightly/date/<directory> > /var/log/backups/<directory>.log** on each of the directories I need to back up.

Is this a good way to do things, or is there a better way?

---

### Post by andguent on 2008-04-14
It is definitely possible to do it that way. I personally would just do a bash script rather than perl, but only because I know it better. Perl is known for running faster than bash.

If doing it in bash/sh, you can do something like:
```

#! /bin/sh
mkdir -p /backup/nightly/`date +%Y-%m-%d`
rsync -vax /etc /backup/nightly/`date +%Y-%m-%d`

```

Whichever way you do it, I highly recommend the -x on the rsync. It prevents rsync from sprawling across to other disks/servers.

---

### Post by girasquid on 2008-04-14
Okay, I'll keep that in mind.

I also need to keep backups of my MySQL databases; at the moment I was planning on just running mysqldump periodically, but I'm wondering: is there a better way?

---

### Post by hyper_ch on 2008-04-15
you could turn of mysql and then copy the actualy database binaries... but this is always a risk... I'd mysqldump...

---

### Post by andguent on 2008-04-15
Agreed. Mysqldump is the way to go, as you don't have to stop the running database. If at all possible, test importing the database later, possibly on another machine.

---

### Post by girasquid on 2008-04-15
Alright, so mysqldump is what I'll be doing to keep MySQL backed up.

I have multiple databases currently, and I was planning on only running the single mysqldump - does anyone know how easy it will be to restore only one database in particular?

---

### Post by hyper_ch on 2008-04-15
[http://howtoforge.com/faq/6_4_en.html](http://howtoforge.com/faq/6_4_en.html)

---

### Post by rickyjones on 2008-04-15
Just a side-note to the OP: Have you tested your mirrored away to ensure that it is indeed mirroring the data? I just wanted to post that so it didn't get overlooked.

Sincerely,
Richard

---

### Post by girasquid on 2008-04-15
Actually, I haven't - I'd like to, but I have no idea how to(and the box is in a colo facility, so access isn't that easy to get). Do you know how I'd test it to be sure?

Thanks for the link, hyper_ch - will that work if I have a global mysqldump, and only need to restore a single database?

---

### Post by rickyjones on 2008-04-15
> **girasquid said:**
> Actually, I haven't - I'd like to, but I have no idea how to(and the box is in a colo facility, so access isn't that easy to get). Do you know how I'd test it to be sure?

The only way I know how would be to contact one of the guys at the colo and have them power down the server and unplug one hard drive. Power it on and see if it boots. Rinse and repeat with the other hard drive. A successful RAID1 will boot using either drive. If it fails on either drive then you know the RAID is not properly configured.

Sincerely,
Richard

---

