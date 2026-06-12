---
title: "Holy Cow. How much HDD space does Vista need?"
date: 2008-04-25
forum: Windows
---

### Post by Pogeymanz on 2008-04-25
My fiancee bought a Vista laptop with an 80GB hard drive almost a year ago, and it is relatively unaltered from how it came out of the box.

I was just playing around on it today and saw that 30GB of hard drive was used!!!! (Not including the 8GB recovery partition)

She does not download anything on this laptop. She has a few photos and word docs. Not even any mp3's.

Does Vista really need almost 30GB of hard drive? I realize some of this is OEM stuff too. So, how much space does Vista need?

---

### Post by lswest on 2008-04-25
base vista install ranges between 8-13GB depending on the version, and the OEM stuff can add probably up to 2GB more.  And yeah, 30GB? i'm using 40+ of mine and i've got a lot of stuff on there. Also, if you have system restore activated, shadow backups, etc.  Clean it up (right-click hard drive, properties, "clean up") and remove all of the backups that accumulated, should free up a lot of space.  And i personally disable that feature, it's never done anything to help before.

---

### Post by Pogeymanz on 2008-04-25
Thanks. I just used clean up to get rid of all but the last restore point and it freed 10GB! There's the rub.

I wont disable it, because it's not "my" computer, but I will do stealth operations to make it run better for her. (I do defrags on her XP machine whenever she isn't home)

So I let her know that I freed up space for her and she was happy, so I patted myself on the back. :)

---

### Post by Joeb454 on 2008-04-25
Just give her KDE 4 and tell her you had a play on her PC and it "just went black, and came back like that" She might never know ;)

---

### Post by Pogeymanz on 2008-04-25
Hmmm. Not a bad idea... :lolflag:

---

### Post by smoker on 2008-04-25
i use this a lot to clean up junk from windows systems:
[http://www.ccleaner.com/](http://www.ccleaner.com/)

it is free, with no spyware, though untick the box for the 'yahoo toolbar' if you give it a try!

if you use the registry cleaner, always opt for a backup. never had to use it, but always good to have one!

---

### Post by LaRoza on 2008-04-25
> **smoker said:**
> i use this a lot to clean up junk from windows systems:
[http://www.ccleaner.com/](http://www.ccleaner.com/)

it is free, with no spyware, though untick the box for the 'yahoo toolbar' if you give it a try!

if you use the registry cleaner, always opt for a backup. never had to use it, but always good to have one!

I never used the backup on ccleaner, as I never had any problems with it.

The biggest space eating Vista is the restore points. See a thread I made on this a while ago in the Cafe. You might want to delete the ones you don't need.

---

### Post by lswest on 2008-04-26
Haha, glad my advice helped :P and thanks for the thanks ^^ (thankfully, the "find all thanked posts by lswest" works now, else i would have spent a while figuring out where the new thanks came from lol).  And my input on ccleaner is that it's not bad, but i prefer doing things by hand.  Also might want to clear the temporary folders (back to the "clean up" window, and then in the first tab is a list of files that can be removed, and how much space they take, check the boxes you want removed, then hit "ok" and it might free up a bit more space).

---

### Post by tamoneya on 2008-04-26
How much space does vista need? Way to much.  I ran into a very extreme case of this myself.  My school supplies laptops with vista preinstalled.  They have 160 GB harddrives and have all the applications necessary for classes.  This includes a couple of large applications but nothing HUGE.  When all was said and done the laptops only had 20 GB of free space.  I find this just ridiculous.  This is without any back up partitions or anything.  

Obviously I quickly installed ubuntu and freed my harddrive.  I know laugh at all my friends when they complain that they don't have enough space for all their music.

---

### Post by kamaboko on 2008-04-27
Vista shadowstorage is the cause.  This is how to fix it.

Go to start>all programs>accessories>dos command. right click dos command and run as administrator. type in the following:

vssadmin resize shadowstorage /for=c: /on=c: /maxsize=1gb

then "enter".  it'll resize the storage size.

vssadmin resize shadowstorage/for=ForVolumeSpec/on=OnVolumeSpec [/maxsize=MaxSizeSpec]

---

### Post by Jiraya on 2008-04-29
> **kamaboko said:**
> Vista shadowstorage is the cause.  This is how to fix it.

Go to start>all programs>accessories>dos command. right click dos command and run as administrator. type in the following:

vssadmin resize shadowstorage /for=c: /on=c: /maxsize=1gb

then "enter".  it'll resize the storage size.

vssadmin resize shadowstorage/for=ForVolumeSpec/on=OnVolumeSpec [/maxsize=MaxSizeSpec]

Thanks for the hint. I'll try this here too.

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

