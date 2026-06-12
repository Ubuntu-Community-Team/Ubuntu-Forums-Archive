---
title: "What virtual management system should I use?"
date: 2008-02-09
forum: Virtualisation
---

### Post by kcav45 on 2008-02-09
I want to create virtual  environments where I can play with Windows XP Professional and Windows XP Professional 64-bit.  I downloaded Ubuntu 7.1, and I have a notebook computer available that has an Intel, Pentium M processor, speed 2MHz, and 2GB of RAM.  It is essential that speech recognition applications be performed inside the virtual environments using the sound system on the host.  The host has a Polycom Communicator, model S100 (speaker/microphone) attached to the USB port.

Which virtual management system should I use?  I was going to use VMware Workstaion, then I found out VMware server is free. I notice people are using Virtual box.  What  system should I use?

:confused:

KC

---

### Post by kyphi on 2008-02-10
VirtualBox is the only virtualisation programme I have ever used.  I have noticed occasional echo effects in sound reproduction in the guest system but cannot advise on how this would affect voice recognition.

Why not run your voice recognition in native Linux mode?  Our EeePC running Xandros Linux has voice recognition.  Have a look in Synaptic.

Although there has been some progress regarding USB access in VirtualBox this seems to be version dependent but should be OK for 7.10 (there is no version 7.1).

Running XP 32 bit in VirtualBox works fine - I do not know if 64 bit will work.

I assume that your processor size is 2 GB rather than 2 MB.

All you can do is try VirtualBox.  It works for me.

Good Luck.

---

