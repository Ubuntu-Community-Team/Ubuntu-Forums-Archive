---
title: "Uninstall xwindows"
date: 2009-12-08
forum: Server Platforms
---

### Post by dnr101 on 2009-12-08
Hey all, I just installed vim-full by accident on my server (8.04 LTS), and that brought xwindows with it.. How can I remove all the xwindows stuff? I used aptitude to install vim-full, so I tried
```
sudo aptitude remove vim-full
```
hoping that would do it, but no dice...
Help greatly appreciated.
-Dave

---

### Post by sikander3786 on 2009-12-08
```
sudo apt-get remove vim-full
```

that should remove vim-full. Or try removing from Synaptic Package Manager.

---

### Post by dnr101 on 2009-12-08
Sorry, it's not that I want to remove vim-full, I want to remove all vestiges of xwindows from my server (one of the reasons I used Ubuntu server when I built my system, instead of say Centos...)

---

### Post by dnr101 on 2009-12-10
Bump... please?

---

### Post by joes7 on 2009-12-10
Try by restoring your PC to a previous restoring point or by using "Recovery Mode",

---

### Post by dnr101 on 2009-12-10
No good, I don't have any restore points and I don't have easy physical access to the system. I was really hoping for a simple aptitude based solution. Thanks for the try though, maybe I should clarify that the machine is a production web server running pretty much just apache and ssh. Does anyone know what x11 packages are in the default 8.04 LTS Server install (or where I could find that info..)
Thanks,
-D

---

