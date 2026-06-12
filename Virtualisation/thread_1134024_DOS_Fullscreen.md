---
title: "DOS Fullscreen"
date: 2009-04-23
forum: Virtualisation
---

### Post by RealG187 on 2009-04-23
Is there a way to make DOS full screen? When I run a VM and go full screen it shows the center of the screen with a border. Can I make it fill the whole screen, like if I actually was in Windows I could make it full screen.

I have a few DOS games I would like to play and it's annoying when they are in a window.

---

### Post by Xepra on 2009-04-24
Exactly what I just started messing with.

Try:  sudo apt-get install vboxgtk

Then open Applications->System Tools->VBoxGTK

It is similar to the GUI that comes with VirtualBox, and should recognize and start your existing VirtualBox VMs.

The fullscreen mode, conveniently, stretches the image to the full screen :)



Unforunately there is no file menu on a running vm in VBoxGTK.  This is a problem because a less than tech savvy client of mine needs to be able to both run full screen and dynamically mount floppies...

There appears to be some custom VESA settings you can use with the standard VirtualBox gui, but I haven't played with them yet.

It would be very nice if the standard gui had a stretch to fullscreen option like the VBoxGTK does.

---

### Post by RealG187 on 2009-04-24
I have Virtual Box OSE, is that the same. All my VMs are in VMWare, is there a way to migrate them if need be?

The first time I used Virtual Box was in Windows Vista running Ubuntu, but Ubuntu didn't install. I have't used it since. Well I installed it and ran a live CD once, but hopeully everything is fixed now...

---

### Post by Xepra on 2009-04-27
VBoxGTK is just a different front end for VirtualBox, so it shouldn't matter what version you have installed.

And for VMWare to VirtualBox try:

[https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool#Converting%20your%20existing%20.vmdk%20Virtual%20Disc%20Image%20To%20a%20.vdi%20File](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool#Converting%20your%20existing%20.vmdk%20Virtual%20Disc%20Image%20To%20a%20.vdi%20File)

---

### Post by RealG187 on 2009-04-28
What do you mean by a diffent front end? Can I still go full screen using normal virtual box? (cuz I have only tried VMWare and DOSBox, as I said I never really "liked" virtual box because of that expereince, but I should give it another try)

---

