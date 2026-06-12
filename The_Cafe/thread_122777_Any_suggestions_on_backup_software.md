---
title: "Any suggestions on backup software?"
date: 2006-01-28
forum: The Cafe
---

### Post by Amon_Re on 2006-01-28
It must be able to backup to dvd :)

---

### Post by mstlyevil on 2006-01-28
[QUOTE=Amon_Re]It must be able to backup to dvd :)[/QUOTE]

I don't know of any good backup software but I just back up all my documents, and other files on to CD/DVD. I just find it easier to burn this stuff on to disk so when I format all I have to do is just copy and paste it back in to my Home file. I really do not care about backing up my settings since I like to change things constantly anyhoo.

---

### Post by briancurtin on 2006-01-28
i just use K3B/GnomeBaker to copy my home folder to DVD(s)

on windows i used some Nero backup utility when my system was going down, and that was a bad idea. ive had these backup DVDs for 8 months and have no way to get the data off of them without getting a windows computer with nero installed, that has a DVD reader/writer. im sitting here with 9 DVDs full of my old music, pictures, and videos...thank god iPods connect as USB hard drives so you can just dump the music from there or id have been completely screwed

---

### Post by Amon_Re on 2006-01-28
Well, the ability to do incremental backups with selected/deselected files would be a plus.

Remote backing up of a server (through ssh eg) with said features would even be better

---

### Post by briancurtin on 2006-01-28
id actually like a similar thing, which is why i posted (but forgot to add in that part, sorry about that)

---

### Post by majikstreet on 2006-01-28
I've heard of rsync which can do remote backups.. not sure how to use it or anything, but you may want to search around..

---

### Post by mstlyevil on 2006-01-28
[QUOTE=briancurtin]i just use K3B/GnomeBaker to copy my home folder to DVD(s)

on windows i used some Nero backup utility when my system was going down, and that was a bad idea. ive had these backup DVDs for 8 months and have no way to get the data off of them without getting a windows computer with nero installed, that has a DVD reader/writer. im sitting here with 9 DVDs full of my old music, pictures, and videos...thank god iPods connect as USB hard drives so you can just dump the music from there or id have been completely screwed[/QUOTE]

Why don't you just reinstall Windows long enough to extract all that data from the DVD's and reburn them in their original format? That is what I would do anyway.

---

### Post by Galoot on 2006-01-28
Try backup-manager. It should be in the repos.

It's command-line, and you have to hand-edit the config file, but it's painless.

Doesn't do incremental, though, afaik.

---

### Post by briancurtin on 2006-01-29
[QUOTE=mstlyevil]Why don't you just reinstall Windows long enough to extract all that data from the DVD's and reburn them in their original format? That is what I would do anyway.[/QUOTE]
i thought about that, and thats why i bought an OEM copy of windows MCE (my computer was designed for it)...it doesnt install anything close to workable. waste of $125 or whatever it cost me. the HP discs that came with the laptop dont help anything, an OEM copy of windows does not work, plain old XP Pro from my dads MSDN binder does not work, and a pirated copy borrowed from a friend doesnt even work. windows cannot even be installed on this computer anymore...yep i said it. i have reformatted several times, started from absolute scratch before i came to running only linux, and at no point could i get a functioning windows install. other than this backup DVD issue, im glad i cant actually use windows.

thats my story haha. i am going to try to extract the files from the DVDs in the lab i run here at school (all windows). it isnt really allowed to be done, but even if i got "caught" it would be no big deal.

---

### Post by Bandit on 2006-01-29
$ tar -cvf backup.tar /home/bandit
then K3B it :)

---

### Post by Amon_Re on 2006-01-29
[QUOTE=Bandit]$ tar -cvf backup.tar /home/bandit
then K3B it :)[/QUOTE]

I'd prefer something abit more sofisticated...
Even the standard program of winxp is more sophisticated

---

### Post by Canuckelhead on 2006-01-31
I thought that that was nice and simple... the way things should be....
however.... is there a way to exclude certain files... rather than including each one you want?

---

### Post by jshein on 2006-01-31
I have been watching this project for a while. Looks like it could turn into a great product.

