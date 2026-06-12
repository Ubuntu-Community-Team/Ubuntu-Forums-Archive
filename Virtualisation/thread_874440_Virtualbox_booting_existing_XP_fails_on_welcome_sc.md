---
title: "Virtualbox booting existing XP fails on welcome screen"
date: 2008-07-29
forum: Virtualisation
---

### Post by spydirweb on 2008-07-29
I had some large problems setting up my VM the other day but I've gotten most everything set up at this point...  I've followed these howtos to get my system setup:

[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)
[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)
[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

Everything seems to be working fine, except I can't actually load windows.  Windows boots up fine, but when it gets to the login selection (Only one user that I set up to auto-login) it can't get past the screen with dark blue bars on top and bottom and lighter blue in the middle with the Windows XP logo.  I'm not sure where to look to figure out what's going on.  I've been reading thru the comments on all of these howto's, seeing a couple things that sound like possible close-tos or things to try, but no luck as of yet...  I'm tempted to try [http://ubuntuforums.org/showpost.php?p=5276934&postcount=64](http://ubuntuforums.org/showpost.php?p=5276934&postcount=64) (what sand lee says to rdiaztushman) but I'm worried about possibly losing the functionality I actually got from VBox normal vs. the nothing from VBox OSE...

Has anyone else had this problem or something similar?  Any clues for where to go, besides installing OSE?  I'd prefer not to if I don't have to.

---

### Post by tuxxy on 2008-07-29
Did it ever boot or has it always had this problem, if it has just started you could try making a new virtual drive and fresh install, I would stick to the supported software in the repos myself.

---

### Post by spydirweb on 2008-07-30
it's an existing XP.  It boots natively but has yet to boot fully thru VBox.

On a side note, I did try the OSE install real quick. It's erroring out on quite a bit of modules problems, and the real reason I'm doing all this is to 1) get rid of my XP laptop, 2) not have to reboot just to sync my iPhone, and the lack of USB support in OSE just won't work for me anyways...  Looks like my next day off work will be trying the vmware way of doing this...

---

### Post by tuxxy on 2008-07-30
If you only want to sync your phone, maybe just leave that existing XP and create another virtual one, once you enable USB for the virtual drive it should do this task.

---

### Post by cocopuffz on 2008-07-30
If you installed guest additions it can mess up your exsisting XP installation and corrupt your mbr. I had an exsisting xp install working through virtualbox. Worked fine until I did the guest additions install and bam.. killed it. I lost the XP install.

---

### Post by spydirweb on 2008-07-31
I was able to get the system up and running in VMWare-server 1.0.6.  However the USB devices seem to not work properly after installing VMWare tools, so I'm going to have to tinker with that...  I'm going to continue trying with virtualbox to, hopefully, see which one will work best for my overall.

---

### Post by Living2007 on 2008-07-31
> **spydirweb said:**
> I was able to get the system up and running in VMWare-server 1.0.6.  However the USB devices seem to not work properly after installing VMWare tools, so I'm going to have to tinker with that...  I'm going to continue trying with virtualbox to, hopefully, see which one will work best for my overall.
You've done the right thing, I'm ust having an educated guess, but with our original VM player, something might have blowing (eg. RAM or HDD). Who really knows.

Good Luck!

---

