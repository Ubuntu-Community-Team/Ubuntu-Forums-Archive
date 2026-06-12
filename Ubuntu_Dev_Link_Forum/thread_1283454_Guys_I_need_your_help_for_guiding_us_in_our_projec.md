---
title: "Guys I need your help for guiding us in our project"
date: 2009-10-05
forum: Ubuntu Dev Link Forum
---

### Post by kapmsd on 2009-10-05
My team is developing SYSTEM RESTORE in linux which will be:
a,Independent of file systems.
b,Independent of desktops,GNOME/KDE.
c,Adding Restoration option from GRUB menu et al.

These are all our ideas.
This is the first time we are trying our hands in system level app in Linux.
Pls provide ur i/ps reg feasibility or other constraints we may face during implementation.
Thanks in advance for ur inputs

---

### Post by dinxter on 2009-10-08
Hi there, it sounds like an interesting idea but I'm not quite sure I understand what your project is. What exactly will system restore try to do, what will it try to restore? Depending on what your program is doing, and what licence you intend to use, you may be able to use some functionality from other freely licensed programs too

---

### Post by kapmsd on 2009-10-15
We are gonna to develop it in Ubuntu.
Our product would do:
a,Auto restore point creation before updates are installed.
b,Manual restore points like that in Windows.
c,Restoration facility made available from GRUB menu.
d,Application wise rollback
e,Independent of file systems,GNOME,KDE etc.

---

### Post by dinxter on 2009-10-23
> **kapmsd said:**
> We are gonna to develop it in Ubuntu.
Our product would do:
a,Auto restore point creation before updates are installed.
b,Manual restore points like that in Windows.
c,Restoration facility made available from GRUB menu.
d,Application wise rollback
e,Independent of file systems,GNOME,KDE etc.

I suppose the simplest way I can think of of 'application rollback' is to keep a copy of the current packages before installing the new ones, though downgrading packages is less well tested than upgrading, but this isnt really adequate for proper restoration of state. 
using some sort of version control system might make sense i suppose to actually restore package settings, files created on installation and so on. 
Is there a reason for having a restoration option in grub? I can't immediately think of a why its useful, though that would depend on exactly what kind of state backup method your going to use
All and all it sounds like an ambitious project, If you have  any firm detail of how you're going to do this I'd be interested to hear how your going to go about it, I'll try to offer any sensible advice if I can.
A simple restoration of older package versions and /etc/ configuration files seems reasonably achievable, but isnt a a full restoration ability. Whereas s fully restorable state seems quite complex and would seem to involve an awful lot more work, hard drive space, and testing, but obviously would be more complete 
I'm sure there are many other ways of doing this I can't think of off the top of my head so If you post more information when you have decided on the details of your project I would be interested to hear them. good luck!

---

### Post by calanor on 2009-10-31
one problem i faced while using fedora, it came with a beta of mozilla firefox 3.5, i updated it to 3.5.3 and installed addons, but i messed it up because of ati drivers and had to reinstall it, as with all the linux distros, it took the settings from home folder and firefox couldn't start due to addons, i have to have a browser to login into our college server, so i couldn't update the damn thing, i had to use the root version of firefox.

things like this might happen when you try to restore the system to use a lower version of any application

---

### Post by jpmelos on 2009-10-31
This project sounds very interesting, and I totally support the idea! It's been three weeks since you created the thread, how is it going?

---

### Post by phillw on 2009-11-03
> **calanor said:**
> one problem i faced while using fedora, it came with a beta of mozilla firefox 3.5, i updated it to 3.5.3 and installed addons, but i messed it up because of ati drivers and had to reinstall it, as with all the linux distros, it took the settings from home folder and firefox couldn't start due to addons, i have to have a browser to login into our college server, so i couldn't update the damn thing, i had to use the root version of firefox.

things like this might happen when you try to restore the system to use a lower version of any application


For your settings in your home directory, a variant on this backup script would 'keep you safe'

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

As mentioned, packages are somewhat trickier ... this thread may give you some insight ...

[B][http://ubuntuforums.org/showthread.php?t=1057608&highlight=synaptic+package+manager](http://ubuntuforums.org/showthread.php?t=1057608&highlight=synaptic+package+manager)

[/B]both are well supported threads and should give you some insight into what you are wishing to achieve.

```
dpkg -l
```May also be of help, for taking a 'screen-shot' of what you currently have, then, I guess a 'diff' command could point you towards what has changed.

As for firefox... lovinglinux keeps an excellent thread over at [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Certainly an interesting project, I wish you well on it.

Phill.

---

### Post by stderr on 2009-11-04
Sounds great! A few questions - is there a project page or suchlike we can track progress on? Also, do you have a specific future distro in mind for inital release, or is such discussion premature?

The main use for this that I can see is pre- dist-upgrade, as a rollback if everything goes wrong/the power cuts out/...  I'm very interested to hear what kind of implementation you're going for. What would get "backed up"? Would successive backups make use of symlinks/(whatever other appropriate mechanism) for unchanged files to save disk space? Could even altered files just have the altered data stored plus some instructions for re-insertion in the event of a restore?

---

### Post by phillw on 2009-11-15
> **stderr said:**
> Sounds great! A few questions - is there a project page or suchlike we can track progress on? Also, do you have a specific future distro in mind for inital release, or is such discussion premature?

The main use for this that I can see is pre- dist-upgrade, as a rollback if everything goes wrong/the power cuts out/...  I'm very interested to hear what kind of implementation you're going for. What would get "backed up"? Would successive backups make use of symlinks/(whatever other appropriate mechanism) for unchanged files to save disk space? Could even altered files just have the altered data stored plus some instructions for re-insertion in the event of a restore?


If you want a pre-dist upgrade backup, then I'd suggest the backup thread from my earlier post. It does take a little to configure - but WILL restore an entire system.

I'm hoping these guys do make it into a project - I have no knowledge of GUI, only command line stuff :-)

Phill.

---

### Post by kapmsd on 2009-11-17
Guys!!Its been a while i am back here.
We will analyse our project implementation by this year end after our semester exams(December mid week).
I will keep you updated in this post or new post as we expect good inputs from you guys!!
Thanks a lot !!

---

