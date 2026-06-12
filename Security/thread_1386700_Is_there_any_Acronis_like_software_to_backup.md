---
title: "Is there any Acronis like software to backup?"
date: 2010-01-21
forum: Security
---

### Post by mrhellboy86 on 2010-01-21
HI
I am using Acronis backup & restore system for my windows partitions
I have a dual boot HDD and I want to backup my ubuntu partition
is there any software like Acronis that can backup and restore a whole partition
with the ability to generate a bootable CD and ability to backup Increamentally
(based on each other)
thank you in advance

---

### Post by pirateghost on 2010-01-21
> **mrhellboy86 said:**
> HI
I am using Acronis backup & restore system for my windows partitions
I have a dual boot HDD and I want to backup my ubuntu partition
is there any software like Acronis that can backup and restore a whole partition
with the ability to generate a bootable CD and ability to backup Increamentally
(based on each other)
thank you in advance

i am pretty sure that acronis has a linux version of that same software 
[http://www.acronis.com/backup-recovery/server-linux/](http://www.acronis.com/backup-recovery/server-linux/)

---

### Post by mrhellboy86 on 2010-01-21
is it free?
is there any free software for doing that

---

### Post by rileinc on 2010-01-21
You might wanna look into Mondo Rescue: [http://www.mondorescue.org/](http://www.mondorescue.org/)
It's free and open sourced. I haven't used it myself but I think it works similar to acronis.

---

### Post by howefield on 2010-01-21
> **mrhellboy86 said:**
> is it free?

No, Acronis is comercial software, and also doesn't support ext4 (except on sector by sector basis).

Clonezilla is a great piece of software, although it looks intimidating, it is pretty easy to follow the defaults which work pretty well.

---

### Post by pirateghost on 2010-01-21
> **mrhellboy86 said:**
> is it free?
is there any free software for doing that

you said you are using acronis backup and recovery on your windows box = its not free either

have a look at clonezilla like howefield suggested.  i have used it before, and it is intimidating at first, but its not so bad after you get used to it.

---

### Post by mrhellboy86 on 2010-01-21
you mean that is the best choice for backup & recovery 
it seems to be an old program that maybe do not have options 
that I need some things like splitting the image file to lower size
so that I can write my image files to DVDs
are you sure doesn't any thing better exist for Linux
I did find out that there is a Linux version for Acronis
and I didn't find a full free  version <snip> for download
that seems to be a good program. <snip>

---

### Post by howefield on 2010-01-21
> **mrhellboy86 said:**
> ...maybe do not have options 
that I need some things like splitting the image file to lower size
so that I can write my image files to DVDs

If you even did a little research of your own, you'd know the answer to those points.

---

### Post by jamesr on 2010-01-21
I have been using Mondo. The support community is quite good, although I have to admit that I went throgh a bad spell where it did not work. Currently I backup to a USB drive as a series of ISO images which I can then burn at leisure. But direct burns to RW media do not seem to work. It used to work and one of the updates from Ubuntu seem to stop it working. The problem seems to be Distro related as Mandriva, red Hat, etc., users seem to get it working with less problems. Currently my test bed is using 8.04 LTS 

I did try others but a few years ago so I cannot make any real comments about later versions of Clonezilla.

If you do wish try Mondo do not use the versions on the Ubuntu site/repository, they are out of date and version labelling means that the update manager always updates to Ubuntu versions, not the later versions available on the Mondorescue.org site. There is a comment on the Mondo website, as how to correct this problem.

---

### Post by mrhellboy86 on 2010-01-22
> **howefield said:**
> If you even did a little research of your own, you'd know the answer to those points.
as I am just a newbie in Ubuntu maybe it is better to use my own Acronis Sector by Sector image, and do update it weakly 
I tried to study the features of mondo but there are lots of terminology that I am not familiar with , I am studying some hand book on Ubuntu so as soon as I become a aware man of ubuntu i would use Ubuntu's software
maybe for now I do not that familiar with some pro software to deal with them:KS
I am happy to be in Ubuntu active community, while for now I am just asking
hope to be a knowledgable person to help others

---

### Post by HermanAB on 2010-01-23
Well, Linux is a bit different...

While on a Windows system it makes sense to back up the whole schtoopidt system with viruses spyware and all, it generally doesn't make sense to do that on Linux systems.  Linux is Free.  There are tons of copies available everywhere, e.g. mirrors.kernel.org, so backing up the whole system is a total waste of time.  

In any case, if your system does get schtuffed up after a few years of use, then you would likely want to install the latest version not re-install a 3 year old version from backup.  Also, re-installing from scratch only takes 30 minutes or so, which is likely much faster than restoring a backup.

Therefore, most Linux users only backup their data and maybe keep a tar ball of the /etc directory - if you installed something special then it may be useful to dig in the old configuration files for guidance.

Sooooo, rsync is your friend. Google for rsync and get to know how to use it.  You very likely don't need special backup software at all.  That actually explains why backup software on Linux generally sucks - since only newcomers develop and use it - the old timers know better! ;)

---

### Post by cariboo on 2010-01-23
If you are a new user and not comfortable with the terminal, try grsync, it is in the repositories. Once it's setup, it is just a matter of one click, and files are backed up.

---

### Post by ratcheer on 2010-01-23
> **howefield said:**
> 
Clonezilla is a great piece of software, although it looks intimidating, it is pretty easy to follow the defaults which work pretty well.

I tried and tried, but could not get Clonezilla to work. It would go through all its setup and questions of everything you could imagine, then when I gave it the command to start backing up, it said there was no disk detected. Even though it had previously shown me all the partitions and had me specify what to back up.

It was too weird for me.

Tim

---

### Post by mrhellboy86 on 2010-01-24
> **cariboo907 said:**
> If you are a new user and not comfortable with the terminal, try grsync, it is in the repositories. Once it's setup, it is just a matter of one click, and files are backed up.
does any one know is it possible to boot with a CD when system doesn't boot and backup and restore everything without any problem?
the most important thing about a backup and restore software is reliability  as restore is the last choice ,is it reliable enough?

---

### Post by cariboo on 2010-01-24
If your system is broken badly enough that it won't boot, it is usually quicker to do a re-install. Depending on how much data you have backed up, it may take several hours to restore it. 

The last time I had to do a restore from a backup, I only backup my home directory, it took about half an hour to install the system, and 1½ hours to restore my home directory, which is currently sitting at 57Gb.

You can do a restore from backup using the Live CD, if you used rsync as it installed by default, if you used another program to backup you will have to install it first, it will be installed in ram, and disappear when you reboot.

---

### Post by jamesr on 2010-01-24
Hi,

I partialy agree with some of the comments  about installing from scratch, except for the debacle with 9.10 (karmic) but that assumes that you have set up a seperate /home disk, and you have remembered to get the appropriate parts from /etc directory.

Currently as I mentioned recently I use Mondo for my home server, along with achiving the /home directory, because it gets the household running sooner, less agro from the missus and the rest of the family who have to run Windows. 

Also as a newbie, at one time,  I remember the panic, when the system would not reboot or files lost because of something that I had done.

Even for my base system I use Mondo even though I may use afio to recover the files from the archive sets.

My greatest problem is the lack of consistency of the CDR writing programmes. Brasero is ???, gnomebaker is a lot more reliable but sometimes says the CDRWs are OK but they are not.

With reference to the Karmic problems, I have not had time over the last month and a half to download new install disks and restart again, so the problems may be now solved but certainly the initial Upgrade was not upto the usual Canonical stanadards more like a Micro$oft upgrade. This is why my signature does not include a Karmic system.

---

### Post by mrhellboy86 on 2010-01-25
> **HermanAB said:**
> Well, Linux is a bit different...

While on a Windows system it makes sense to back up the whole schtoopidt system with viruses spyware and all, it generally doesn't make sense to do that on Linux systems. Linux is Free. There are tons of copies available everywhere, e.g. mirrors.kernel.org, so backing up the whole system is a total waste of time.

In any case, if your system does get schtuffed up after a few years of use, then you would likely want to install the latest version not re-install a 3 year old version from backup. Also, re-installing from scratch only takes 30 minutes or so, which is likely much faster than restoring a backup.

Therefore, most Linux users only backup their data and maybe keep a tar ball of the /etc directory - if you installed something special then it may be useful to dig in the old configuration files for guidance.

Sooooo, rsync is your friend. Google for rsync and get to know how to use it. You very likely don't need special backup software at all. That actually explains why backup software on Linux generally sucks - since only newcomers develop and use it - the old timers know better! 
I didn't really get you
but I have installed Ubuntu 4-5 times in just a week
and I didn't found it reliable to remain on my computer for years
I expericed lots of problems reasons was : updating ubuntu, installing a fps game from repository and play with that, and powering off the system by power button
and my grub were gone as simply as I couldn't even imagine
so i think it is really crucial a full backup
nevertheless, suppose I am using my Ubuntu system all well
I installed lots of programs, lots of settings in the programs and I don't know
a hundred customization things
I don't want to do them all again
the time is not worthless
I didn't meant any insult to nobody no Ubuntu not any thing else
I am just telling you that it is really crucial for Ubutu and ( as my experience tell me) all linux based system to have backup of your data
the simples reason is that you will loss your grub just with a reset( Ya, it is possible I have expericed it with RedHat some years ago just a reset and the grob is gone)

---

### Post by jamesr on 2010-01-25
Hi 

Please read my previous replies, 

Yes people do understood, unfortunately you are at the point where the learning curve is quite steep, so saving all of your mistakes may not be as useful as you think. Initially, in fact, I still do, I kept a log of all of my changes and why I did them. It was quite complete then , now I only record what I have installed and the changes needed.

Mondo does a bare metal install from CD's or DVD's
Also can split a larger partition into smaller ISO's for burning later. See my other comments.

You mention reinstalling Ubuntu> but I have installed Ubuntu 4-5 times in just a week and > I installed lots of programs, lots of settings in the programs and I don't know
a hundred customization things. It seems that you using Ubuntu 24 hours a day so a log book is invaluable.

You also said> I am just telling you that it is really crucial for Ubutu and ( as my experience tell me) all linux based system to have backup of your data
the simples reason is that you will loss your grub just with a reset( Ya, it is possible I have expericed it with RedHat some years ago just a reset and the grob is gone)

I think is probably more important for Windows to have backups and that is why Acronis was developed for business use and that is why you have to pay for a copy. That is equally why I use Mondo for my server because I need it to be up and running again quickly and I may not remember how I configured something that I did 1 year ago even with a log book.

---

### Post by cariboo on 2010-01-25
+1 for a log book, especially if you are just learning. If you have to use the power button to shut down, usually booting from the Live CD and running fsck will solve most of your problems.

Boot from the Live CD, and once at the desktop open an Applications->Accessories->Terminal and type:

```
sudo fsck -a /dev/sda
```

Substitute your Ubuntu partition for the example above. Once fsck is done, reboot the system and you should be ok.

If your system seems to lock up, try pressing Ctrl-Alt-F1 to get to a console where you should be able to shutdown without having to press the power button:

```
sudo reboot
```

will reboot the system.

---

### Post by mrhellboy86 on 2010-01-25
I am really thankful of you all that are helping me stand on Ubuntu
NOW I can see how the Community and the internet may support a thing
and how valuable it is ,
Is there any software for log book, or I should do it myself?
I have experienced RedHat and OpenSuse before and still ubuntu
but I didn't come to them academically 
Now I am studying a book of ubuntu 
so I did realize that the Community is very important for all linux based OSs
really enjoyable unforgettable experience on this kinda community
love you all

---

### Post by jamesr on 2010-01-25
Hi,

I still use pen and paper although currently I starting to use TreePad for linux as a logbook, but as always you have to remember to backup the logbooks preferably to CDR but if you doing a lot of updates and changes the paper log book works out cheaper.

Good Luck

---

### Post by cariboo on 2010-01-25
> **mrhellboy86 said:**
> I am really thankful of you all that are helping me stand on Ubuntu
NOW I can see how the Community and the internet may support a thing
and how valuable it is ,
Is there any software for log book, or I should do it myself?
I have experienced RedHat and OpenSuse before and still ubuntu
but I didn't come to them academically 
Now I am studying a book of ubuntu 
so I did realize that the Community is very important for all linux based OSs
really enjoyable unforgettable experience on this kinda community
love you all

I use zim, it is in the repositories. the notes are stored in a directory called notes, this gets backed up daily, along with the rest of my home directory.

---

### Post by User Abuser on 2010-07-21
What's a logbook? =) Some software that keeps track of changes??

---

### Post by cariboo on 2010-07-21
I use a notebook (paper) and zim to log changes I make to the system.

---

