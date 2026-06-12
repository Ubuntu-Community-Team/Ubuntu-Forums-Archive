---
title: "[SOLVED] VMWare 3D Acceleration Needed"
date: 2008-02-25
forum: Virtualisation
---

### Post by scrop on 2008-02-25
I've been following the instructions in the manual for enabling acceleration. I've added this to the vmx file of a non-running vm.

mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"

when I start the vm, vmware immediately flips that mks.enable3d setting back to FALSE.
I can't find any error in the logs or information about this. Can someone please help?

Latest Gutsy in use
Latest NVIDIA driver in use (desktop is accelerated, no trouble here)
GeForce 8600 GT

Guest OS is WinXP w/ VMWare Tools installed. From watching the log file, it looks like VMWare toggles this setting to false on me before the Guest OS ever starts.

---

### Post by HermanAB on 2008-02-25
There is no 3D accelleration.

---

### Post by scrop on 2008-02-25
There is, enabled via DirectX 8.1 if your guest os is Windows 2000 or Windows XP

[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)

---

### Post by HermanAB on 2008-02-25
Pardon yes - though you also need VMware Workstation.

---

### Post by scrop on 2008-02-25
This is all under VMWare workstation 6.0, sorry I left that out.

---

### Post by OmegaBLK on 2008-02-25
Never encountered this problem so I can't really help.

Check here to make sure everything is correct (above link was for WS 5.0 this one is for your version of 6.0):
[http://pubs.vmware.com/ws6_ace2/ws/ws_vidsound_d3d_enabling_guestos.html](http://pubs.vmware.com/ws6_ace2/ws/ws_vidsound_d3d_enabling_guestos.html)

If there are still problems you may want to ask this question in the [VMware forums](http://communities.vmware.com/index.jspa) if you cannot receive an answer here.

> 
Pardon yes - though you also need VMware Workstation.


VMware Player 2.0 also has Direct3D support for Windows XP and 2000 guests only.

---

### Post by scrop on 2008-02-28
The VMWare forums have been having some issues for a few days. Users can't login w/o being taken to the registration screen in an endless loop. I even called them and they had the same issue on their end.

Anyway, after experimentation, I found that VMWare will silently disable 3d support if you don't specify this parameter correctly.

svga.vramSize = "67108864"

If this works out to be anything other than the exact size of the memory your graphics card has then w/o warning or errors being logged you just get reverted to no 3d. 

How about a round of applause for that user experience? :)

---

