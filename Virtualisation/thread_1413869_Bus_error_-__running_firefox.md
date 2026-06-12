---
title: "Bus error -  running firefox"
date: 2010-02-23
forum: Virtualisation
---

### Post by koba101 on 2010-02-23
I have a karmic 32 bit guest inside a virtualbox (host is also karmic).  I've updated to the latest firefox version in the guest OS.  When I try to run firefox, I get a "bus error" message.

I thought this might be  virtualization issue so I posted it here.

Anyone encounter shuch a problem before?

---

### Post by yogesh.girikumar on 2010-02-23
Hi,


       This issue has been out there for quite sometime. This is not specific to Virtual Box. It has been reported several times even in non-virtualized environments.


   The most common solution is to remove and reinstall firefox , xulrunner and (if installed) ubifox packages. 
```
$ sudo aptitude remove firefox xulrunner ubifox
```then..
```
$ sudo apt-get install firefox
```  Make sure that you make a backup of your firefox folder. 
```
$ mv ~/.mozilla ~/.mozilla_backup
```      **If you want to force a rollback of the update**
   Open Synaptic package manager:
```
System --> Administration --> Synaptic Package Manager 
```click on File --> History
Search for the "Firefox" "Xulrunner" and "Ubifox" packages to find out what changes have been made to them.      To revert back to an older version close the history window and search for the package in the Synaptic Package Manager Window. After you've found out the package, click on the package and press CTRL+E.

       Click the drop-down menu and select an earlier version and click "Force Version". Then click "Apply". This will revert the package back to the earlier version.

    Hope this solves the issue.

---

### Post by koba101 on 2010-02-27
yogesh,,,thanks for the hint....i actually figured out i had to remove ubuntu-desktop as well....and then i reinstalled everything back.....and it worked, propbably the eclipse installation (or maybe java) messed up with xulrunner

---

