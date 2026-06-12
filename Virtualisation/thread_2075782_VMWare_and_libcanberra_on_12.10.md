---
title: "VMWare and libcanberra on 12.10"
date: 2012-10-24
forum: Virtualisation
---

### Post by bogdan_5844 on 2012-10-24
I am having a problem that I am not able to solve.

I have been trying to install the latest version of VMWare Player. I downloaded the bundle file from the site, and after a lot of patches and googling, I managed to get it to install. 

Right now, it starts but it fails to load a virtual machine. In terminal, it spews this error:

> Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory



Installing libcanberra-gtk-module only tells me that it's already installed. I have been searching on the internet for hours, and have tried editing the GTK_MODULES environment variable among other things, but to no avail. 

Can VMWare player run under Ubuntu 12.10 ? And if so, what do I have to do in order for it to load a virtual machine ?

---

### Post by chrmod on 2012-11-19
Have exactly the same problem. Once choosing the image to run, vmware-player silently crashes with no error in console. 

If you have any clues, please share.

Product Name         Product Version     
==================== ====================
vmware-player        5.0.1.894247

---

### Post by dcstar on 2012-11-22
> **bogdan_5844 said:**
> 
.......
Can VMWare player run under Ubuntu 12.10 ?

The current version can, the version you tried to use 4 weeks ago cannot.

---

### Post by dcstar on 2012-11-22
> **chrmod said:**
> Have exactly the same problem.
........

Not it is **not** on the information you have provided.

Unless you have the exact specific **libcanberra** error then you have a different problem so you should not hijack other threads. Start you own thread.

---

### Post by chrmod on 2012-11-22
You are right, my the problem was different (now I'm sure it was image specific).

Had solved error with libcanberra by adding own symlink in:
> /usr/lib/libcanberra-gtk-module.so -> 
/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.soand running `ldconfig` as root.

My setup is: 12.10 64bit, for 32bit you should probably symlink to:
> /usr/lib/i386-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so

---

