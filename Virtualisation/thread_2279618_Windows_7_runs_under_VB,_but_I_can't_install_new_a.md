---
title: "Windows 7 runs under VB, but I can't install new apps"
date: 2015-05-24
forum: Virtualisation
---

### Post by Tom_ZeCat on 2015-05-24
I hope you guys can help me to make heads or tails of this.  Windows 7 was working fine under VirtualBox (under Kubuntu 14.04/LTS).  However, now when I go to run it, I get this error message: 

> One or more virtual hard disks, CD/DVD ... disk image files are not currently accessible.  As a result, you will not be able to operate virtual machines that use thse files until they become accessible later.  

Please Check to open the Virtual Media Manager window and see which files are inaccessible, or press ignore  to ignore this message.  

When I press "check," I get this: 

[[img]http://s20.postimg.org/mx6fmc299/Virtual_Box_Prob.png[/img]](http://postimage.org/)
[upload an image](http://postimage.org/)

When I proceed anyway, Windows 7 loads just fine and I'm able to run any software I've already installed.  However, I cannot permanently install anything new.  If I install something, it works for that session, but when I close down Windows 7 and reboot into it, the newly installed software is gone.  There's plenty of room on my virtual hard drive, so I know that's not the problem.  Anyone know what's going on here and how I can fix it?

---

### Post by DuckHook on 2015-05-27
Are you, perhaps, opening an old snapshot every time you open your VM? Just a guess, but you may wish to start your troubleshooting with that.

Also, you appear to have a missing optical disk which is the source of the warning message. You can resynchronize your VM with your resource configuration by releasing this non-existent drive.

---

### Post by CharlesA on 2015-05-27
The snapshot is fine. You have an exclamation under the Optical Disks tab, so that is where your problem lies.

---

