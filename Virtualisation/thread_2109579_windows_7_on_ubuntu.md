---
title: "windows 7 on ubuntu"
date: 2013-01-28
forum: Virtualisation
---

### Post by pctweak on 2013-01-28
simple questions to everyone who knows what to do...
i'm new in here so i don't ...

     can someone tell me how to install windows 7 on 
     ubuntu-12.04.1-desktop-amd64

the easy way...
vmware? 

-----------------------------------------------------------
what i'm really up to is install that ubuntu on freshly
formated HDD 250GB
then install windows 7 so i can (i think) have plug-n-play
ubuntu with windows 7 on it...

can i do that??

thanks in advance
Dan

---

### Post by heiko_s on 2013-01-28
I guess the easiest way would be VirtualBox. However, if you need more performance then Xen or KVM might be better. Perhaps also VMware, though I haven't tried it.

If you need good graphics performance, the choice narrows down to Xen and perhaps KVM, and only if using VGA passthrough which is anything but easy and also requires specific hardware.

If VirtualBox is not suitable, then you could go with either Xen or KVM and use virt-manager as a GUI. It's actually quite easy to use.

Xen has better documentation than KVM, though it can be daunting sometimes. VirtualBox has the best documentation of all. What do you use Win 7 for?

---

### Post by Udayan C on 2013-01-29
Hi! PCtweak...

I won't say that VMware is the easiest way as it requires a lot patches to be installed post installation of VMWare...there are some compatibility issues with VMWare..though once you install it.I am telling you ..you gonna love it...as far as VirtualBox is concern I would say I didn't really find it good for Windows 7 as it keeps crashing and you can't port virtual disk from one system to other....it will again crash...
I didn't tried any other suggested by heiko_s but now would love to try those after recommendation....

Hope you get the best out of it....!!! Best of luck!!! :)

---

### Post by Bucky Ball on 2013-01-29
Virtualbox, but the easy way is what suits you and how you work best. Remember, you are going to need decent specs and plenty of RAM (the OSs need to share it).

---

### Post by SeijiSensei on 2013-01-29
I have never experienced a Windows crash in VirtualBox, but I allocate 1.5 GB to the memory for a Windows 7 VM.  That still leaves 2.5/4 GB for Ubuntu on this machine, which is plenty.  Make sure you install the Extensions in the Windows VM as well.

I'm not sure what Udayan means by a "virtual disk," but you can create portable snapshots of VirtualBox VMs in a variety of formats including ones compatible with VMWare.

You'll want to make sure you have a swap area, too.

---

