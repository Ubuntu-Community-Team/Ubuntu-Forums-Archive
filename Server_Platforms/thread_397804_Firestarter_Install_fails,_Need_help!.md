---
title: "Firestarter Install fails, Need help!"
date: 2007-03-31
forum: Server Platforms
---

### Post by alextj on 2007-03-31
Hi!
I was using Firestarted for internet connection sharing for a while and recently I have uninstalled Firestarter, because I thought I didn't need it anymore.

Well, today I had to install it again, but installation script gives errors and Firestarter is not starting after the installation.

I am running latest feisty (note, firestarter was working with this same kernel before). x86

Here is installation error that I get:
```
sudo aptitude install -fy firestarter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  firestarter 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/393kB of archives. After unpacking 1929kB will be used.
Writing extended state information... Done
Selecting previously deselected package firestarter.
(Reading database ... 101763 files and directories currently installed.)
Unpacking firestarter (from .../firestarter_1.0.3-1.3ubuntu2_i386.deb) ...
Setting up firestarter (1.0.3-1.3ubuntu2) ...
 * Starting the Firestarter firewall...                                  [fail] 
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firestarter (1.0.3-1.3ubuntu2) ...
 * Starting the Firestarter firewall...                                  [fail] 
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 firestarter
```

Here is what I get when I am trying to start Firestarter:
```
A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.
Firestarter will now close.
```

Damn! :confused:

Can anybody help?
Is there anything else I can do to share internet connection with another computer?

Thanks!!

---

### Post by alextj on 2007-03-31
Well, after some help from #ubuntu IRC channel, I managed to uninstall and reinstall Firestarter without errors!

I am not quite sure how this happened, because I did many things, but it started working after I messed around with Broken packages filter.

---

