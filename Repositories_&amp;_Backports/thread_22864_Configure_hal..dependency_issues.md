---
title: "Configure hal..dependency issues??"
date: 2005-03-30
forum: Repositories &amp; Backports
---

### Post by dmgedgoods on 2005-03-30
here is my issue:  I am trying to install pkgs of all sorts from synaptic. when the terminal pops up, the below messages generate. Now...i'm imagining that i have to manually configure these files...how do i go about fixing this? Please help me!!


root@dmgedgoods:~ # apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up hal (0.2.98-1ubuntu9) ...
adduser: The group hal' already exists.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on hal (>= 0.2.92); however:
  Package hal is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-device-manager:
 hal-device-manager depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-device-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-volume-manager; however:
  Package gnome-volume-manager is not configured yet.
 ubuntu-desktop depends on hal; however:
  Package hal is not configured
 yet.
 ubuntu-desktop depends on hal-device-manager; however:
  Package hal-device-manager is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 gnome-volume-manager
 hal-device-manager
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by fdoving on 2005-03-30
try:
```

sudo delgroup hal
sudo dpkg --configure -a

```

---

### Post by dmgedgoods on 2005-03-31
it says :

root@dmgedgoods:~ # sudo delgroup hal
/usr/sbin/delgroup: There are users having `hal' as primary group!
root@dmgedgoods:~ # sudo dpkg --configure -a
Setting up hal (0.2.98-1ubuntu9) ...
adduser: The group hal' already exists.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-volume-manager:
 gnome-volume-manager depends on hal (>= 0.2.92); however:
  Package hal is not configured yet.
dpkg: error processing gnome-volume-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-volume-manager; however:
  Package gnome-volume-manager is not configured yet.
 ubuntu-desktop depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-device-manager:
 hal-device-manager depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-device-manager (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 gnome-volume-manager
 ubuntu-desktop
 hal-device-manager
root@dmgedgoods:~ #

---

