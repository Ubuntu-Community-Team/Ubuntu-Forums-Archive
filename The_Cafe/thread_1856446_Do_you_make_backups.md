---
title: "Do you make backups?"
date: 2011-10-08
forum: The Cafe
---

### Post by person287 on 2011-10-08
Hi,
I'm doing a post for [my site](http://silicoxvalley.com) and I was wondering do you make backups, and if yeah how often?
If you do or don't, it'd be great if you could vote on my [Poll](http://poll.fm/3bbya), and if you use a program then could you tell me here.
Thanks, Ed

---

### Post by collisionystm on 2011-10-08
> **person287 said:**
> Hi,
I'm doing a post for [my site](http://silicoxvalley.com) and I was wondering do you make backups, and if yeah how often?
If you do or don't, it'd be great if you could vote on my [Poll](http://poll.fm/3bbya), and if you use a program then could you tell me here.
Thanks, Ed

yeah, rsnapshot. Backups 5 linux servers and 2 Windows every night of the week.

---

### Post by CharlesA on 2011-10-08
I just use rsync myself, but +1 to rsnapshot.

---

### Post by markp1989 on 2011-10-08
I only back up things that are not replaceable, like uni coursework.

I use dropbox on all my machines, so its instantly on all my machines, my file server also take an hourly copy of the dropbox folder on to a different local drive just encase something happens to my account.

the local dropbox backup is also rsynced to a remote, server every 24 hours.

I don't back up my music or movies as it would cost too much to remotely back them up, and if the worst happens I can always re rip them.

---

### Post by rudihawk on 2011-10-08
I backup stuff that I can't replace. 

Photos and University stuff mostly.

---

### Post by mr-woof on 2011-10-08
I've just started to use Rsync for my backups, in the past id just copy everything to an external hd. 

For a new rsync user, what options would people recommend? Im on my netbook at the moment, so dont have the sh file handy, but i think i'm using azv --progress --delete. 

Internal hd to external drive

---

### Post by CharlesA on 2011-10-08
I use rsync -ai most of the time.

---

### Post by mr-woof on 2011-10-08
whats the benefit of using ai?

---

### Post by CharlesA on 2011-10-08
-a = --archive - recursive/preserve permissions
-i = --itemize-changes - shows what's going on. You can also use -v I believe.

Man page can be found [here]("http://linux.die.net/man/1/rsync"). ;)

---

### Post by mr-woof on 2011-10-08
:) I've been impressed with it so far, the sync is very quick after the first complete backup

---

### Post by CharlesA on 2011-10-08
> **mr-woof said:**
> :) I've been impressed with it so far, the sync is very quick after the first complete backup
Yep, it only sends the part of the file that has changed. Very nice.

---

### Post by beercz on 2011-10-08
I use rsync and rsnapshot - up to 5 times per day - to an encrypted external USB hard disk and spare PC with a massive hard disk.

I have a lot of confidential data and I've been doing this for years and have never lost a thing!!

---

### Post by wolfen69 on 2011-10-08
Doesn't anybody believe in copy/paste to an extra hard drive(s)? Or is that too old school?

---

### Post by beercz on 2011-10-08
> **wolfen69 said:**
> Doesn't anybody believe in copy/paste to an extra hard drive(s)? Or is that too old school?
Takes too long, I have 350 Gb of data to backup - rsync (and rsnapshot) only backs up new or modified files, takes less than 20 minutes.

---

### Post by wolfen69 on 2011-10-08
> **beercz said:**
> Takes too long, I have 350 Gb of data to backup - rsync (and rsnapshot) only backs up new or modified files, takes less than 20 minutes.

I don't recopy anything. Anything new I get that I want to keep automatically gets copied to my storage drives. I don't download huge files most of the time, so it's easy to copy/paste. Plus, I don't save much stuff anymore. So there!

---

### Post by jchw on 2011-10-08
I use Deja Dup backing up to a USB memory stick on a daily basis.  Deja Dup works fine and I have reinstalled a few times with complete success.   While Deja Dup restores my setting and bookmarks etc for the desktop, Thunderbird and Firefox I have to manually reinstall some of the additional programs I have loaded like fslint, Googleearth, unetbootin and Crossover. This is usually very quick once the restore is completed.

---

### Post by IWantFroyo on 2011-10-08
I used to use BackInTime. Now I just use a USB drive. Most of my data is in text documents.

---

### Post by jonkiribati on 2011-10-09
I used backup-manager to backup some servers and it seems to be great.

---

### Post by Paqman on 2011-10-09
I don't.

Anacron and rsync take care of it all for me, I never lift a finger.

---

### Post by Lucradia on 2011-10-09
I do not make backups, as all of my documents are permanently stores (the ones I keep anyway) on a 32 GB flash drive. Anything else, like, temporary art I change, temp. texts, temp. anything, is removed when I reformat the harddrive. I do not ever store installers, etc. unless it's for old stuff like ffdshow that will never be updated as it was back then.

This is also why I have no need, whatsoever, for cloud storage save for picasaweb for my wallpapers and things I don't really need to actually keep, but want to see every now and then (like, months and months, even years, until I look at it again.)

Windows may make backups using the system recovery dealie, but that's Microsoft's doing, not mine.

---

### Post by keithpeter on 2011-10-09
+1 rsync but only a couple of hundred Gb

I use --delete option for one external hard drive which then has an exact copy of what is on the hard drive of this PC

I have another much larger external hard drive where I run rsync without the --delete option, so everything is kept, even when I delete files from the hard drive pc.

Finally, I use a dropbox account to keep working files in, mostly ODT documents of handouts, but also a copy of my web site. I use dropbox as I need to sync with a windows laptop.

---

