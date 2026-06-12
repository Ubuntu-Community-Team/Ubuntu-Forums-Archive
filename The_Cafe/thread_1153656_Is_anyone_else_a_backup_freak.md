---
title: "Is anyone else a backup freak?"
date: 2009-05-09
forum: The Cafe
---

### Post by HappyFeet on 2009-05-09
I have my main install on 1 drive, and keep all personal (important) files on another. And then I back it up 3 more times on various hard drives/partitions/usb drives. I don't take any chances. Plus it allows me to play around with my main install no matter what distro it is. All my stuff is always ready to go. Anyone else the same way?

---

### Post by Polygon on 2009-05-09
i run a backup that backs up to an external drive every day. yay for rdiff-backup.

---

### Post by Newuser1111 on 2009-05-09
I don't backup.

---

### Post by aurelieng on 2009-05-09
Same here: three main backups (one on a RAID1 external disk, two in anoter geographical locations among which one with backup history over two month at least). Plus two  more on external disks, just in case... ;)

---

### Post by HappyFeet on 2009-05-09
> **aurelieng said:**
> Same here: three main backups (one on a RAID1 external disk, two in anoter geographical locations among which one with backup history over two month at least). Plus two  more on external disks, just in case... ;)

I don't do RAID, but I see your point. Glad to see I'm not the only one.

---

### Post by I-75 on 2009-05-09
I started backing up AFTER I lost a computer AND tunes that were in the computer due to a bad electrical storm three years ago. I learned my lesson. 



I try to do double back up when possible and recently started doing "data disc" file save on DVD. DVD can be cheaper than a external hard drive,  $22 for 100 blank DVDs on sale is less expensive than a 320 GB hard drive for $70.

---

### Post by Zack McCool on 2009-05-09
I have been working in IT for a VERY long time (it seems).  I have seen the effects of bad or missing backups, and have made the mistake a couple of times myself...

These days, My main system has 2 internal drives with several partitions.

Important data is backed up every 6 hours, using a GFS scheme, with rsnapshot to a USB drive.  The drive gets mounted, the rsnapshot happens, the drive gets unmounted.

Then, the Media files are rsync'ed to a small NETGEAR SAN drive once per day.

My server is a VMWare ESX server with a 12 Drive RAID 5 array.  I back up the important data from the servers using Rsync to a NAS drive.  The data here is my personal photos, and that kind of stuff.  The drive is located right by the front entrance to my house.  If I have to leave in a hurry, this is the last thing I grab while going out the door.

Also, the workstation has live images done, every Monday morning, of the /, /usr and /home partitions.  

Last time I blew up my main system, it took me about an hour, from start to finish, to have it back up and pretty much identical to what it was before I accidentally deleted that partition...   ;)

You cannot have too many backups.

---

### Post by Zack McCool on 2009-05-09
> **I-75 said:**
> I started backing up AFTER I lost a computer AND tunes that were in the computer due to a bad electrical storm three years ago. I learned my lesson. 
 That's the way it happens for most people...   ;)

> 
I try to do double back up when possible and recently started doing "data disc" file save on DVD. DVD can be cheaper than a external hard drive,  $22 for 100 blank DVDs on sale is less expensive than a 320 GB hard drive for $70.

Sure, but backing up to DVD takes more time and requires active participation.  A backup to an external hard drive is very quick, and can be completely automated and scheduled...

---

### Post by FuturePilot on 2009-05-09
I never used to be, but recently I've turned into one. And it's a good thing too because a little while back I needed to fall back on those backups, thank goodness I had them. 

I use Sbackup on all my computers to do weekly backups of my /home as well as any important system files and I've recently started doing disk images every few months.

---

### Post by aurelieng on 2009-05-09
AFAIK, the lifespan of DVD is also quite low, slightly above one or two year, but probably not much more...

---

### Post by HappyFeet on 2009-05-09
And I have a UPS.

---

### Post by JK3mp on 2009-05-09
I am for my home server i suppose. I have it back up to a 1Terabyte external drive daily. Plus it also backs up to an second partition on the drive too so i can mess with install (as you stated, change software and if all goes bad...just reinstall fresh, fall onto backup and be back in business :-P )

---

### Post by Orlsend on 2009-05-09
I use remastersys. I have fully done a backup that can be installed as a distro.

---

### Post by HappyFeet on 2009-05-09
> **aurelieng said:**
> AFAIK, the lifespan of DVD is also quite low, slightly above one or two year, but probably not much more...

Not true. Blank cd's can often outlast manufactured recordings.

