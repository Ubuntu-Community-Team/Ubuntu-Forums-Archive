---
title: "Installing a guest in VirtualBox causing system to lock up"
date: 2009-05-06
forum: Virtualisation
---

### Post by CloudFX on 2009-05-06
I have VirtualBox-2.2 installed on a fresh Jaunty install.  The VirtualBox installation is the non-free one from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).  When I attempt to install a VM using a CD, my system completely locks up, resolvable only with a forced shut down.  I have tried this with both a Ubuntu 9.04 CD (the same one I used to install my current system with) and a Windows XP CD.  Both fail, with the same result.  I have also completely reinstalled Ubuntu 9.04 and tried it, with the same result.  This did not happen with Intrepid.  Does anybody have any clues as to what is causing this?

---

### Post by Wolfhere on 2009-09-18
I am getting the same thing. I want to switch from VMware, seeing as how VirtualBox is open-source. I am at a loss

---

### Post by skatinjj on 2009-09-18
Can you two post your system specs please?

---

### Post by Shazaam on 2009-09-20
And post how much physical memory you are allocating to the virtual machine(s). You shouldn't allocate more than half of your physical memory to a virtual machine; especially if your ram is shared with the video card (like in a laptop). If you do it can lead to host system sluggishness and lockups.
Also, if your cursor/keyboard is captured on a locked up virtual machine the host will act as if it is frozen. Before you hit that reset or power button try the magic SysRc keys or try to get to a prompt (Alt+F1/F2).
Magic keys=
Hold down your Ctrl+Alt+SysRq keys and type in reisub

---

### Post by scrooge_74 on 2009-09-22
Another good idea is to download latest version from virtualbox.org they are at version 3 there, and it works pretty well

---

