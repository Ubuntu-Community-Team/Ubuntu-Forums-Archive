---
title: "Installing Starcraft 2 [Complete Newb]"
date: 2010-08-24
forum: Wine
---

### Post by Lamoramaks on 2010-08-24
Hey, I'm pretty much a complete Newbie to Linux / Ubuntu and I installed it on my computer today and have installed Wine and Crossover Games after deciding to do so from my research, and am now trying to install Starcraft 2: Wings of Liberty onto my Ubuntu 10.04 system. 
I put my SC2 disc into my laptop, then I opened up Applications> CrossOver Games> Install Windows Software and selected Starcraft II: Wings of Liberty, clicked proceed and then selected SC2-L100-D1 (Which I presume is the Starcraft disc Inserted) then hit install.

Pretty much as soon as it started I got the following error message: 
```
**An error occurred while running the 'AIEInsertMedia(Starcraft II: Wings of Liberty)' task**

This disk contains two sections, one for Mac and one for Windows.  In order for CrossOver to use this disk it must be mounted so that the Windows portion is visible.

To make this change, remount as root with this command:
mount -t udf -o users,ro,unhide,uid=1000 /dev/cdrom "/media/SC2-L100-D1"
```I then loaded up the terminal application, and as I have ubuntu I put sudo infront of the command and got this back:

```
mount: /dev/sr0 already mounted or /media/SC2-L100-D1 busy
mount: according to mtab, /dev/sr0 is already mounted on /media/SC2-L100-D1
```I then tried CrossOver again, to no avail.

Sorry if I missed anything out or did something wrong, as I said, I'm a complete Newbie to Linux and was wondering if this should have gone in the beginner section or the wine section, if a mod could move this to there it would be muchly appreciated, and this is my first post on any ubuntu forums :)

---

### Post by efikkan on 2010-08-24
Try entering:
umount /dev/sr0

And then try to mount again.

---

### Post by Lamoramaks on 2010-08-24
Now getting 

```
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab
```

And when I try to install it using CrossOver same message as before.

---

### Post by urbanus on 2010-08-24
Download the digital version from battle.net and use that. I couldn't get the DVD to work at least :-/

---

### Post by face_mcgace on 2011-08-10
Ok guys, I'm new to this forum but I found out how to install Starcraft 2 on Crossover from the Install DVD rather than downloading it from blizzard (took a while and figured out that Crossover has it completely wrong).

First, make yourself superuser with:

**su** (and enter your password)

Second you must unmount the DVD from the system itself using:

**sudo umount /media/the_cd_file  (for me it was /media/SC2-L100-D1)**

(notice that its not sudo *UNmount* but sudo *UMount* and everything is case sensitive)

Next is the tricky part, we must remount the file into the system, but we can't since we just unmounted it! So what we need to do is make a directory to mount the DVD back into. So:

mkdir /media/whatever_you_want (I used mkdir /media/SC2)

Now, to relaunch the DVD we don't use the old SC2-L100-D1 file that we mounted, we use the new /media/SC2 folder created (or whatever you used).
However, the next problem is that the info Crossover gives us is a paradox because we never 'mounted' the /media/SC2 directory folder.

(Notice the 'remount' in the code given by Crossover......sudo mount -t udf -o users,ro,unhide,uid=1000,**remount** /dev/sr0 "/media/SC2")

So to mount the Windows side of the DVD we use a little work around:

**mount /dev/sr0 "/media/SC2" -t udf -o users,ro,unhide,uid=1000**

(Notice, the /dev/sr0 is similar in most systems, but it could be anything /dev/xxx, so make sure you have the right drive)

And thats it,fire up Crossover and just install. Welcome to DVD SC2 installer :)

---

