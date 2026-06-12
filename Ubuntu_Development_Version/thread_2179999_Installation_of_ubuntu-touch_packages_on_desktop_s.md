---
title: "Installation of ubuntu-touch packages on desktop systems causes problems"
date: 2013-10-10
forum: Ubuntu Development Version
---

### Post by bpow on 2013-10-10
I'm not even sure that it is intended that these packages would be installable on a desktop system, but there is nothing in the .deb files that prevents them from being installed. So, I notice some touch-related packages (and I have a laptop with touchscreen) and I try to install things like 'ubuntu-touch' and 'ubuntu-touch-session' on the laptop and havoc ensues...

As described in bug 1237160 ( [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools-ubuntu-touch/+bug/1237160](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools-ubuntu-touch/+bug/1237160) ), installing 'ubuntu-touch' pulls in 'initramfs-tools-ubuntu-touch', which contains a script that causes error in update-initramfs because of missing files (so future kernel updates fail).

Also, installation of 'ubuntu-touch-session' (see bug 1238151,  [https://bugs.launchpad.net/ubuntu/+source/ubuntu-touch-session/+bug/1238151](https://bugs.launchpad.net/ubuntu/+source/ubuntu-touch-session/+bug/1238151) ) leads to a session that cannot actually be started, but since .dmrc recalls it as the previous session, also prevents the normal ubuntu session from being started after the 'ubuntu touch' session had been selected in lightdm.

I'm just pointing this out in the forums in case someone else runs into this. I think if/until ubuntu-touch is actually usable on non-tablets/non-phones, the packages should not be installable on these systems. At the least, installing them shouldn't break an otherwise working system.

---

