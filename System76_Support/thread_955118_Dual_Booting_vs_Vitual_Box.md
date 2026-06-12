---
title: "Dual Booting vs Vitual Box"
date: 2008-10-21
forum: System76 Support
---

### Post by Brickrat on 2008-10-21
I just purchased a Pangolin Core 2 dual P8400, 2.26 Ghz, with 2.0G RAM, running Ubuntu 8.04.   I have long followed linux and have played with it several times, but found I didn't have time to do everything from the console (after learning what needed to be done) and so only made the leap after installing Ubuntu on my daughter's ACER, which wouldn't work on Vista, and seeing it was pretty easy to install and use.  I have been using Open Office for business and personal for 3 years, and so I am confident I can live in a non-MS world, except for a couple programs I use in my work, mainly ACT! and TurboCAD.  (hopefully I can find replacements for them also) 

I was going to set up a dual boot, but in reading the forums and FAQ's several people mentioned VirtualBox and I would like to give it a try.  However, I tried to load it from S76's synaptic package manager, and it appeared to load, except when I tried to start it after setting up a Windows VM.  It said that the driver was not loaded.  

Researching further I went to VirtualBox.org and downloaded the i386 version for Ubuntu Hardy Heron and it started to load until it gave me a error for improper processor. After two strikes and looking at the VB forums, I'm not so sure now. 

Questions:  
1-   Anyone with experience on running ACT! or TurboCAD on VitualBox? 
2 -  Is the problem loading VB that the Dual Core P8400 is not supported yet?  or did I do something wrong? 
3 -  Is there a better solution than Virtualbox? 
4 -  Any tips on setting up dual boot?  What is the best tutuorial to use? 

I apologize for not logging the error messages, as always it was late at night when I was doing it.  

I'd really like to prove to my doubting friends that Linux is the future. 

Thanks

Brickrat
Kansas City, MO

---

### Post by patrickballeux on 2008-10-21
I am using VirtualBox from the repositories...

If I'm not mistaken, you haven't installed/loaded the kernel module for virtual box.   Remove the from from Virtualbox.org, and reinstall the one from the repositories.

Also, install the "virtualbox-ose-modules-generic".  This is the module that is missing by default.  I just don't know why is it not loaded by default...  Anyway...

Then, once installed, in a terminal, execuce "sudo modprobe vboxdrv".  And if I remember well, you have to be part of the vboxdrv group...

Then all should go well.

To have the module loaded at boot time, run this:

sudo echo vboxdrv >> /etc/modules

Good luck!

---

