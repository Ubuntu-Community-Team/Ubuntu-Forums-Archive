---
title: "Virtualbox crashes host in 9.10"
date: 2009-12-09
forum: Virtualisation
---

### Post by chipper_farley on 2009-12-09
About two months ago I took the plunge and installed Ubuntu 9.04 on my HP Compaq nc8430 laptop.  All went very well.  In order to run a handful of Windows apps I have to have, I installed Virtualbox from the Sun website and again all went well.  

So, after 9.10 came out I decided to install that.  I used the VBoxManage clonehd utility to clone the vdi images of the various machines I had setup (XP, RHEL 4, and CentOS) and moved those off the laptop.  I then did a full install of 9.10, formatting the hard drive and doing a fresh install.

After that, I moved the vdi's back to the normal local directories on the laptop and started using them.  All seemed well for a while but pretty soon I started having major crashes when running virtualbox.  It seems to occur when there is higher CPU demand from the VM but there is really no indication that the crash is coming.  When it does come, often the crash comes in phases.  First the VM won't respond but the gnome menus can be opened and windows minimized and maximized.  Then that stops working but the mouse can still be moved around.  Then the mouse freezes.  There is no way out except to power the laptop off and reboot.  I have not been able to find any logging that indicates what has happened although I might have missed something.  This occurs with both the OSE version and the full version.  Also, once a VM has caused one of these crashes, the time it takes for it to cause one in subsequent sessions is much less.

Unfortunately, this issue has forced me to go back to 9.04 where everything works great.  Has anyone else seen this issue?  Oh...sorry for being so wordy...just trying to be complete.

---

### Post by chipper_farley on 2009-12-16
Anyone?

---

