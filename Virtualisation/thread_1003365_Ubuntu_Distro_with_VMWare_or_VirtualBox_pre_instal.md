---
title: "Ubuntu Distro with VMWare or VirtualBox pre installed"
date: 2008-12-06
forum: Virtualisation
---

### Post by drshahab on 2008-12-06
Hi
I am new to Linux & using Ubuntu for some time. I was very excited when I read about running windows XP within Linux, but reading the tutorials it appeared like a daunting task. Is there any chance that future version of Ubuntu may have Virtualization builtin (pre installed)?

---

### Post by matpol on 2008-12-06
Wine comes with or is available for ubuntu already - this allows you to run windows apps.

---

### Post by the yawner on 2008-12-06
> **drshahab said:**
> Hi
I am new to Linux & using Ubuntu for some time. I was very excited when I read about running windows XP within Linux, but reading the tutorials it appeared like a daunting task. Is there any chance that future version of Ubuntu may have Virtualization builtin (pre installed)?

I highly doubt that anyone would come up with such a distro. Why don't you give it a shot? I mean, install Virtualbox. I find it relatively easier than VMware. Cheers!

---

### Post by HotShotDJ on 2008-12-06
> **drshahab said:**
> Is there any chance that future version of Ubuntu may have Virtualization builtin (pre installed)?Highly unlikely, and probably unnecessary.  The installation of VirtualBox (for example) is trivial.  Point, click, done. The more complicated part is installing and configuring the guest operating system, which in the case of Windows, cannot be preinstalled in Ubuntu.

---

### Post by Zack McCool on 2008-12-06
Personally, I find VMWare Server a bit easier to install, on the grand scale.  While VirtualBox is in the Repos, if you want to set it up with bridged networking, it can be a pain.  Not to mention that the one in the repos doesn't include USB support.

VMWare Server 2.0 is pretty simple to install.  Go to the website and get a (free) license, download the tarball and extract it.  Install build-essential and linux-source, then run the vmware installer (the .pl file in the newly created directory from above).  Answer the questions with the defaults, and everything should just work.

Operationally, I like VMWare a little better than VB, but either will do what you want.

As to Wine, if it supports the apps you need, then it's a fine idea.  Easy to install, easy to use.  If it doesn't work with your app, though, it can be more of a pain than any virtualization product...   ;)

---

