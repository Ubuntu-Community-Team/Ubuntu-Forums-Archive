---
title: "HAL missing for Flash DRM playback in 15.10"
date: 2015-11-07
forum: Ubuntu Studio
---

### Post by jmarkus on 2015-11-07
Terminal 
sudo apt-get install hal

[sudo] password for dad:
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package hal is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'hal' has no installation candidate

Adobe troubleshooting reports..."If the Hardware Abstraction Layer module  is  missing, Flash Player still functions. However, it cannot play   protected content that requires the Adobe Flash Access DRM (Digital   Rights Management) module."

This also was working in 14.04, but not now. Is there another source, workaround, or set of terminal commands that can get this working again?

---

### Post by ueter on 2015-11-23
There is a PPA version here:
 [https://launchpad.net/~flexiondotorg/+archive/ubuntu/hal-flash](https://launchpad.net/~flexiondotorg/+archive/ubuntu/hal-flash)

---

