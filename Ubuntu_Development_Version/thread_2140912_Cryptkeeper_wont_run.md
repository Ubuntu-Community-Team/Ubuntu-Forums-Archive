---
title: "Cryptkeeper wont run"
date: 2013-05-01
forum: Ubuntu Development Version
---

### Post by jimafternoon on 2013-05-01
I installed cryptkeeper, but when I try to open it, nothing happens. 

I've been reading up on it, and on earlier versions it was suggested that using dconf-editor to add it to the whitelist was the fix to get it to open in the system tray. 

However, I also read that this whitelisting procedure is obsolete in 13.04. 

Thanks for any help, or for any suggestions for alternative tools.

---

### Post by dino99 on 2013-05-01
> **jimafternoon said:**
> I installed cryptkeeper, but when I try to open it, nothing happens. 

I've been reading up on it, and on earlier versions it was suggested that using dconf-editor to add it to the whitelist was the fix to get it to open in the system tray. 

However, I also read that this whitelisting procedure is obsolete in 13.04. 

Thanks for any help, or for any suggestions for alternative tools.

Cant say about unity, but if you login GS and add an extension for displaying icon (extensions.gnome), then it might work.

---

### Post by Irihapeti on 2013-05-01
As an alternative, there is gnome encfs manager which is said to run with Unity out of the box. (I haven't tried it with Unity, so can't confirm that.) Currently, it's available from a PPA, though there seems to be a request to have it included in the official repos: [https://bugs.launchpad.net/ubuntu/+bug/1080327](https://bugs.launchpad.net/ubuntu/+bug/1080327)

---

### Post by jfernyhough on 2013-05-01
Quick +1 for GEncFSMan. Arguably better than Cryptkeeper anyway. :)

---

### Post by alphacrucis2 on 2013-05-01
Another +1.  I ditched crypt keeper and switched to gnome encfs manager. Even if cryptkeeper was fixed I wouldn't bother going back.

---

### Post by jimafternoon on 2013-05-01
Thanks!!

---

### Post by gz1derbread on 2013-12-05
You can get Gnome Encfs Manager by typing the following into terminal:
sudo add-apt-repository ppa:gencfsm && sudo apt-get update && sudo apt-get install gnome-encfs-manager

---

### Post by cariboo on 2013-12-05
This looks like it is concerning Saucy, since we are now in the Trusty development cycle, there is no need for this thread. Closed,

---