---

### Post by HappyFeet on 2009-05-09
> **Orlsend said:**
> I use remastersys. I have fully done a backup that can be installed as a distro.

I've found remastersys pointless. It's so easy these days to have instant gratification, that it's almost a moot point, if you back up well.

---

### Post by lisati on 2009-05-09
I've got three external hard drives, one of which has "gone south" (dropping it some months back probably didn't help). The surviving two contain mostly backups of video footage I've shot over the years that I might want access to and assorted Windows stuff, but I think I'll have to pull finger one day and remove duplicates.

---

### Post by keith.newell on 2009-05-09
I have a 2tb internal raid that holds my home directory, but i also have a 1gb external raid that i regularly backup to.  You can't be too careful.  :)

---

### Post by HappyFeet on 2009-05-09
> **keith.newell said:**
> I have a 2tb internal raid that holds my home directory, but i also have a 1gb external raid that i regularly backup to.  You can't be too careful.  :)

I thought *I* was bad. Whatever floats yer boat. It's all about doing what's comfortable for you.

---

### Post by itsStephen on 2009-05-09
I've never made a backup in my life

---

### Post by juancarlospaco on 2009-05-09
I use** Back In Time**, but mostly for the *"go back in time"* thing...

---

### Post by lisati on 2009-05-09
> **juancarlospaco said:**
> I use** Back In Time**, but mostly for the *"go back in time"* thing...

Isn't that a song by Huey Lewis? (BTW: "Back to the future III" is on the box in my area tonight, I *might*  give it a miss since I can watch it on DVD any time, one of the alternatives is the Steve Martin version of "Pink Panther" on another channel, haven't seen it yet)

---

### Post by k2t0f12d on 2009-05-09
> **lisati said:**
> \BTW: "Back to the future III" is on the box in my area tonightI'll be watch BttF3 in Auckland :P

---

### Post by juancarlospaco on 2009-05-09
[[IMG]http://backintime.le-web.org/img/backintime/gnome/mainwindow.png[/IMG]]("http://backintime.le-web.org/download_page/")

---

### Post by lisati on 2009-05-09
> **k2t0f12d said:**
> I'll be watch BttF3 in Auckland :P

Enjoy. It's awesome with surround sound.

---

### Post by hessiess on 2009-05-09
I store everything in an SVN repo, makes syncing my 2 computers easier and anything that is on one is also backed up on the outher.

---

### Post by MikeTheC on 2009-05-09
Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep!

---

### Post by FuturePilot on 2009-05-09
> **MikeTheC said:**
> Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep! Beeeeeeeeep!

oh I see wut u did thar.

---

### Post by Rackstar on 2009-05-09
I needed to force myself doing backups from my laptop more. 

So I decided to write a script that uses the libnotify-send to get a nice notification that my backup is starting when I hotplug my external HDD, and get a notification whenever my backup is ready.

Using a combination of rsync commands, the whole backupprocess only requires 5 minutes. It wasn't that easy to get the notifications running. I wrote a how to about it:
[http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/)

---

### Post by mingtien on 2009-05-09
I do a Remastersys backup of the OS once a month (just so I don't have to download all the packages again -- Internet is slow here).  ISO image on an external HD and I always burn it to DVD and test it as well.

I do a weekly full backup and daily incrementals of /home, /var and /boot to an external HD using Simple Backup

All files for work get backed up in the /home backup, but also get copied to a separate partition daily.   Crucial documents, contact lists, and configuration files get replicated to Google and Dropbox. 

So I'm pretty much ready for a new OS install at any time, although I'm so pleased with Jaunty I believe it will be my main OS until December, when KK becomes available.

Rackstar -- nice script and it's a great idea -- I'm going to try it :)

---

### Post by Rackstar on 2009-05-09
> **mingtien said:**
> 
Rackstar -- nice script and it's a great idea -- I'm going to try it :)  Do you think it will work with a firewire-connected drive?  (the drive also has USB, but my 3 ports are very much in demand)

Thank you! You made my day! I got little response on my blog, so I thought it might be less of a great idea than I thought in the first place. But I think it's running smoothly.

It uses udev-rules to recognize devices, as udev is for all devices, firewire should work. There is a link to a good udev tutorial website.

---

### Post by richg on 2009-05-09
I have been using a Firewire external drive for nearly four years. The drive is only powered up for backups.

I started doing this with 98SE and had two folders, one for MS stuff, one for Linux stuff. Never, ever had a need to partition or format the drive. Linux read all MS files. Got rid of MS drive with an older PC.

