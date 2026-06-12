---
title: "Lucid Lynx is due out next week - before you install/upgrade..."
date: 2010-04-23
forum: The Cafe
---

### Post by Irihapeti on 2010-04-23
That's right, **[COLOR="Red"][SIZE="3"]BACK UP YOUR FILES[/SIZE][/COLOR]**.

That is, unless you've decided that you can quite easily live without them.

At the minimum, back up your personal files - documents, music, videos, pictures, emails and stuff.

If you are worried that you might get into a mess with Lucid and will want to reinstall your current system, you can make an image of the complete system.

I do this before doing any major change, and it's saved me from ruination on more than one occasion. It takes me about half an hour to do a restore.

How to do it? There are various methods available. [This link]("https://help.ubuntu.com/community/BackupYourSystem") gives you plenty of options. No doubt other members will have suggestions as well. I prefer to use [archives]("https://help.ubuntu.com/community/BackupYourSystem/TAR"), but if you have another preference, that choice is yours. The main thing is to DO IT.

Unless you are completely confident that you can't possibly install to the wrong drive or partition, get the backup file(s) right off your computer. A removable drive or even DVDs fits that bill, or a server or another machine if you have access to one. If you want to be really safe, have two copies in different places.

Knowing that you **have a good backup available** does wonders for the stress levels. :)

I wish you all stress-free installing and upgrading.

---

### Post by tica vun on 2010-04-23
Backups are overrated. There's nothing like the adrenalin surge when you tell the partitioner not to format your 700GB /home and pray it obeys.

---

### Post by Irihapeti on 2010-04-23
> **tica vun said:**
> Backups are overrated. There's nothing like the adrenalin surge when you tell the partitioner not to format your 700GB /home and pray it obeys.

If you want to live on the edge, then yes. :) Me, I'm not that addicted to adrenalin.

It reminds me of an old definition I heard somewhere: A backup is something you promise to do next week and actually get round to doing the day after you've lost your files.

---

### Post by fatality_uk on 2010-04-23
Seperate home partition /home :)

---

### Post by cariboo on 2010-04-23
After you back up your files, **Read The Release Notes** while downloading the iso.

---

### Post by sn0m on 2010-04-23
I'm not sure how having a separate /home directory helps.
It helped a lot prior to encryption, but now, when it is encrypted, it will not let you install a new ubuntu without giving major headaches.
Apparently you can use some how to to mount and decrypt your home directory, but to a simple chap like me, it turned out to be quite a difficult task, and i really hope that ubuntu folks have created an option to do this easily and flawlessly during install process, ie if install detects encrypted home directory, then it asks your for password and does decrypting etc automatically, otherwise, all simple chaps like me will have major depression issues.
I have learnt the lesson, bought a 1 tb external hd and will copy everything there before upgrading, but what about people who do not have such an option....
Ta Sokol

---

### Post by Irihapeti on 2010-04-23
@sn0m
I have a separate /home partition, not encrypted, and I don't see how that does away with the need for backups.

I don't have the option of an external drive, either. I use DVDs.

I don't know what I'd do if I had 100 GB of videos/photos/music and no money for an external drive, or at least a second internal one. I do know I'd be feeling uncomfortable in that situation.

---

### Post by Swagman on 2010-04-23
New hard drive for the win.

I have a 200gb drive empty (Capture) from my old NLE days that I drag home to before installing new drive with newer version.

[img]http://www.upload3r.com/serve/230410/1272026123.jpeg[/img]

---

### Post by wykedengel on 2010-04-23
> **tica vun said:**
> Backups are overrated. There's nothing like the adrenalin surge when you tell the partitioner not to format your 700GB /home and pray it obeys.

LMAO :lolflag:

---

### Post by fidelandche on 2010-04-23
Is there a way to back up chrome?

---

### Post by Khakilang on 2010-04-23
How do I say farewell to Karmic Koala?

---

### Post by Megaptera on 2010-04-23
> **fidelandche said:**
> Is there a way to back up chrome?

The easiest way I've found is Xmarks:
[http://blog.xmarks.com/?p=1119](http://blog.xmarks.com/?p=1119)

---

### Post by beercz on 2010-04-23
Why not backup regularly, not just when it's upgrade time?

---

### Post by Ric_NYC on 2010-04-23
I need a fresh start. The upgrade to Lucid messed up my computer.
I used Dropbox to backup somethings I think are important.

---

### Post by Mr. Picklesworth on 2010-04-23
> **fidelandche said:**
> Is there a way to back up chrome?

The latest version has built in bookmark / settings / themes sync. (Well, Chromium's daily build has had it for a long while, and I'm pretty sure Chrome has released with the feature by now).

Try the wrench menu, then Synchronize Bookmarks&#8230;, or go open its Options and check out the first item in the Personal Stuff section.


As for other stuff, Deja Dup is the way of the future, and it's already awesome, so use that :)

---

### Post by sunk8 on 2010-04-23
sbackup is good...
ubuntu one helps...
dpkg-repack + aptoncd helps me backup old progs not in  repos...

---

### Post by northwestuntu on 2010-04-23
> **tica vun said:**
> Backups are overrated. There's nothing like the adrenalin surge when you tell the partitioner not to format your 700GB /home and pray it obeys.


lol :)

