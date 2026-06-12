---
title: "Snapd problem."
date: 2018-07-21
forum: Ubuntu Development Version
---

### Post by cariboo on 2018-07-21
This is the second time I've run into this problem:

```
Setting up snapd (2.34.1+18.10) ...
snapd.snap-repair.service is a disabled or a static unit, not starting it.
```

The first time I just reinstalled as there were other problems that I couldn't be bothered to solve, due my negligence more than anything else. This is getting frustrating, as I can't do any updates.

Bug report here:

[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1781919](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1781919)

---

### Post by #&amp;thj^% on 2018-07-21
My workaround for Ubuntu 18.10:

```
sudo dpkg -r snapd gnome-software-plugin-snap
sudo apt update
sudo apt full-upgrade


```
Hope this works for you too.

---

### Post by cariboo on 2018-07-21
I'll give it a try when I get home from work tonight.

---

### Post by P-I H on 2018-07-21
I also got this problem a 2:nd time some days back. Fixed it with info from this thread
[https://ubuntuforums.org/showthread.php?t=2393347](https://ubuntuforums.org/showthread.php?t=2393347)

---

### Post by rrnbtter on 2018-07-21
Greetings,
This works for me
```
 sudo apt remove --purge snapd 
```

---

### Post by corradoventu on 2018-07-23
also [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1776622](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1776622)
if you remove snapd you lose all the snap applications: calculator, characters, monitor...
problem can be solved following the suggestion in [https://ubuntuforums.org/showthread.php?t=2393347](https://ubuntuforums.org/showthread.php?t=2393347)

---

### Post by rrnbtter on 2018-07-23
Greetings,

> **corradoventu said:**
> 
if you remove snapd you lose all the snap applications: calculator, characters, monitor...


I have been using Gnome/Wayland since it arrived with the Bionic cycle and don't care to use anything else. Since my "updates" were being locked by a conflict between apparmor and snapd I removed snapd to clear dpkg to update. If they get it fixed and I think I need snapd I can reinstall it and the needed snap apps. In the mean time I can update as needed. I have Cosmic installed on a new Lenovo 320-15 with four gig of ram and this is the very best OS I have ever used since 1986. Right now, just need to update, thats all. Hence remove snapd. But thanks for the threads.

---

### Post by VMC on 2018-07-23
> **rrnbtter said:**
> Greetings,
This works for me
```
 sudo apt remove --purge snapd 
```
I don't think that's what the OP has in mind.

---

### Post by cariboo on 2018-07-23
Actually I would like to get rid of snapd, but in order to remove it, it needs to be installed properly. I'm running into a failed package install loop. When trying to install the latest version I now get:

```
Setting up snapd (2.34.2+18.10) ...
snapd.snap-repair.service is a disabled or a static unit, not starting it.
```

---

### Post by #&amp;thj^% on 2018-07-23
**I can't promise** it wont break your system but if you want to give it a go:
```
sudo fuser -vki /var/lib/dpkg/lock
sudo apt purge snapd
sudo dpkg --configure -a
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo apt install snapd
```
Fingers Crossed
BTW The old method of ridding your self of snapd still worked for me via:
```
sudo apt purge snapd ubuntu-core-launcher squashfs-tools
```
Mine was an upgrde to 18.10 so I was lucky this still worked for me.
```
apt policy  snapd ubuntu-core-launcher squashfs-tools
snapd:
  Installed: (none)
  Candidate: 2.34.2+18.04
  Version table:
     2.34.2+18.04 500
        500 http://archive.ubuntu.com/ubuntu bionic-proposed/main amd64 Packages
     2.33.1+18.04ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
     2.32.5+18.04 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
ubuntu-core-launcher:
  Installed: (none)
  Candidate: 2.34.2+18.04
  Version table:
     2.34.2+18.04 500
        500 http://archive.ubuntu.com/ubuntu bionic-proposed/universe amd64 Packages
     2.33.1+18.04ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     2.32.5+18.04 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
squashfs-tools:
  Installed: (none)
  Candidate: 1:4.3-6ubuntu0.18.04.1
  Version table:
     1:4.3-6ubuntu0.18.04.1 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
     1:4.3-6 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```
And as above still works for 18.04

---

### Post by cariboo on 2018-07-24
> **1fallen said:**
> **I can't promise** it wont break your system but if you want to give it a go:
```
sudo fuser -vki /var/lib/dpkg/lock
sudo apt purge snapd
sudo dpkg --configure -a
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo apt install snapd
```
Fingers Crossed
BTW The old method of ridding your self of snapd still worked for me via:
```
sudo apt purge snapd ubuntu-core-launcher squashfs-tools
```
Mine was an upgrde to 18.10 so I was lucky this still worked for me.
```
apt policy  snapd ubuntu-core-launcher squashfs-tools
snapd:
  Installed: (none)
  Candidate: 2.34.2+18.04
  Version table:
     2.34.2+18.04 500
        500 http://archive.ubuntu.com/ubuntu bionic-proposed/main amd64 Packages
     2.33.1+18.04ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
     2.32.5+18.04 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
ubuntu-core-launcher:
  Installed: (none)
  Candidate: 2.34.2+18.04
  Version table:
     2.34.2+18.04 500
        500 http://archive.ubuntu.com/ubuntu bionic-proposed/universe amd64 Packages
     2.33.1+18.04ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     2.32.5+18.04 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
squashfs-tools:
  Installed: (none)
  Candidate: 1:4.3-6ubuntu0.18.04.1
  Version table:
     1:4.3-6ubuntu0.18.04.1 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
     1:4.3-6 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```
And as above still works for 18.04

That worked until I reinstalled snapd :)  I filed a bug, [lpbug]1776622[/lpbug], there is a similar workaround:

```
sudo killall apt dpkg
sudo dpkg -r snapd gnome-software-plugin-snap
sudo apt update
sudo apt full-upgrade
```

Thanks for the help.

---

### Post by #&amp;thj^% on 2018-07-24
> **cariboo said:**
> 
```
sudo killall apt dpkg
sudo dpkg -r snapd gnome-software-plugin-snap
sudo apt update
sudo apt full-upgrade
```

Thanks for the help.
Your Welcome and thanks for the above similar workaround. I'll keep that one in my back pocket. :)
I also found this one worth checking out in the report by corrado venturini (corradoventu) 
```
after changing /var/lib/snapd/seed/seed.yaml as suggested in [https://ubuntuforums.org/showthread.php?t=2393347&page=3 ]("https://ubuntuforums.org/showthread.php?t=2393347")sudo dpkg --configure -a works fine.
```

---

### Post by VMC on 2018-07-24
> **cariboo said:**
> Actually I would like to get rid of snapd, but in order to remove it, it needs to be installed properly. I'm running into a failed package install loop. When trying to install the latest version I now get:

```
Setting up snapd (2.34.2+18.10) ...
snapd.snap-repair.service is a disabled or a static unit, not starting it.
```
Maybe then I'm missing something already said. I always remove *snapd*, without issue. I have no need for it. 
Why can't you remove it then. Did you install a snap product first, then tried removal?

---

### Post by cariboo on 2018-07-24
> **VMC said:**
> Maybe then I'm missing something already said. I always remove *snapd*, without issue. I have no need for it. 
Why can't you remove it then. Did you install a snap product first, then tried removal?

On that system, it's a pretty well default cosmic installation with my most used apps. The snaps were installed as part of that installation. I'm trying to keep the system as stock as possible for now.

I actually want to get rid of all the installed snaps, but having a broken snapd won't allow me to do that.

---

### Post by mc4man on 2018-07-25
This should no longer be an issue on fresh 18.10 installs using current image.

As far as included snap apps, there is only 1, gnome-calculator. It can't run from the fresh install & users would be hard pressed to fix.
(- can be  made usable by removing snapd, installing snapd, installing the gnome-calculator snap,  though why bother.., just install the .deb

---

