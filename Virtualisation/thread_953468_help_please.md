---
title: "help please"
date: 2008-10-20
forum: Virtualisation
---

### Post by chemicall on 2008-10-20
trying to use virtualbox, so i can run solaris within ubuntu.

the virtualbox OSE opens, when im about to instal the image, I get this:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
What can I do to correct this? thanks I dont see the package i need in package manager, where can I find it?

---

### Post by meho_r on 2008-10-20
Version? VirtualBox 2?

If it's VB 1.5.6 that is located in Ubuntu repos, then you should see virtualbox-ose-modules-generic or something like that. As I remember, you should belong to user group named "vboxusers" to use VB.

---

### Post by chemicall on 2008-10-20
Thanks pal, got it!

---

### Post by meho_r on 2008-10-20
Why not try the new version, there've been some nice improvement (i.e. now you can install 64bit Linux as guest :)).

I installed from repo listed [here]("http://www.virtualbox.org/wiki/Linux_Downloads") and works fine. Just in case you'd want to give it a try ;)

---

### Post by chemicall on 2008-10-20
cool, i'll have to give that one a go on my 64bit box. thanks for the hint.

---

### Post by chemicall on 2008-10-20
well, virtualbox is running, but it buggered my video in X, its a IBM G41 laptop, I am only getting 800x600 now. any ideas?

---

### Post by chemicall on 2008-10-21
well, the sound was gone too, did some updates and a couple reboots and all is back to normal - and virtualbox is still functioning :)

thanks for the info folks :guitar:

---

### Post by Thelasko on 2008-10-21
> **chemicall said:**
> well, virtualbox is running, but it buggered my video in X, its a IBM G41 laptop, I am only getting 800x600 now. any ideas?

Opensolaris is a bit tricky.  [Here's a guide.]("http://blogs.sun.com/fatbloke/entry/installing_opensolaris_2008_05_as")  Hope you have a powerful computer.:)

---

