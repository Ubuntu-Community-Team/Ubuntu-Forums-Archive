---
title: "0wned!!!!!!!!"
date: 2005-04-17
forum: Server Platforms
---

### Post by goofrider on 2005-04-17
OK my box been 0wned this morning. I think I was on it while that happened. I was trying to delete some file and it says I had no permission to ~/.Trash.

Rebooting ends in  "/sbin/init not found error". fsck the drive found a bunch of "xxxx has unsused/deleted inode" errors. Looks like some script kiddy unlinked these dirs:


/etc,   /etc/* 
/home,   home/*,   /home/<username>/*
/usr,   /usr/* 
/var,   /var/*


Luckily I can still recover /var/lib/dpkg/status from /lost+found, so I can pretty much rebuild the entire system to the same point as it was. I just have to manually rebuild conffiles in /etc, plus crucial data dirs in /var and /home, 

I'll reinstall it on a new partition while keeping the old one for forensic.


This REALLY SUCKS, considering I just installed Ubuntu less than a month ago, and I just installed Snort + Acid + Firestarter this morning, plus a bunch of other tools like chrootkit, Oinkmaster, etc.

The box was inside NAT, only port 80, 25, 22 and 1194 are forwarded to it.

80: Apache 2
25: PostFix
22: OpenSSH
1194: OpenVPN

Iptables is configured to reject all incoming connections from outside my LAN, except on these 4 ports.

Well, I guess 4 ports can be too many...? LOL  Since Apache 2 and Postfix both run in chroot jail. I suspect it was either SSH or OpenVPN. What do u guys think?

---

### Post by -Rick- on 2005-04-17
As for SSH:
Its better to have it on an higher port(say 32000) and to not allow root access.
Further, if possible for you, you could set in an chroot aswell.

---

### Post by mendicant on 2005-04-17
What makes you think somebody got on vs something else happening (ide controller error, other disk errors)?  Were you up to date on security (if warty)?

---

### Post by goofrider on 2005-04-17
[QUOTE=-Rick-]As for SSH:
Its better to have it on an higher port(say 32000) and to not allow root access.
Further, if possible for you, you could set in an chroot aswell.[/QUOTE]

I thought root access is disabled by default. If not, it ought to be.

I typically set stuff like SSH and www admin on a higher port, but I didn't for this server because it was new and I was still testing the OS. I guess I need to be more careful no matter what.

What's the point of running SSH in chroot jail?  LOL

---

### Post by goofrider on 2005-04-17
[QUOTE=mendicant]What makes you think somebody got on vs something else happening (ide controller error, other disk errors)?  Were you up to date on security (if warty)?[/QUOTE]


Hmm, hardware errors unlinked the most important directories like /etc, /home, /var and everything 1 or 2 levels under it, but not deeper, and nothing else on the file system? I don't think so.

Hardware errors rarely caused errors hierachically: write errors usually appears reverse-chronically (i.e. the most recently written data are most vunerable), while sector-level failure appears to files at random locations in the file system. It's extremely unlikely that file system corruption or hardware failure causes these directories to corrupt in this systematic way.

BTW I'm running Hoary.

---

### Post by -Rick- on 2005-04-17
> What's the point of running SSH in chroot jail? LOL 
Your right...:) I meant its better to let people who log-in will be inside a chroot jail instead of /

---

### Post by nautilus on 2005-04-17
how close together do you think the highest level directory inodes will be to each other?

they are all created at the exact same time; installation time, and they're about the only files/folders which will never and HAVE never changed in any way (other than 'contents') since installation.

besides, wouldn't it be easier to just delete them, if somebody were so inclined to being a pest on your system?

sorry, it doesn't add up.  it's more likely your hard disc is shot, try running badblocks on it, i have a feeling it'll yield a few.

---

### Post by mendicant on 2005-04-17
[QUOTE=goofrider]Hmm, hardware errors unlinked the most important directories like /etc, /home, /var and everything 1 or 2 levels under it, but not deeper, and nothing else on the file system? I don't think so.
[/QUOTE]

It still doesn't seem like enough evidence to immediately conclude that there was unauthorized access to your system.  After all, I'd think they'd rather put it to further evil uses before doing anything else, or try to access other machines on your lan (if it was an apache hole, I suppose they couldn't do much to other machines).  While I think it's more correct to approach things as if somebody had broken in, I would also try to get evidence from other boxes that this was truly the case.

---

### Post by HungSquirrel on 2005-04-17
[QUOTE=goofrider]I thought root access is disabled by default.[/QUOTE]
Yes and no.  By default, the root account is locked down on Ubuntu.  If you unlock it and run sshd, root can login via ssh.  You must manually edit /etc/ssh/sshd_config and change PermitRootLogin to no.  I would also recommend disabling X11Forwarding unless you need it.

---

### Post by jdong on 2005-04-17
[QUOTE=goofrider]Hmm, hardware errors unlinked the most important directories like /etc, /home, /var and everything 1 or 2 levels under it, but not deeper, and nothing else on the file system? I don't think so.

Hardware errors rarely caused errors hierachically: write errors usually appears reverse-chronically (i.e. the most recently written data are most vunerable), while sector-level failure appears to files at random locations in the file system. It's extremely unlikely that file system corruption or hardware failure causes these directories to corrupt in this systematic way.

BTW I'm running Hoary.[/QUOTE]

If there was filesystem corruption (bad HDPARM, IDE cable noise, controller failure, drive failure) while writing to the metadata or superblock, it's very likely for TLD's to be unlinked. The FSCK unused/deleted inodes message is also a good indication of filesystem corruption, as opposed to an rm -rf.

I'd say this is just hardware failure, as opposed to an intrusion, unless firewall or system logs (you do send those nightly to another system or email, *right?* ;)) tell you otherwise.


PS, I assume you're using Ext3?

---

### Post by skoal on 2005-04-17
[QUOTE=goofrider]Hardware errors rarely caused errors hierachically: write errors usually appears reverse-chronically (i.e. the most recently written data are most vunerable), while sector-level failure appears to files at random locations in the file system. It's extremely unlikely that file system corruption or hardware failure causes these directories to corrupt in this systematic way.[/QUOTE]

It may be rare as you suggest, however, it did exactly that in my case when my firmware on my hardrive went schizo.  I was running a simple background task of 'du -sb' and the entire path plus a few other completely unrelated spots were affected.  I had started getting buffer errors and I think it tried to sync 'em back.  On next reboot, no init.  Fscked it.  Worked for a while.  Then wiped it clean.  Worked for a while.  Then even BIOS wouldn't give that drive any recognition lovin'.

That may not be your case here, but in case it is and your drive is completely unsuable in the fore-seeable future, just priv or email me and I'll share some recovery tips if you need 'em.  If you start to notice any random "buffer I/O' messages, chances are it's hardware failure. It might be a good idea to try the disk diagnostic tools on Ultimate Boot CD for your particular drive.

---

### Post by goofrider on 2005-04-18
[QUOTE=skoal]It may be rare as you suggest, however, it did exactly that in my case when my firmware on my hardrive went schizo.  I was running a simple background task of 'du -sb' and the entire path plus a few other completely unrelated spots were affected.  I had started getting buffer errors and I think it tried to sync 'em back.  On next reboot, no init.  Fscked it.  Worked for a while.  Then wiped it clean.  Worked for a while.  Then even BIOS wouldn't give that drive any recognition lovin'.

That may not be your case here, but in case it is and your drive is completely unsuable in the fore-seeable future, just priv or email me and I'll share some recovery tips if you need 'em.  If you start to notice any random "buffer I/O' messages, chances are it's hardware failure. It might be a good idea to try the disk diagnostic tools on Ultimate Boot CD for your particular drive.[/QUOTE]

yeah, now that I got some time to think about it, it's probably a file system corruption. It might have been a bad fsck cmd I ran.

I was pretty lucky that all of my /home data was recovered, and /var/mysql. Still need to try to recover some of the rest of /var but I think I don't need most of it.

I also happened to install Backuppc a few days ago. I haven't done any configuration to it yet but I just found out it backed up my /etc everyday by default, needless to say it saved me a lot of time.

I guess this corruption give me the excuse to repartition each of the main directories to separate volumes using LVM, so file system corruptions can be contained; and get serious about backing up.

---

### Post by TravisNewman on 2005-04-18
One thing you will learn the hard way (more than once if you make mistakes like I did ;)) is that being diligent about backups is VERY important! :)

---

### Post by jdong on 2005-04-18
Having GMail account**(s)** is also a great idea ;)

---

### Post by TravisNewman on 2005-04-18
yes, oh yes, that has saved me before too :) When there's NOTHING to back up to, gmail is a lifesaver.

---

### Post by wmcbrine on 2005-04-18
I tend to suspect filesystem corruption too, rather than intrusion. The one time my system got 0nwz0red, they did much more interesting things than trashing it. Rather, they installed (or tried to install -- see below) a rootkit. Had they succeeded, it would've allowed them to continue using my system, without it showing up in my logs. That's usually the goal.

In my case the attempt failed because my system was too archaic -- it was strictly libc5, and they were trying to install libc6 (glibc)-based stuff. Heh.

Annoyingly, even though I also had "insecure" telnet and ftp ports open, they got in through a vulnerability in SSH.  ](*,)

After that, I just closed off my system to the outside world. I could count on one hand the number of times I'd actually *used* the ability to log in remotely (outside my LAN), so I just decided to do without it. If I ever need it (and know beforehand), I can reactivate it temporarily. And nowadays, I only let my hardware router face the Net.

P.S. Another time, I badly corrupted the filesystem on the same system (a 486) by trying to run hdparm on it. So I do have a point of comparison. :)

---

