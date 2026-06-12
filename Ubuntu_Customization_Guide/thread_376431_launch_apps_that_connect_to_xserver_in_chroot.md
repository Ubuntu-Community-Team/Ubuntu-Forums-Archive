---
title: "launch apps that connect to xserver in chroot"
date: 2007-03-04
forum: Ubuntu Customization Guide
---

### Post by marrabld on 2007-03-04
Hi,

I'm trying to customize Ubuntu edgy.  Is there a way of launching apps from chroot?

I tried doing xhost +h outside chroot, I got a message saying that X server would accept connections, but i still get the error cannot connect to X server: 0.0 when i try to launch anything eg gdmsetup

any one know how?

---

### Post by marrabld on 2007-03-05
OK I have given up on that approach.

What I am trying to do is change the default login on the customized live cd.  I tried launching gdmsetup in chroot but couldn't

I was under the impression that this was done in /etc/gdm/gdm.conf  when i change it  on my installed version of edgy, the user that i change to the default login to works fine..  but when I change it before I build the customized disc it changes back to the default setting after the build.

I read somewhere that on xubuntu that you need to change /etc/gdm/gdm-cdd.conf, however this file doesn't exist in ubuntu_edgy.  This leads me to assume that when i rebuild the file system, somewhere the squashfs (maybe?) is writing to the gdm.conf file as the file changes after the build.

Anyone got any ideas?  this is taking ages with the trial and error approach! :confused:

---

