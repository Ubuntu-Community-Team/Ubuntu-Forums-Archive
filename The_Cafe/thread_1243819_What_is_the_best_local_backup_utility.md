---
title: "What is the best local backup utility?"
date: 2009-08-18
forum: The Cafe
---

### Post by lsutiger on 2009-08-18
I bought a WD Passport for the purpose of backing up my laptop. In your opinion, what is the best backup utility and why?

thanx in advance!

---

### Post by approaching on 2009-08-18
rsync

it will do an incremental backup. you probably want the archival mode.

---

### Post by scouser73 on 2009-08-18
I use Pybackpack, it's a nice & clean back up utility.

[[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html")

---

### Post by Baneblade on 2009-08-18
I have only used one "Sbackup" or Simple Backup.
As the name implies, really easy, bulletproof backup utility.

Its got what i call a "n00b mode" where it does everything for you, backing up your files and scheduling the backups in future from then on.

Or for those that like the get custom, a powerful GUI to fiddle to your hearts content! Supports backup to local folder, usb, NAS and remote server.

As im sure you can tell, i like it :)

---

### Post by lsutiger on 2009-08-18
Thanx for the replies! Hey Baneblade, that's one heck of a machine you got there! How old is it? Does the quad core processing make a true difference? Thinking about building a new toy with 4C, but the money could be spent elsewhere...

---

### Post by lsutiger on 2009-08-18
Could someone give me a good example of an rsync command? I read up on it but I am still a bit confused on several things. I read one article and the result was fillning up my / partition.


Thanx again in advance!

---

### Post by approaching on 2009-08-18
you would do something like this
rsync [options] source destination

so if you want to archive your home directory on your external, it should look something like this: (-a is an ok default for what you are probably trying to do, but look at the other options for it, you can get really granular in what you do)
rsync -a /home/user /media/external

feel free to make that a cron job if you keep the two drives connected all the time, otherwise, just make it into a script you can run when you know it can be run

---

### Post by stinger30au on 2009-08-18
quick and dirty backup

[http://sourceforge.net/projects/discspan/](http://sourceforge.net/projects/discspan/)

extract the discspan.py file to the directory you want to backup

start up shell

navigate to the directory u put the discspan.py file to and run

python discspan.py

if it want to know what directory to backup press

.

the fullstop button that will tell it to backup the current directorys and below and let it rip

backups done to cdrw & dvdrw as well

---

### Post by lsutiger on 2009-08-18
How do I backup multiple folders and tell it to omit certain directories with rsync?

E -  I want to backup everything in /home/user (including hidden), and certain folders in the / partition.

Thanx again!

---

### Post by anechoic on 2009-08-18
I've just started using Back in Time for backing up
seems pretty versatile

[http://backintime.le-web.org/](http://backintime.le-web.org/)

---

### Post by oboedad55 on 2009-08-19
> **anechoic said:**
> I've just started using Back in Time for backing up
seems pretty versatile

[http://backintime.le-web.org/](http://backintime.le-web.org/)

Do you run this as root? If not, how do keep file permissions?

---

### Post by anechoic on 2009-08-19
there is a root and non-root version 
that shows up in 'Applications/System Tools' after an install
I always use the root version

---

### Post by cariboo on 2009-08-19
I use grsync, which is just a gui for rsync.

[apt://grsync](apt://grsync)

---

### Post by Cheesemill on 2009-08-19
+1 for Back in Time

---

### Post by paok4 on 2009-08-19
I think what you need is this !!!

[IMG]http://img11.imagehosting.gr/out.php/i380333_about.png[/IMG]

[IMG]http://luckybackup.sourceforge.net/[/IMG][http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)

---

### Post by Rackstar on 2009-08-19
I made script a while back to do this:

1) I plug my backup-drive in
2) Nice notification "Backup device detected"
3) Runs several rsync commands
4) Notification "Backup finished"

It was harder than I expected. If you're interested the code is on my blog:
[http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/)

This made it a lot more easy for me, this forced me into doing backups more.

---

### Post by Ozor Mox on 2009-08-19
I use rsync, it's dead easy.

sudo rsync -av /your/important/folder /your/backup/drive

**-a** means **archive**, which will preserve timestamps, owners, permissions etc. in other words make an exact copy.

**-v** means **verbose**, so that rsync will talk to you in the terminal about what it's doing.

Other useful options:

**-n** means **dry run**, so you can see what rsync will do first before it does it.

**--del** means **delete on destination** so you can clear your backup of files that have been deleted on your live copy. Be careful to get the source and destination right when using this!

---

### Post by approaching on 2009-08-19
i would suggest making a script if you have a bunch of different folders and complicated exclusions, that way it will be easier in the future to both be repeatable and modifiable. for example this backs up your home directory without your porn stash, as well as your web root without those time sensitive log files you probably don't want cluttering up your backup.

myAwesomeRsync.sh
```

rsync -a --exclude 'porn' /home/user /media/external
rsync -a --exclude 'logs' /web/root /media/external/webServer

```

then you just do a chmod on that script like so:
chmod 755 myAwesomeRsync.sh

then you can run it with whatever you want, say chron, or even just by hand
./myAwesomeRsync.sh

that type of flexibility is why i usually would lean towards command line tools instead of gui's, because you know a few things once you run that script. That is exactly what you did last time, and it should still work (ie, you didn't forget to tick some stupid box now all your data is lost). If you decide to do more with it, you already have example code for yourself. And another really big point is that you have invocation options, you could run this by hand, you could run it via another script, you could use cron (which would be the ideal backup system) or any other number of things that linux could let you do with it

that and rsync is wicked fast.

---

### Post by approaching on 2009-08-19
@rackstar

you are awesome

---

### Post by lsutiger on 2009-08-20
Thanx anechoic!

That was exactly what I was looking for! Simple to use and extremely quick. 

All replies appreciated!

---

### Post by lsutiger on 2009-08-20
> **Amberjhons said:**
> So sorry!

Sorry? Huh? What? Sorry?

---

### Post by oboedad55 on 2009-08-20
> **Ozor Mox said:**
> I use rsync, it's dead easy.

sudo rsync -av /your/important/folder /your/backup/drive

**-a** means **archive**, which will preserve timestamps, owners, permissions etc. in other words make an exact copy.

**-v** means **verbose**, so that rsync will talk to you in the terminal about what it's doing.

Other useful options:

**-n** means **dry run**, so you can see what rsync will do first before it does it.

**--del** means **delete on destination** so you can clear your backup of files that have been deleted on your live copy. Be careful to get the source and destination right when using this!

Thanks, this works very well. Is there any way to keep the permissions from changing to root?

Jon

---

