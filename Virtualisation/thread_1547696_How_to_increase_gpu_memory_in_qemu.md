---
title: "How to increase gpu memory in qemu"
date: 2010-08-07
forum: Virtualisation
---

### Post by nidzo732 on 2010-08-07
I've been using QEMU to try diferent operating systems , just for fun. But some systems reguire better graphics than the video cards offered in QEMU.I use a GUI called Aqemu , it offers folowing GPUs:
-StdVGA(vesa 2.0)
-cirrus clgd 5446
-vmware video card
Is any of theese better than default?Is there any way to scale video memory (just like in VirtualBox)? I have to use VirtualBox when i try a system that reqires better GPU, and VB is much slower then QEMU.

---

### Post by manzdagratiano on 2010-09-18
The command-line switches '-vga std' or '-vga cirrus' or '-vga vmware' provide the same options, so there is no need to use the GUI. I have the same problem too however - in high resolution mode using the switch -vga vmware on my Debian guest (resolution 1366x768), I observe a very sluggish performance of the video card. Is there a way to allocate more memory to the video card? The machine, and others as well, are lightning fast for text based operations or even for start-up/launching applications (indeed, qemu + kvm is awesome).

---

### Post by manzdagratiano on 2010-09-20
Any ideas people? I do believe that performance becomes better if I allocate a Gig of RAM to the VM instead of my usual 512, so I suspect that qemu probably chooses how to allocate memory to the graphics card. Pray do tell me if I can choose to do so myself, or if I may not. 'man qemu' has no far not provided me with the answer.

---

### Post by manzdagratiano on 2010-09-25
I beseech some of the Ubuntu gurus to speak to me here - is it possible or is it not?

---

### Post by Tankety on 2011-09-13
So a year later, I have the same issue and no one has found a way to do this.  There has to be a way.  Any type of help would be excellent.

---

### Post by bodhi.zazen on 2011-09-13
The best available graphics are provided by spice.

As of this post, spice is available for Fedora / Scientific linux and has not yet been fully ported to Debian or Ubuntu.

You can try the spice ppa, but I could not get spice working well last time I tried a month or so ago in Ubuntu.

---

### Post by Tankety on 2011-09-14
I found a way of increasing the gpu memory.  Mind you, I did this in Fedora 15 and have not tried it in Ubuntu.  Simply edit this file: "/etc/libvirt/qemu/HOSTNAME.xml"

There should be a line in there towards the bottom listing the GPU you are using and the ram allocated to it in bytes.  Change that number and you should be good to go.  I had to reboot to get it to display properly.  Your results may vary.

Thanks for your response bodhi and I will look into spice for my Fedora system.

---

