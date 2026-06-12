---
title: "Unable to upgrade from 8.10 to 10.04"
date: 2010-05-29
forum: Server Platforms
---

### Post by mondo1287 on 2010-05-29
I have a Ubuntu Server machine that I can't get to 10.04.  Sometime in the past I updated it to 9.04, but perhaps something went wrong.  

When I do a do-release-upgrade, it tells me there are no upgrades available.  I tried a bunch of things but no luck, so I installed gnome to try the gui update manager on the console.  When I start it, it first tells me that my distribution is no longer supported and that I should update.  It gives me the button that says 9.04 is available, but after I click it I'm told that there are no new versions available.

---

### Post by ajgreeny on 2010-05-29
8.10 recently lost its support so you will need to update with a new install.  You would not be able to go from 8.10 direct to 10.04 in any case but would have had to do it in one version stages, 8.10 to 9.04, 9.04 to 9.10, and then 9.10 to 10.04.

Much simpler to start from scratch and do a clean install, after backing up all your configurations and files, etc etc.

---

### Post by mondo1287 on 2010-05-29
> **ajgreeny said:**
> 8.10 recently lost its support so you will need to update with a new install.  You would not be able to go from 8.10 direct to 10.04 in any case but would have had to do it in one version stages, 8.10 to 9.04, 9.04 to 9.10, and then 9.10 to 10.04.

Much simpler to start from scratch and do a clean install, after backing up all your configurations and files, etc etc.

The problem is I can't seem to get to 9.04.  I can't take this server down all day to do a reinstall.

---

### Post by mondo1287 on 2010-05-29
I definitely think sources.list was messed up, but it's still not working.  I removed everything from the third party tab in the software sources GUI.  It really seems like the system has 9.04 packages, but the update manager still thinks it's running 8.10.

---

### Post by mondo1287 on 2010-05-29
apt-cache policy python
python:
Installed: 2.6.2-0ubuntu1
Candidate: 2.6.2-0ubuntu1
Version table:
*** 2.6.2-0ubuntu1 0
500 [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) jaunty/main Packages
100 /var/lib/dpkg/status

So it looks like I've got all 9.04 packages installed.  How can I convince the system it's running 9.04 and not 8.10?

---

### Post by mondo1287 on 2010-05-29
I finally got this resolved. I manually edited /etc/lsb_release and /etc/issue to reflect 9.04. I'm now able to upgrade to Karmic.

---

