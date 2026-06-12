---
title: "VMware Player 3.1 - How to make it &quot;fit to full screen&quot;?"
date: 2010-08-05
forum: Virtualisation
---

### Post by indstr on 2010-08-05
Does anyone know how to make VMware player fit to full screen even when the resolution is different than the host's? I've got Windows XP installed on it to play some older games at 640x480 (most of which run surprisingly well), but unfortunately when the resolution of Windows is not the same as Ubuntu, I get a tiny Windows in the middle of the screen, with a huge black border around it. 
 
I have not been able to find anything in the VMware menus to "fit to full screen". The closest is something like "automatically resize guest to host", but when I manually change the res on the guest, it still has the borders. 
 
I have also tried just manually changing the Ubuntu resolution to 640x480 before I run VMWare, but unfortunately the VMware window goes out of the viewable screen area (even in full screen). My best solution so far has been to switch Ubuntu to 800x600, lock VMware at 640x480, and then use the "zoom" function on my monitor to make it *almost* full screen. Of course, this is less than optimal. :smile: 
 
(FYI I am running Xubuntu Studio 9.10, with some nvidia binary drivers installed.. I forget which version)
 
I have tried a couple of solutions, such as the one suggested here:  
[http://communities.vmware.com/thread/204564](http://communities.vmware.com/thread/204564)   
(pref.autoFitFullScreen = "fitHostToGuest")... With not much luck. I even tried uninstalling VMware tools. Still didn't work.
 
If I need up add a line in some config files, does anybody know specifically which files it needs to be added to?
 
Any suggestions would be appreciated.

---

### Post by fjgaude on 2010-08-05
You can't just click a corner and drag it to full screen?

---

### Post by indstr on 2010-08-05
> **fjgaude said:**
> You can't just click a corner and drag it to full screen?
 
Maybe I didn't really explain it well enough?
 
Full screen mode works just fine. I am using it. But when the virtual machine's resolution is lower than Ubuntu's, it puts a huge black border around the screen. So for example, my native Ubuntu resolution, I usually run 1024x768. Windows XP in the VM, I am wanting to usually run at 640x480.... So even in "full screen" mode in VMware, the Windows XP only takes up a small space in the middle of the screen. 
 
What I think I need to do is make the "Host fit to Guest". 
 
This morning I tried editing the ~/.vmware/preferences file and adding ```
pref.autoFitFullScreen = "fitHostToGuest"
``` , but it still didn't work.
 
"Guest fit to host" works just fine.. For example it can automatically resize Windows XP up to Ubuntu's 1024... But I can't get it to work the other way around... Even when I disable "guest fit to host" in the VMware settings and force the monitor's max res to 640x480 :(

---

### Post by fjgaude on 2010-08-05
I think I understadn but have never wished to do what you want. I have nothing to suggest to get to where you wish to go.

---