[http://planb.cloudnine.net.nz/?q=](http://planb.cloudnine.net.nz/?q=)

Works with both Linux and Windows clients / servers.

---

### Post by Bandit on 2006-01-31
[QUOTE=Amon_Re]I'd prefer something abit more sofisticated...
Even the standard program of winxp is more sophisticated[/QUOTE]
If you want more sofisticated, write your own script to backup your home folder and use cdrecord to burn it to disc. Then use cron to schedule it at night why you sleep. This is almost exactly how we did it with tape backups when I worked for a ISP. We schedule it for 4AM when most everyone was a sleep and had the least server load. Just double check them in the morning to make sure it worked.
I just dont see why your looking for new software do to something when everything you need is at your fingure tips. But thats just my opinion. \\:D/ 

> is there a way to exclude certain files... rather than including each one you want?
Check out man tar. I think there may be a way to exclude files by file extentions. For example you dont want to tar you MP3 collection as it may take 4 DVDs alone like my oggs do.

Cheers,
Bandit

---

### Post by Galoot on 2006-01-31
[QUOTE=Canuckelhead]I thought that that was nice and simple... the way things should be....
however.... is there a way to exclude certain files... rather than including each one you want?[/QUOTE]Here's what I use to exclude certain directories.```
tar cvpzf homebackup.tgz /home --exclude=/home/porn
```...because you can always find more porn.

---

### Post by mstlyevil on 2006-01-31
[QUOTE=Galoot]Here's what I use to exclude certain directories.```
tar cvpzf homebackup.tgz /home --exclude=/home/porn
```...because you can always find more porn.[/QUOTE]

Internet = porn :mrgreen:

---

### Post by Canuckelhead on 2006-02-02
thats what I needed thanks...

---

### Post by wrtrdood on 2006-02-02
I've wrestled with this for some time now and ended up simply doing manual archives by creating tarballs as described then using mkisofs to create an ISO to save to DVD.  Problem here is the version of mkisofs in the repository still has the 2G file limit and it's a pain to work with.  You have to break your tarballs up which tar allows.  Not a big deal but just that much more to have to do.

I was never successful getting multivolume backups to work, especially on-the-fly.  All other solutions require storage space to create these ISO files which, to me, seems to defeat the purpose.  I still want a good solution but it will probably take a lot more work with DVD right now.

There's a great resource page for this stuff at:
[http://www.troubleshooters.com/linux/coasterless_dvd.htm](http://www.troubleshooters.com/linux/coasterless_dvd.htm)

---

### Post by Amon_Re on 2006-02-10
[QUOTE=Bandit]If you want more sofisticated, write your own script to backup your home folder and use cdrecord to burn it to disc. Then use cron to schedule it at night why you sleep. This is almost exactly how we did it with tape backups when I worked for a ISP. We schedule it for 4AM when most everyone was a sleep and had the least server load. Just double check them in the morning to make sure it worked.
I just dont see why your looking for new software do to something when everything you need is at your fingure tips. But thats just my opinion. \\:D/ [/QUOTE]

Erm, no, thanks, while i may know my way arround a terminal, i don't feel like actually writing a program or script for this just yet, there are probably programs out there that do what i want already.

And i'm not talking about backing up my /home folder(s), i'm talking about backing up a complete system with live sql databases, sites & other running processes.

Hence the request that it's incremental

---

### Post by jshein on 2006-02-10
> And i'm not talking about backing up my /home folder(s), i'm talking about backing up a complete system with live sql databases, sites & other running processes.

Hence the request that it's incremental

It sounds like you would be interested in Mondo Rescue
[http://www.mondorescue.org/](http://www.mondorescue.org/)

#sudo apt-get install mondo

It works great and has save me on numerous occasions. I find that this is the easiest way to backup the system in a way that I can get it back up and running in the shortest time possible. I have now been using this on all the systems I manage for about 4 years.

From the documentation page:

[http://www.mondorescue.org/docs/docs.html](http://www.mondorescue.org/docs/docs.html)

"BTW, to restore, just boot from the emergency floppy/CD and choose Nuke Mode to wipe and restore. If you prefer, boot to Interactive Mode for a less drastic, more user-friendly set of menus. Yes, it is that simple. :-)"

Hard drive failure? Throw in a new drive. Insert CD#1. Type "nuke" and it partitions the disk, puts all your data back, makes it bootable. Reboot and you are back where you left off.

---

### Post by UbuWu on 2006-02-10
SBackup is also nice. It was developed for Ubuntu during Google's summer of code last year and has most features you asked for.


> SBackup is a simple backup solution intended for desktop use. It can backup any subset of files and directories. Exclusions can be defined by regular expressions. A maximum individual file size limit can be defined. Backups may be saved to any local and remote directories that are supported by gnome-vfs. There is a Gnome GUI interface for configuration and restore.

[http://sbackup.sourceforge.net/](http://sbackup.sourceforge.net/)

---

### Post by Ted_Smith on 2006-10-10
Arkeia Backup looks like a great utility that can backup to tape or disk and you can use incremental, differential or full backup options, with scheduler. There's two versions, but the 'Arkeia Smart Backup' is free for data up to 50Gb. 

[www.arkeia.com/download/](www.arkeia.com/download/). 

There's even an Ubuntu Dapper package! 

Ted

---

