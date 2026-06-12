---
title: "VM aborts on switching to seamless"
date: 2013-07-10
forum: Virtualisation
---

### Post by jdwaugh on 2013-07-10
I am running Windows XP guest inside Virtualbox on a Ubuntu 13.04 host.  I installed the latest version from Oracle by adding the PPA.  I have installed the extensions pack and Guest Additions in Windows XP.  THe VM has 1 GB of memory available to it, the hardware has 8 GB of ram.  Full screen mode works fine, I can do everything inside the VM without an issue; however, if I switch to seamless mode, the machine aborts.  

I am just learning virtualbox so not sure about how to try running down the issue.  Google did not provide any recent answers that shed any light on the problem.  Some assistance is greatly appreciated.

---

### Post by gwm on 2013-07-11
Are you running with 3D turned on? Here is one of a series of links to other users who have their guest OS crash when changing to full screen.

[http://ubuntuforums.org/showthread.php?t=2160898]("http://ubuntuforums.org/showthread.php?t=2160898")

If you are running with 3D on, try turning it off as an experiment.

I would also recommend allocating more RAM to your VM. It definitely makes a difference to the performance of my guest (Windows 7).

---

### Post by jdwaugh on 2013-07-11
I turned off #D and it doesn't abort now, but the menu isn't visible and I can't do anythig in the guest OS.  THe perfomrance of the VM in Full screen or otherwise is good.  XP runs quite well with 512 MB, and I gae it double that.   I think the min is something like 124MB.  

Maybe I just use fullscreen, but I wish I could figure out what was going on.

---

