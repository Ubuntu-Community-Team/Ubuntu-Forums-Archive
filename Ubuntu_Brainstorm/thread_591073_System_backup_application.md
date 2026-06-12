---
title: "System backup application"
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by the.dark.lord on 2007-10-25
Something like Time Machine or Windows System Restore would be cool to have on Ubuntu...

---

### Post by smartboyathome on 2007-10-25
There is a project called TimeVault.

[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

---

### Post by the.dark.lord on 2007-10-25
> **smartboyathome said:**
> There is a project called TimeVault.

[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

I'm aware of that... shouldn't it be included by default?

EDIT: Isn't TimeVault only CLI?

---

### Post by smartboyathome on 2007-10-25
> **the.dark.lord said:**
> I'm aware of that... shouldn't it be included by default?

EDIT: Isn't TimeVault only CLI?

No, it has a GUI in Applications > System Tools. I use it all the time. :)

---

### Post by ubuntios on 2007-10-25
Hi there,

I just Download the timevault 0.7.4.deb, I install it , my system says ok, I can see it also on system tolls , but when I click it nothing happens.


What  I do wrong here??



Thanx in advance

---

### Post by smartboyathome on 2007-10-25
> **ubuntios said:**
> Hi there,

I just Download the timevault 0.7.4.deb, I install it , my system says ok, I can see it also on system tolls , but when I click it nothing happens.
I'm using Ubuntu 7.10

What  I do wrong here??



Thanx in advance

It opens in the tray. Click on the tray icon and it should come up.

---

### Post by Bruce M. on 2007-10-30
> **ubuntios said:**
> Hi there,

I just Download the timevault 0.7.4.deb

Thanx in advance

Where did you get it?
I did a search in Synaptic and can't see it.

---

### Post by coolen on 2007-10-31
I think, with a little work by the Ubuntu team on integration and configuration, this would be a really handy feature. Many new users may delete essential files (the root user can do anything, after all, even wipe the filesystem).
The average user isn't going to go about setting up incremental backups themselves, and probably wouldn't even recognise the need. Give it to them out of the box, and they may just use it.

---

### Post by erginemr on 2007-10-31
I am using plain ald console to back up my system. And my periodic backups saved my day more than once.
If you are insterested, please follow the steps given in the first post of:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

You may backup your entire system with tar (/), or may backup only your home page (/home/user_name) and config folder (/etc) which are the most critical ones. Then you can store the back up archive in a backup folder or write it to a CD-R or DVD-R. Restoring in case of a problem is really pretty easy and straightforward.

Other than that, I had the same urge to have a graphical backup manager and had installed Simple Backup Restore back in Edgy days:
[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

though, I never had a chance to actually use it. The decision is yours, but I would recommend the console way.

---

### Post by coolen on 2007-10-31
You can do differential backups using rsync and tar archives, too. A GUI which implements this, included by default, would be awesome. You could use this to easily backup to a remote server, too.
The command line work has been done, and is stable. I'm sure there are GUIs for it, too. It would be an incredibly useful feature for the next release (whose focus will probably be on stability, reliability, and system management).

---

### Post by Jonne on 2007-11-06
I came here to ask for 'simple backup' to be included by default, when I saw this (similar) thread. Apparently this useful little backup app has existed for ages, but nobody seems to know about it. I want it to be included by default, so it's more discoverable (it's in synaptic under the name 'sbackup').

Somehow improving it so it's easier to get an old file back without needing to open every tar.gz archive manually would be neat too.

---

### Post by ntetreau on 2007-11-10
Actually, the updated NSsbackup (Not So simple backup) builds on the strenghts of sbackup but ads much needed features like feedback about what is happening.  If one wants to include simplae backup, NSsbackup seems superior to me.

---

### Post by Jonne on 2007-11-10
Unfortunately it doesn't seem to be in the repo's for Gutsy yet. But if they can get it ready by Hardy, sure why not. I can't find any clues as to what's new/improved about it, though. Do you happen to know that?

---

### Post by migheleto on 2008-01-08
An EASY application for creating a System backup CD/DVD (apps, progs, configuration) and the possibility to include it when re-installing from alternate cd or live cd (on the same machine). Someting like Reconstructor, but easyer, without creating an entire installation cd from scratch. Only data's to use as add-on for an existing installation cd. 

(restore with backup CD? [yes] [no]) :arrow: Re-installation done =D>

---

### Post by smartboyathome on 2008-01-08
you can use remastersys, it does this.

---

### Post by oneferna on 2008-01-18
There is a basic backup GUI app in Synaptic, it's called sbackup. You can backup your system to a remote system too.

---

