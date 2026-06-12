---
title: "Installation using mini.iso for i386-16.04 freezes loading nic-firmware package"
date: 2016-07-17
forum: Virtualisation
---

### Post by geppetto on 2016-07-17
The creation of a VirtualBox Ubuntu image worked perfectly yesterday morning (July 16 2016). In the afternoon I repeated the process but the installation procedure stopped when trying to install the nic-firmware package: it simply stops at 26% of the installation process suggesting to change mirror. I've tried several mirrors, with no success. The problem persists today (July 17).

To reproduce the problem, download the 32bit 16.04 "minimal" installation iso, and proceed with the creation of the VirtualBox machine (i.e., create the empty vm, add a virtual disk, set the mini.iso as installation CD, run the installation). After setting locales and hostname, the installation starts downloading the packages; the initial downloads are successful, but the process pauses when the nic-firmware is reached, and after a delay the download is interrupted with a message suggesting to change mirror.

I suspect the package has been deleted or replaced.

Thank you

---

### Post by frank18 on 2016-07-17
Man go back to 14.04 that runs great,16.04 is a fluke and it wont run good for most people.Ubuntu decided to do changes but these changes were for the worse.

---

### Post by geppetto on 2016-07-18
Sorry Frank, I work for the future, not in the past. However, 14.04 installs fine (just (re)-tried) but it's not what I need. Thanks.

---

### Post by geppetto on 2016-07-21
No real solution till today, so it's time for a

*** WORKAROUND ***

What I want is a minimal VirtualBox image (cli+sshserver+locales) 16.04 i686 that can be easely reproducible and reliable: mini.iso is optimal, when it works. 

In that case my workaround has been to:

-) produce a 15.10 with desired (minimal) flavor using the 15.10 mini.iso 32bit, 
-) at the first boot run the command "do-release-upgrade" to obtain a 16.04
-) remove the old kernel package (4.2)
-) do other ordinary things like removing used archives, package lists, zeroing etc

and it works. The result (358Mb) is probably slightly sub-optimal compared with the native 16.04 mini.iso, but we are all confident that the problem will be finally solved and the native mini.iso will be usable by everybody. I'll keep watching for mini.iso (I used one with 04f as final md5sum code).

I do not feel like marking the thread as solved: the problem remains there.

---

### Post by howefield on 2016-07-21
Moved to the "*Virtualisation*" forum.

---

