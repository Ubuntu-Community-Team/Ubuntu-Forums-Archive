---
title: "linbaku - create easy backups of your ubuntu installation"
date: 2008-04-14
forum: The Cafe
---

### Post by dje on 2008-04-14
linbaku is no longer under development

dje

---

### Post by dje on 2008-05-02
linbaku 0.1.6 released, debs are available from the website or if you are using the repository it will be updated when you next update your system

dje

---

### Post by dje on 2008-05-03
linbaku 0.1.8 released (0.1.7 release skipped) fixing a problem where it sometimes wouldn't start

dje

---

### Post by Timbothecat on 2008-05-06
Hey there DJ.

I have just downloaded and installed linbaku. I'll be setting it up later on to give it a good thrashing so I'll let you know how it goes.

Thanks so much for taking the time to develop this though. Even though I'm a child of the 70's-80's I never got into computers until about 5 years ago. And even then it was an MS environment! So GUI is -unfortunately- where I'm more comfortable.

Anyway, I'll keep you posted (no pun intended).

All the best,

Tim.

---

### Post by dje on 2008-05-08
Thanks Tim, hope it works well for you and be sure to check the website for new releases (if you didn't use the repository). There will be some good changes for 0.1.9 leading up to the milestone 0.2 release

dje

---

### Post by Timbothecat on 2008-05-08
I haven't had a chance to give it a go yet, unfortunately. Things have been a little hectic since I downloaded the program. My 2nd youngest burnt his fingers on some hot toffee (yes, toffee, not coffee) which my wife had just cooked. This meant that things got knocked a little out of whack.

I'll give it a shot tomorrow, I need to clean off an external drive first so it might take a little time.

I will certainly keep you posted on how it goes though.

All the best,

Tim.

---

### Post by Timbothecat on 2008-05-09
Worked a treat DJ.

One question though. Is it going to become an automated system at any stage (in the mold of SyncbackSE or something of that ilk) as I would love to be able to choose which files to back up and when it needs to be done etc.

I know I can do this at the command line but what can I say, I'm lazy.:) 

Anyway, it worked beautifully so keep up the good work.

All the best,

Tim.

---

### Post by dje on 2008-05-10
Glad it worked Tim,
Unfortunately, at the present time, i have no plans to automate the backup. Some reasons for this are that other utilities do and i wish to keep mine as 3 or so mouse click simple. Thanks for the feedback

dje

---

### Post by dje on 2008-05-12
linbaku 0.1.9 has been released, with a new feature and interface changes which begins the lead up to the 0.2 milestone release and the 0.2.x releases which will focus on the interface

dje

---

### Post by dje on 2008-05-13
linbaku 0.2 milestone released!
This release fixes some bugs and the interface now remembers your last used settings. debs available at the website or through update manager if you used the repository

dje

---

### Post by dje on 2008-05-16
linbaku 0.2.1 released as a bug fix release

dje

---

### Post by dlmoak on 2008-06-18
Ubuntu 8.04.1 64-bit; Gnome; release 2.1; synaptic I think.
Installed linbaku and did a complete backup to an external usb drive (Western Digital Passport) as a tar.gz file.  Yesterday I attempted to do a complete restore.  Using the gui, I selected the backup file and clicked on restore, but nothing happened.  I then tried to extract the files using the archive manager.  Some extracted and some did not with the result that most of my system didi not work.  I re-installed Ubuntu and restored my data, re-installed my software so I am back to normal.  However, I would like to be able to use linbaku if possible.  I assume there is a command line usage to restore the tar.gz file, but I was unsure of the syntax and did not try it.

---

### Post by dje on 2008-06-18
Firstly, thank you for trying linbaku and i hope that your problem can be resolved

Ok i have never had this problem before, i assume it is the 64 bit that is causing problems and i have not tested it on 64 bit as i dont have any 64 bit machines (i should put a warning about that along with the early alpha warning). Anyways linbaku does not support command line arguments yet but you can use tar to unpack it like this:
```
sudo tar xzvpf /path/to/backup/file -C /directory/to/unpack/files/to
```
obviously substitute the file paths ;)

On the 64 bit front try installing to run 32 bit applications:
```
sudo apt-get install ia32-libs
```

Also please run this from the terminal:
```
linbaku.py
```
and post the output here (i know about the bug warning ;)
Also can you confirm if the backup file is .tar .tar.bz2 or .tgz it should not be .tar.gz

Please post back and i hope that helps,
dje

---

### Post by dlmoak on 2008-06-18
I'll try it when I get home this evening.  Should I uninstall the linbaku that is there already before I do this?  I'll confirm the backup file type.

Now that I already have everything restored, I may not actually want to do the restore because my system is somewhat cleaner now.  :)

---

### Post by dje on 2008-06-18
> **dlmoak said:**
> I'll try it when I get home this evening.  Should I uninstall the linbaku that is there already before I do this?  I'll confirm the backup file type.

Now that I already have everything restored, I may not actually want to do the restore because my system is somewhat cleaner now.  :)

ok
a complete removal of linbaku shouldn't hurt:
```
sudo apt-get autoremove --purge linbaku
```

---

### Post by dlmoak on 2008-06-18
OK - good and bad news.
I ran the sudo apt-get install ia32-libs followed by a fresh install of linbaku (I had completely removed the previous installation).  I did a complete backup of my system, using the gui.  I then attempted a restore.  When it started (which it had not done before) I clicked on "Cancel."  The gui went away, but I noticed that my hard drive light indicated that it was working like crazy.  Just prior to the hard drive activity stopping, I got a message saying, "There was an error during restore - please try again."  However, I think the restore completed, judging from the length of time the hard drives were working.  I think perhaps the error message is tied in to the lack of the cancel button to actually cancel the restore.  At any rate, it seems to be working.  The backup was a tgz file, by the way.  Thanks for your help.

---

### Post by dje on 2008-06-19
No problem and i'm glad you got it working. The cancel button on the progress dialog currently causes problems as documented [here]("http://code.google.com/p/linbaku/issues/list")

dje

---

### Post by dje on 2008-09-20
linbaku 0.3.x is now in development featuring an all new interface and new features including directory exclusion and scheduled backup. check [http://linbaku.co.cc]("http://linbaku.co.cc") for the latest news. linbaku is also making a switch to rsync to allow incremental backup

dje

---

### Post by Polygon on 2008-09-20
what distinguishes this program from other backup programs such as rdiff-backup, pybackpck, sbackup and timevault?

---

### Post by earthpigg on 2008-09-20
simplicity seems to be his major selling point.

and he is probably having fun and learning some stuff with this project ;)

---

### Post by dje on 2008-09-20
> **earthpigg said:**
> simplicity seems to be his major selling point.

and he is probably having fun and learning some stuff with this project ;)

just about what i was going to say :D

---

### Post by dje on 2008-10-17
linbaku is no longer under development

---

