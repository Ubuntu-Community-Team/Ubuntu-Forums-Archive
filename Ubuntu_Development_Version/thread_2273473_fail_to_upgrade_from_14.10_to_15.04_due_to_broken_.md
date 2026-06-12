---
title: "fail to upgrade from 14.10 to 15.04 due to broken packages"
date: 2015-04-13
forum: Ubuntu Development Version
---

### Post by petran79 on 2015-04-13
I purged all PPAs and removed most of the applications and their dependencies.

however after trying to upgrade to the latest version, I see there are still issues with dependencies.
Upgrader stops after checking the vivid sources list.

I have no idea which files to install, remove or reinstall and if they can be removed or installed either....

upgrader directs me to launchpad.net

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1443476](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1443476)

---

### Post by grahammechanical on 2015-04-13
What method are you using to upgrade from utopic to vivid? What command?

Due to the fact that 15.04 is not yet released the method which uses Software Updater may not be available or have the right scripts. After all, vivid is still a moving target. For example, it just got another version of kernel 3.19. 

I am of the opinion that (a) upgrading from one stable release to the next stable release after release day is fine and (b) upgrading from the last stable release to the development release in the early weeks of the development cycle is also fine, but once the development period is well under way it is better to install the latest daily image ISO and go from there if we want to move forward without too much going wrong.

Was utopic updated and upgraded before attempting the upgrade?

Regards.

---

### Post by dino99 on 2015-04-13
cant see something special into your report. Have you manually modified /etc/apt/sources.list (utopic -> vivid) ? or used something else ?
i suppose you still can go on using synaptic

---

### Post by ian-weisser on 2015-04-13
What happens if you do an ordinary 14.10 upgrade instead of a release-upgrade?
Do you get any package errors?

---

### Post by Alan F on 2015-04-13
Why not just get a copy of the Vivid .iso and re-install rather than upgrade?

Then you have a clean system with no dependency concerns.

---

### Post by petran79 on 2015-04-13
> **ian-weisser said:**
> What happens if you do an ordinary 14.10 upgrade instead of a release-upgrade?
Do you get any package errors?

No packages are fine, I only use the default ones. Problem was that some libldap-2.4-2 error and I had to remove most software in order to remove the file as well. But to no avail. 
Software  refuses to install and I get constant dpkg errors. 

> **Alan F said:**
> Why not just get a copy of the Vivid .iso and re-install rather than upgrade?

Then you have a clean system with no dependency concerns.

I think this will probably be the best solution. 
14.10 broke and I cant install anything.

Problem was I added too many PPAs in 14.04 and system got messed up that even a PPA purge wasnt enough.
Upgrading to 14.10 solved some issues but not the main ones.
So if I burn the ISO on a DVD or USB, stick it will provide the option to upgrade the 14.10 partition with 15.04?
I dont mind if it is a clean install as long as it is the same partition
I'll wait for the full release then.

---

