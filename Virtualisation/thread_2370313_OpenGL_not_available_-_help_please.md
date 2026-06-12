---
title: "OpenGL not available - help please"
date: 2017-09-02
forum: Virtualisation
---

### Post by salmirabile on 2017-09-02
Hi Everyone,
 
I've created a linux based VM in Azure which uses the Nvidia graphics cards and i've been trying to get openGL working on my ubuntu azure machine and simply can't get it to work. I've wasted 12hrs so far today and i'm tearing my hear out now. I've followed microsofts guide to the letter! [https://docs.microsoft.com/en-us/azure/virtual-machines/linux/n-series-driver-setup?toc=%2fazure%2fv...]("https://docs.microsoft.com/en-us/azure/virtual-machines/linux/n-series-driver-setup?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json")
 
I've read tons of posts in lots of forums, none of them of any help.
 
basically whenever i try and run glxinfo i get the error "couldn't find RGB GLX visual or fbconfig.
I can't run any openGL programs as it says that i don't have openGL.

I've uploaded my xorg log and i know there's a line in there stating "failed to initialize GLX extension (compatible nvidia x driver not found) but can't figure out why.
ive also blacklisted the nouveau drivers
 
I've also confirmed the drivers are installed correctly by running the "nvidia-smi" command
 
any help would be very much appreciated.
Sal

---

### Post by deadflowr on 2017-09-02
*Thread moved to **Virtualisation**.*

---

