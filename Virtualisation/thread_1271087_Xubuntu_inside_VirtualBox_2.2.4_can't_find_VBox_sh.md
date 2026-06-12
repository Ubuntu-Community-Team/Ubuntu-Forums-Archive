---
title: "Xubuntu inside VirtualBox 2.2.4 can't find VBox shares"
date: 2009-09-20
forum: Virtualisation
---

### Post by Zachs Kappler on 2009-09-20
I have used virtualBox before and loved being able to use XP without restarting for small windows only tasks. Well this month I had decided to build a distro based off Xubuntu but with a reworked/modified GUI. Only problem is I get this while mounting a VirtualBox share:

```
sudo: unable to resolve host AS-WORKSTATION-01
cjohnson@AS-WORKSTATION-01:~$ sudo mount -t vboxsf daniel /mnt/share
sudo: unable to resolve host AS-WORKSTATION-01
cjohnson@AS-WORKSTATION-01:~$ modprobe vboxvfs
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
cjohnson@AS-WORKSTATION-01:~$ 

```

I made the folder the share is supposed to go in, but it won't work. I have yet to find another way to carry over the theme stuff I made outside the VBox session either. 

Also noticed USB drives aren't spotted by VBox sessions with Linux inside. Any ideas on this?

---

### Post by scrooge_74 on 2009-09-20
Advice, go to virtualbox.org and download ver 3 and uninstall your present version, you are going to see a lot of difference from one version to the next

---

### Post by Zachs Kappler on 2009-09-20
Will do.

EDIT: After removing and installing Virtual Box to update it to 3.0.6, Xubuntu decided it had gone through enough and messed up some network stuff, so that broke any chance of sharing stuff with it EVER.

Going to try again, but to make sure this isn't just a Xubuntu thing, I'll try Mint 7 for now.

---

