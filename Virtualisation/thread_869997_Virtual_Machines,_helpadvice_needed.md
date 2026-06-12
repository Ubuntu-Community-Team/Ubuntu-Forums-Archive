---
title: "Virtual Machines, help/advice needed"
date: 2008-07-25
forum: Virtualisation
---

### Post by davidpeace on 2008-07-25
I want to run a virtual machine on my Ubuntu desktop (8.04, amdx64). The machine would running the same Ubuntu that is on the hd. I want to do this so I can experiment and "play around" without breaking the OS and forcing me to reinstall everything on the original. I tried installing, via the Ubuntu repositories, virtualbox and once completed, it was as if the sound card and the video card ceased to exist. I rebooted and they were still "gone". I did a clean reinstall of Ubuntu and thinking the first time was a fluke, tried again with virtual box. Same thing. Another clean install later and I'm at an impasse. What are my best options for running Ubuntu on Ubuntu? And is there anything special I need to do to make it work?

---

### Post by overdrank on 2008-07-25
moved to  Virtualization. :)

---

### Post by NetworkGuy on 2008-07-25
> **davidpeace said:**
> I want to run a virtual machine on my Ubuntu desktop (8.04, amdx64). The machine would running the same Ubuntu that is on the hd. I want to do this so I can experiment and "play around" without breaking the OS and forcing me to reinstall everything on the original. I tried installing, via the Ubuntu repositories, virtualbox and once completed, it was as if the sound card and the video card ceased to exist. I rebooted and they were still "gone". I did a clean reinstall of Ubuntu and thinking the first time was a fluke, tried again with virtual box. Same thing. Another clean install later and I'm at an impasse. What are my best options for running Ubuntu on Ubuntu? And is there anything special I need to do to make it work?


Get the version of VirtualBox from Sun's WebSite (not the OSE version).   If you are trying to load the one from the repositories, it might be 32 bit only.  There is a 64 bit version on their site that also may fix your problem.   I'm using it without any issues.   Also the non OSE version will allow you to use USB devices after you apply the tweak that is floating around here somewhere.

---

### Post by davidpeace on 2008-07-25
Okay. Went through the installation and everything is fine. I try to load up the Ubuntu iso cd I have and I get this:

"This kernel requires an x86-64 CPU, but only detected an i1586 CPU. Unable to boot - please use a kernel appropriate for your CPU."

My machine is an AMD Turion 64x2, HP tx1320us

---

### Post by Donpablo on 2008-08-09
> **davidpeace said:**
> Okay. Went through the installation and everything is fine. I try to load up the Ubuntu iso cd I have and I get this:

"This kernel requires an x86-64 CPU, but only detected an i1586 CPU. Unable to boot - please use a kernel appropriate for your CPU."

My machine is an AMD Turion 64x2, HP tx1320us

I ran into the same issue trying to do the same thing, not 100% on this, but I think you can only install 32bit OS's as guests using Vbox.

---

