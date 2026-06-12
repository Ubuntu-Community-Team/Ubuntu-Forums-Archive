---
title: "Upgrade Linux Mint from 21.1 --&gt; 21.2 without a GUI?"
date: 2023-08-27
forum: Ubuntu/Debian BASED
---

### Post by TheFu on 2023-08-27
I'm trying to figure out how to upgrade Mint from 21.1 ---> 21.2 without a GUI.  I've swapped out the DE and use fvwm as a window manager.  Can't seem to get any DE to start.  I see some Mate and some Cinnamon programs/packages.

Running 
```
$ mintupdate
/usr/lib/linuxmint/mintUpdate/mintUpdate.py:1338: DeprecationWarning: Gdk.threads_init is deprecated
  Gdk.threads_init()
module 'cinnamon' has no attribute 'UpdateManager'
<class 'AttributeError'>


```and nothing happens. The program closes. 
```
sudo apt full-upgrade
``` doesn't work either.

I'm using Mint to avoid snaps for desktop applications, but generally run the apps I need over a remote X11 ssh tunnel to my local workstation.
I searched the system for .desktop files. The /usr/share/applications/mintupdate.desktop **Exec=mintupdate** is it, so it should work.

Ideas?  I get that 21.1 and 21.2 aren't really big updates, no kernel differences, so there isn't much that I'd get that would actually matter. Other apps like thunderbird, firefox, libreoffice are all being maintained through APT already and that's working.

Just seems odd that a specific GUI is required to perform updates for any Linux OS.

BTW, I removed all the PPAs (only 2) and told Synaptic to fix broken packages.  Both/neither worked to correct the mintupdate problem.
Idea's?

---

### Post by #&amp;thj^% on 2023-08-27
I always use this method, but I know what I've done and needs to be fixed first.
You do as well so my method:
```
sudo sed -i 's/vera/victoria/g' /etc/apt/sources.list.d/official-package-repositories.list
```
And to be safe I check with:
```
sudo nano /etc/apt/sources.list.d/official-package-repositories.list
```
EDIT: I forgot this the recommended command to start the upgrade:
```
sudo apt-get dist-upgrade
```
After the update command but you knew that.
Hope that works for you as well, Safe journey....

---

### Post by TheFu on 2023-08-28
I did it yesterday and it worked. Thanks!  That should have been obvious - it is the debian way.  Guess I'm spoiled by the do-release-upgrade tool in Ubuntu.
I am a little impressed - I haven't rebooted, yet it says I'm on victoria now.  No reboot is needed either.

```
$ uptime
 11:20:48 up 2 days,  2:47,  3 users,  load average: 0.05, 0.08, 0.08

$ lsb_release -a
No LSB modules are available.
Distributor ID: Linuxmint
Description:    Linux Mint 21.2
Release:        21.2
Codename:       victoria

$ ll /var/run/reboo*
ls: cannot access '/var/run/reboo*': No such file or dir
```

---

