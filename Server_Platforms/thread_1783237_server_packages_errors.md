---
title: "server packages errors"
date: 2011-06-15
forum: Server Platforms
---

### Post by thunder63cs on 2011-06-15
I recentled upgraded all the packages on my server and now I have an issue where I can't get any thing to install or uninstall do to errors, This is what I get:
 
 
praetorian@praetorian:~$ ps ax | grep dpkg
7330 pts/1 Ss+ 0:00 /usr/bin/dpkg --status-fd 21 --configure bind9 cups cups-bsd
7331 pts/1 S+ 0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/bind9.postinst configure 1:9.7.3.dfsg-1ubuntu2
7814 pts/2 S+ 0:00 grep --color=auto dpkg
praetorian@ praetorian:~$ sudo rm /var/lib/dpkg/lock
praetorian@praetorian:~$ sudo dpkg --configure -a
Setting up man-db (2.5.9-4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
subprocess installed post-installation script returned error exit status 1
Setting up cups-bsd (1.4.6-5ubuntu1.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing cups-bsd (--configure):
subprocess installed post-installation script returned error exit status 1
Setting up bind9 (1:9.7.3.dfsg-1ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing bind9 (--configure):
subprocess installed post-installation script returned error exit status 1
Setting up cups (1.4.6-5ubuntu1.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing cups (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
man-db
cups-bsd
bind9
cups

---

### Post by smurphy_it on 2011-06-15
Locked ?

Did you check for a lock file, or see if you have a browser window opened which is accessing synaptic ?

You could see if anything is holding it open with fuser or lsof.

```
fuser dpkg
lsof dpkg
fuser | grep deb

```

For example.

---

### Post by thunder63cs on 2011-06-15
yes it is showing a locked or unavalable part in teh report it is giving 
 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

which before it was the dpkg lock file was locked so I did what I saw in another thread to remove it and then do the sudo dpkg -- configure -a to try and get it working which then brought up the new errors .. 
 
I am running 11.04 server
 
This is a ubuntu only machine

---

### Post by smurphy_it on 2011-06-15
Did fuser of lsof find anything ?

---

### Post by thunder63cs on 2011-06-15
specified file name dpkg does not exist. is what fuser and lsof gave me

---

### Post by smurphy_it on 2011-06-15
No open synaptic windows, or zombies of it ?

ps -aef | grep synaptic

---

### Post by thunder63cs on 2011-06-15
> **smurphy_it said:**
> No open synaptic windows, or zombies of it ?
 
ps -aef | grep synaptic
 
 
the responce I get from that is :
 
1000     10041  7628  0 15:29 pts/2    00:00:00 grep --color=auto synaptic

 
sry I am a noob when it comes to this everything I have learned I have done on my own via research or books.  Just running into an issue that have had no luck with.

---

### Post by arrrghhh on 2011-06-15
> **thunder63cs said:**
> the responce I get from that is :
 
1000     10041  7628  0 15:29 pts/2    00:00:00 grep --color=auto synaptic

 
sry I am a noob when it comes to this everything I have learned I have done on my own via research or books.  Just running into an issue that have had no luck with.

You said this is a Server install, right?  So no Synaptic, there's no GUI in the Server edition.

Well, a quick&dirty way to see if it's just something holding a lock is to reboot.

To narrow down what has a lock on the config.dat file,```
lsof |grep config.dat
```

---

### Post by thunder63cs on 2011-06-15
> **arrrghhh said:**
> You said this is a Server install, right? So no Synaptic, there's no GUI in the Server edition.
 
Well, a quick&dirty way to see if it's just something holding a lock is to reboot.
 
To narrow down what has a lock on the config.dat file,```
lsof |grep config.dat
```
 
 
after I do that with out sudo I get nothing with sudo I get this:
 
frontend   7331       root    4uW     REG              251,0     60107    1966457 /var/cache/d         ebconf/config.dat

---

### Post by arrrghhh on 2011-06-15
> **thunder63cs said:**
> after I do that with out sudo I get nothing with sudo I get this:
 
frontend   7331       root    4uW     REG              251,0     60107    1966457 /var/cache/d         ebconf/config.dat

Hrm.  Well, root definitely has a lock on that file.  I'm not familiar with 'frontend' tho.  Doing a find on my system makes me think it's related to debconf.

I'm not really sure how to proceed... I could have you kill that process, not sure of the repercussions.  Have you tried simply rebooting?

---

### Post by thunder63cs on 2011-06-15
I have rebooted and ti ends up goign right back to that ..  Most of this started when I updated the bind9 package which it looks like it is still trying to install.  Is there a way to kill that package taht has been uunpacked but not installed yet?

---

### Post by arrrghhh on 2011-06-15
> **thunder63cs said:**
> I have rebooted and ti ends up goign right back to that ..  Most of this started when I updated the bind9 package which it looks like it is still trying to install.  Is there a way to kill that package taht has been uunpacked but not installed yet?

Oo it persists after a reboot...  That's very strange.

I very rarely have dpkg/installation issues, so I'm not really well-versed in troubleshooting issues related to it...

In other words, I don't think I'm qualified to tell you to start killing things - I would feel awful if my direction ended up making things worse.  Hopefully someone else chimes in to help...

---

### Post by thunder63cs on 2011-06-16
yea it would be nice.  Thanks for the help you did provide already.

---

### Post by smurphy_it on 2011-06-17
Found this with a google search.

I found the problem: I was running tasksel in another terminal, as a user. I didn't know running tasksel without privileges could mess up a configure script.

From:

[https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/380491](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/380491)

Not sure if it relates to you or not.  

Tasksel is a Debian/Ubuntu tool that installs multiple related packages as a co-ordinated "task" onto your system.  Looks like it runs in cli.  Are you running that program/process ?  if so, close out of it and you should be good.

```
sudo ps -ef | grep tasksel
sudo lsof | grep tasksel

```

---

### Post by thunder63cs on 2011-06-17
cool ..  I just found the issue when I was messing with things a few min before ya posted this.  I ended up going into the ect/resolveconf/ folders and deleting a few things I found there and wala no more issues have everything updated and working great again.   I hope that this helps soem one else out at some point.

---

### Post by smurphy_it on 2011-06-17
Good.

---

### Post by arrrghhh on 2011-06-17
> **thunder63cs said:**
> cool ..  I just found the issue when I was messing with things a few min before ya posted this.  I ended up going into the ect/resolveconf/ folders and deleting a few things I found there and wala no more issues have everything updated and working great again.   I hope that this helps soem one else out at some point.

Interesting.  Did you have stuff that was manually entered in there...?  Just curious, glad you fixed the issue tho ;).

---