---

### Post by northwestuntu on 2010-04-23
> **Mr. Picklesworth said:**
> The latest version has built in bookmark / settings / themes sync. (Well, Chromium has had it for a long while, and I'm pretty sure Chrome has released with the feature by now).

Try the wrench menu, then Synchronize Bookmarks…, or go open its Options and check out the first item in the Personal Stuff section.


As for other stuff, Deja Dup is the way of the future, and it's already awesome, so use that :)

well i see bookmark sync and that's working.  nothing i can see for themes and settings.  i would would just like something to back up my passwords.  themes and settings are a quick setup.

---

### Post by CharlesA on 2010-04-23
> **cariboo907 said:**
> After you back up your files, **Read The Release Notes** while downloading the iso.

This definitely helps.

I have the OS drive backed up as an image, and the data array backed up using rsync. Less stress is good. :D

> **northwestuntu said:**
> well i see bookmark sync and that's working.  nothing i can see for themes and settings.  i would would just like something to back up my passwords.  themes and settings are a quick setup.

Can't you just backup the folder inside the home directory? I don't use Chrome or Chromium, but most stuff should store their data in /home/user/.(insert program name here)

---

### Post by conradin on 2010-04-23
> **tica vun said:**
> Backups are overrated. There's nothing like the adrenalin surge when you tell the partitioner not to format your 700GB /home and pray it obeys.

Lolz Hell yeah!

---

### Post by standingwave on 2010-04-23
> **beercz said:**
> Why not backup regularly, not just when it's upgrade time?Precisely. Last November I had a drive just fail without warning. I started the computer and the BIOS was unable to see any media. Now I had three drives and it couldn't see any of them. Couldn't see the optical drive either. I was thinking my controller had died but I started pulling drives and soon determined that the WD 1TB was the culprit. It didn't even have an OS on it but whenever it's plugged in, it prevents the system from seeing any drive. Apparently something to do with the SATA interface electronics. It's still sitting here on my shelf if anyone has any bright ideas. But thank the FSM for my backup. There's really no excuse these days with drives being so inexpensive.

---

### Post by Irihapeti on 2010-04-23
> **beercz said:**
> Why not backup regularly, not just when it's upgrade time?

I agree. In fact, just after I'd posted this I remembered that I hadn't backed up my system (as distinct from home directory) for some time, so I did it.

Hopefully, if people can be encouraged to backup before upgrading, they might continue to do it at other times.

On the other hand, dreams are free. :)

---

### Post by beercz on 2010-04-23
I backup all the time - 3 or 4 times a day - minimum.

I have a lot of clients' data on my pc and laptop.

And in almost 20 years of IT professional experience I have never lost anything important.

I use [rsnapshot]("http://rsnapshot.org") and some custom written scripts, together with cron to backup.

---

### Post by Ebere on 2010-04-28
Why not just copy the entire hard drive ?

To another hard drive, or DVDs, or flash drive, or whatever you have that would hold the entire contents...

Isn't everything going to be there, if you need it ?

---

### Post by CharlesA on 2010-04-28
You can image it, yes. Makes it a bit of a pain to access files without restoring.

---

### Post by ttshivers on 2010-04-28
> **CharlesA said:**
> You can image it, yes. Makes it a bit of a pain to access files without restoring.
 
[Clonezilla]("http://www.clonezilla.org/") is a great tool to image your hard drive or even make an exact clone of it on another hard drive.

---

### Post by Ebere on 2010-04-28
BTW: Not something that has ever worked for me with windows. 

First of all, windows will not let you copy the entire system area of the hard drive.

Once you do copy what you can, you have to reinstall windows somewhere, and copy your saved stuff back in.

But from what I have seen, you can copy the -complete- hard drive, with ubuntu.

And if you copied it onto another bootable drive, you'd have your entire system back.

Maybe I am missing something essential, but that is what it seems like, to me.

---

### Post by CharlesA on 2010-04-28
> **ttshivers said:**
> [Clonezilla]("http://www.clonezilla.org/") is a great tool to image your hard drive or even make an exact clone of it on another hard drive.

Indeed. I use it all the time. :)

The only downside to doing it on a data partition is that you need to restore it to the same drive, or a different drive to access the files.

I usually just rsync the data drive and image the main OS drive. Works like a charm for me.

> **Ebere said:**
> BTW: Not something that has ever worked for me with windows. 

First of all, windows will not let you copy the entire system area of the hard drive.

Once you do copy what you can, you have to reinstall windows somewhere, and copy your saved stuff back in.

But from what I have seen, you can copy the -complete- hard drive, with ubuntu.

And if you copied it onto another bootable drive, you'd have your entire system back.

Maybe I am missing something essential, but that is what it seems like, to me.

If you copy just the files from a Windows drive to another drive, you would need to recreate the MBR data. If you do a dd of the same drive, to the other drive, it would boot fine, since it does block-by-block copying.

Clonezilla works fine for Windows, since it saves the MBR and whatnot.

---

### Post by ttshivers on 2010-04-28
Yeah.  I am not that techie so I just stick to clonezilla.

---

### Post by stmiller on 2010-04-28
```
sudo do-release-upgrade
```

---

