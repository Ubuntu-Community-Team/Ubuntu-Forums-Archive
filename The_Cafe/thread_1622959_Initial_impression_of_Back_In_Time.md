---
title: "Initial impression of Back In Time"
date: 2010-11-16
forum: The Cafe
---

### Post by rmcellig on 2010-11-16
Having been a Mac user since 1988 and recently changed over to Linux Ubuntu, I was looking for a replacement for Time Machine that I used on the Mac. Yesterday I tried Back In Time and really like it. I find it way more flexible than Time Machine as well as easier access to my Back In Time backups.

I just wanted to get a feel for other users out there who have tried or are using Back In Time. I know it's not a cloning solution but at least I can have my Home directory backed up somewhere. 

I know that there are folders in my File System that I should back up as well. Which ones would they be?  This way I can recover my settings and home directory in case a major catastrophe occurs by simply reinstalling Ubuntu or using Rastersys ( I think that's what it is called) to make a working CD of my Ubuntu installation without all the files.

---

### Post by handy on 2010-11-16
I just installed it on Arch/Openbox & had a quick look at it, read up some on it as well.

BiT looks like a great front end for rsync, simple & easy to use.

I may or may not have use for it in the near future, as my ReadyNAS box has an rsync option built into it, so I'll see how useful it is first.


As far as the question of what other directories in your system to backup are concerned. You could do the following:

/boot - I just manually grab the /boot/grub/menu.lst file, which is no good to you as you will be using grub2, which I'm not. So someone else can give you advice on the path to what I'm sure will be a much smaller directory than grub1's /boot. The directory you want will have all of the grub2 config' files in it.

/etc - it's only about 6.5MB on my machine & contains many config files, that you will probably never need, but for the size, why not?

/opt - may be worth having a look in as I find it gets used unexpectedly from time to time. It is most likely not going to be worth backing up though.

---

### Post by rmcellig on 2010-11-16
I didn't know that BIT was a front end for rsync. I also use Lucky Backup which is also an rsync front end. I guess that they would both do the same thing?

Regarding files/folders in the file system thanks for the info. I'm just looking at easy ways to back up/ restore my machine in case of disaster. I also clone my machine using Clonezilla which also works well.

---

### Post by Dragonbite on 2010-11-16
I've been using Deja Dup. Unfortunately I encrypted it and I have forgotten my pass phrase (darn it!) so I can't keep backing up at this point, nor restoring it onto my laptop!

---

### Post by handy on 2010-11-16
> **rmcellig said:**
> 
I didn't know that BIT was a front end for rsync. I also use Lucky Backup which is also an rsync front end. I guess that they would both do the same thing? 

Use whichever makes the job easier. It seems that BiT is being currently developed which is nice as it will be kept up to date with whatever unforeseen (by most of us) changes may pop into our Linux systems.

> **rmcellig said:**
> 
Regarding files/folders in the file system thanks for the info. I'm just looking at easy ways to back up/ restore my machine in case of disaster. I also clone my machine using Clonezilla which also works well.

Clonezilla is wonderful. :)

I'd just make a Clonezilla image whenever you make a dramatic change to your system, & use BiT or whatever to keep your /home backed up or even just the directories in your /home account where you store your data.

I use Xmarks to synchronise between systems & also to backup my Firefox Bookmarks. It works very well & offers the option to encrypt your data. It may be of use to you.

All the best. :)

---

### Post by handy on 2010-11-16
> **Dragonbite said:**
> I've been using Deja Dup. Unfortunately I encrypted it and I have forgotten my pass phrase (darn it!) so I can't keep backing up at this point, nor restoring it onto my laptop!

That's a bummer Dragonbite. :(

My memory causes me trouble also. A strategy I use is to put all of my security info' amongst other useful & forgettable stuff into my Contacts section under Security, in my iPod Touch. 

If anyone did find the iPod, they would first have to get past the password to be able to use it, & then all of my security info' is entered in a way that they couldn't do anything with it anyway.

I like this system because it is also backed up onto my computer & elsewhere, so if I lose this lot, something devastating has happened & that loss will be the least of my worries.

---

### Post by Dragonbite on 2010-11-17
> **handy said:**
> That's a bummer Dragonbite. :(

My memory causes me trouble also. A strategy I use is to put all of my security info' amongst other useful & forgettable stuff into my Contacts section under Security, in my iPod Touch. 

If anyone did find the iPod, they would first have to get past the password to be able to use it, & then all of my security info' is entered in a way that they couldn't do anything with it anyway.

I like this system because it is also backed up onto my computer & elsewhere, so if I lose this lot, something devastating has happened & that loss will be the least of my worries.

With so many accounts, and my wife's memory being just as bad or worse (passwords are a computer~thingy which she isn't very interested in) we have our "little black book".  Too bad I forgot it before I could put it in there!

---

### Post by rmcellig on 2010-11-17
Thanks Handy!

I have used Xmarks. Pretty handy for sure! On my Mac I used a program called Superduper. This would do scheduled clones of my hard drive so that every morning at around 1am it would clone my internal drive to an external 250GB USB drive. This way if anything happened to my internal drive, I could simply restart from the external drive and clone that back to my internal drive if I wanted to.

Is there such a thing in the Linux world? That would really be great for me because I like to keep things as simple as possible. Clonezilla seems to be the only cloning tool I have found. Maybe I should rethink my backup strategy now that I am mostly using Ubuntu and seem to not use my iMac that much anymore. There is something about Ubuntu that keeps me coming back. :)

---

### Post by handy on 2010-11-17
I haven't done it, but I'm sure you can organise Clonezilla to backup your entire HDD whilst you sleep every night if you desire, (basically whenever you want) as a cron job.

Someone here will tell you how to do it. If you don't hear from them within a couple of days, start at new thread on the topic. I'm sure many people would benefit from the knowledge that such a topic would bring. ;)

---

### Post by rmcellig on 2010-11-17
Yes. I reallly think a lot of people would be interested in thos. I use Scheduled Tasks to organize my cron jobs so if there is a way to set up Clonezilla or something similar to do a bootable clone backup nightly, that would be way cool!!

I use Sheduled Tasks to record my radio shows every Sunday. Works great with the arecord command.

---

