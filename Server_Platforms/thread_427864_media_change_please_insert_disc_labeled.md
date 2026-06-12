---
title: "media change: please insert disc labeled"
date: 2007-04-29
forum: Server Platforms
---

### Post by nonewmsgs on 2007-04-29
media change: please insert the disc labeled 'Ubuntu-Server 7.04 _Fiesty Fawn_ - Relese i386 (20070415)' in the drive 'cdrom' and press enter

wtf?  do i have to keep the server cd in the dvdburner all the time??

---

### Post by earobinson on 2007-04-29
I bet its in your sources.list and you are trying to update or install things

can you post your /etc/apt/sources.list

Thanks

---

### Post by nonewmsgs on 2007-04-29
GNU nano 2.0.2          File: /etc/apt/sources.list

#
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feist$

deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty $
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu sec

---

### Post by nonewmsgs on 2007-04-29
oh duh! there it is i can see it now

---

### Post by eha1990 on 2007-05-24
What is the solution to resolving this problem?  I'm having the same issue.  Do you remove the statement about "Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)"?

---

### Post by shen-an-doah on 2007-05-24
> **eha1990 said:**
> What is the solution to resolving this problem?  I'm having the same issue.  Do you remove the statement about "Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)"?

Just comment it out (stick a # in front of it). Don't remove it completely as you never know when you might need it.

---

### Post by earobinson on 2007-05-26
> **shen-an-doah said:**
> Just comment it out (stick a # in front of it). Don't remove it completely as you never know when you might need it.
It being the line > deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty $ so it should look like this > # deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty $

Note # is used for comments so the computer just ignores any text after the # when parcing the file.

Thanks for searching shen-an-doah!

---

### Post by REDISISTone.nl on 2007-06-01
Awsome,

Had the same problem and I could figure out what was the problem (it was just to easy ;)) thanxx

---