I back all the data up to a DVD maybe every two months, break the old DVD, and throw it away.

I use a drive rack in my desktop PC. A key unlocks, remove drive, insert another drive, lock drive, boot up. One OS, one drive. Never ever a dual boot issue. I have two more drives to play around with. Drives are cheap enough.

A second drive has identical install so if first drive fails, I can be back up in the time required to switch drives. Very easy to install the same OS on a second drive.

If you ever have a drive fail with data on it, you will think twice about backing up data.

My way. Your mileage may vary.

Rich

---

### Post by happysmileman on 2009-05-09
I don't really backup, generally before switching distro I copy my home directory to my external drive... So worst case scenario I have a fairly old backup of my firefox directory and my KWallet password file, so i can still get to my email and most websites (and through "forgot password" I can get to the rest).

I don't have backups of my music or videos because I don't have the space, I have an 80GB harddrive in my computer, and a 250GB external, so all my music and video will only fit on the external, and thaqt's running out of space.
In the future if I can justify spending money on another hard drive purely for copies I'll get it, but right now I'm not even sure if I can afford another external when this one is full.

---

### Post by dragos240 on 2009-05-09
I dont backup.

---

### Post by beercz on 2009-05-09
To answer the OP's question - Yes!

I have an automated backup system using [rsnapshot]("http://rsnapshot.org") to backup from my laptop to my home server.  I have written a very tiny bash script that runs in cron (at 11:30pm daily) that runs rsnapshot over ssh (using keys) to my laptop and writes the backup to a log file.

I have been in the IT industry nearly 20 years and have never lost anything important!

---

### Post by dLeon on 2009-05-09
I do backups. About quantity... well I think I can count my self as backups freak. At least one data backup a day, usually come out more than two.

Quote from Linus T:
Backup is for looser, mirror your data so everybody can have the copies. [http://ubuntuforums.org/images/smilies/icon_surprised.gif](http://ubuntuforums.org/images/smilies/icon_surprised.gif)

D#$N I'm a big looser...

---

### Post by mingtien on 2009-05-09
> **Rackstar said:**
> Thank you! You made my day! I got little response on my blog, so I thought it might be less of a great idea than I thought in the first place. But I think it's running smoothly.



Well, I should also tell you then -- I sent the link to an old mate from my Uni days (who is now a systems administrator), and he thought the idea of using udev was brilliant :)

---

### Post by chellrose on 2009-05-09
(Newbie alert)

I try to back up relatively often, although apart from manually burning files to CD, or putting them on a USB stick, I haven't got a clue how to do it... :)

---

### Post by dLeon on 2009-05-09
> **Sissy13 said:**
> (Newbie alert)

I try to back up relatively often, although apart from manually burning files to CD, or putting them on a USB stick, I haven't got a clue how to do it... :)

Make ISO for your data then burn the ISO to CD.

---

### Post by chellrose on 2009-05-09
> **dLeon said:**
> Make ISO for your data then burn the ISO to CD.

Thanks.  But how does one make ISO for data?

---

### Post by richg on 2009-05-09
I only have 4gb of data so I copy and paste to my external. Very easy.

Rich

---

### Post by dLeon on 2009-05-09
> **Sissy13 said:**
> Thanks.  But how does one make ISO for data?

I use 'geniso' command line for my everyday work making ISO and use 'cdrecord' to burn. But, Brasero or K3B able to help you make ISO + burn it for you with pretty GUI interface and may easy to understand. Other GUI interface burner tools also available in repository. Search for 'ISO', 'Burn', CD/DVD or anything like that.

---

### Post by chellrose on 2009-05-09
> **dLeon said:**
> I use 'geniso' command line for my everyday work making ISO and use 'cdrecord' to burn. But, Brasero or K3B able to help you make ISO + burn it for you with pretty GUI interface and may easy to understand. Other GUI interface burner tools also available in repository. Search for 'ISO', 'Burn', CD/DVD or anything like that.

Thanks for the info.  I'll give it a go. :)

---

### Post by Rackstar on 2009-05-10
> **mingtien said:**
> Well, I should also tell you then -- I sent the link to an old mate from my Uni days (who is now a systems administrator), and he thought the idea of using udev was brilliant :)

Alright! Best Sunday morning ever!

---

### Post by HavocXphere on 2009-05-10
I sync the *important* stuff (<0.0001% of my data) to Dropbox. And I occasionally also email that stuff to myself since I really really can't have that stuff go AWOL.

Everything else (99,999%) is on a happy-go-lucky approach to data safety.:)

---

