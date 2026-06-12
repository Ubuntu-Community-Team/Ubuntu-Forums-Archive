---
title: "dpkg-reconfigure weird problem"
date: 2011-03-22
forum: Server Platforms
---

### Post by dirtylobster on 2011-03-22
I was going to update the system (apt-get update && apt-get upgrade) but it needed to reconfigure phpmyadmin (using dpkg-reconfigure) which I for some reason couldn't navigate. The normal keys for this are space for ticking a checkbox, arrows to move up and down, tab to move around the different fields and enter to ok/cancel/next. None of these works. I got past the phpmyadmin configuration somehow, don't really know why, but there are still three unconfigured packages and when running apt-get upgrade it invokes dpkg-reconfigure console-setup which I can't for my life seem to navigate.

When I press up, it just outputs ^[[A, down ^[[B etc. and the colors are all weird.

[IMG]http://dl.dropbox.com/u/138305/images/dpkg-reconfigure-problem.png[/IMG]

Tab just does what tab usually does (hops to the right) and enter seems to work in the sense that it exists the installation with error: 

```
# apt-get upgrade

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Setting up console-setup (1.21ubuntu9) ...
dpkg: error processing console-setup (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of kbd:
 kbd depends on console-setup | console-common; however:
  Package console-setup is not configured yet.
  Package console-common is not installed.
dpkg: error processing kbd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of inithooks:
 inithooks depends on kbd; however:
  Package kbd is not configured yet.
dpkg: error processing inithooks (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 console-setup
 kbd
 inithooks
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What could be the cause of (and fix for) this? As for terminals I've tried Putty, Shellinabox, Gnome-terminal and Xterm so the problem is definitely serverside.

I'm running [Turnkey Linux](http://www.turnkeylinux.org) fwiw.

---

### Post by obsidiandh on 2011-03-27
Try ```
dpkg-reconfigure -freadline <packagename>
``` that will use the readline interface instead of the default dialog interface, the dialog interface sometimes doesn't work if your console setup is broken (which it appears yours is), try running dpkg-reconfigure on console-setup first.

---

