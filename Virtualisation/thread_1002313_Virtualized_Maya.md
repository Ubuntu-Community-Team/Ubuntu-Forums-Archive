---
title: "Virtualized Maya"
date: 2008-12-04
forum: Virtualisation
---

### Post by Neon612 on 2008-12-04
I'd like to know how well Maya 8.5 will work on a vmware (XP) installation inside of Ubuntu (hardy)?

The main reason is because I've tried the linux version of Maya, it worked great, my only problems were that it would not export AVI's and the weird problem with the mouse pointer changing shape, but outside of that there was not problem. Until I received a shelf error and tried to reinstall it, which no matter what I tried I still could not get rid of that shelf error. But now that I've updated my system -- the hard way, complete overinstall, wiping my gutsy -- I'm thinking that there was a folder somewhere where all of the project files were placed along with the items in the shelves, so I probably just had to do something with the folder and my problem would have been solved. Oh well, they always say hindsight is 20/20.

But, to forgo this problem again I'd like to try and install maya inside of a vmwared XP install and try my luck.

---

### Post by Thelasko on 2008-12-05
Your biggest problem with be 3d graphics hardware support.  I hear the latest version of VMWare has it, but it's not fully supported.

---

### Post by Neon612 on 2008-12-05
Well my Graphics card is a knockoff ATi. Its a VisionTek Radeon HD 2400 Pro. I'm not sure what the memory or other stats are.

And I read somewhere that the guest OS depends on the hardware minus what the host OS uses. So my specs are as follows:
AMD 2GHz chip
2GB DDR/2 Memory (not sure which type)

---

### Post by Neon612 on 2008-12-06
IS there some command I can run that will display everything in my comp that will help you guys?

---

### Post by indigo42 on 2009-08-15
All,
I was running Maya 2008 on VMWare in a Fedora8 guest OS as recommended by Autodesk (well they didn't recommend the VMWare part)

I have recently installed directly on Kubuntu 9.04...it is much faster. Here are a few reasons why.

[LIST]
[*]VMware virtualizes your card so things like "High quality rendering" will never work, as Maya is not looking at your 'real' card through VMware.
[*]You will be stuck at Direct X version 9. something.
[*]VMware only allows you to have 128MB of texture ram.
[*]I tested glxgears in VMware and natively..native had 10x the frame rate!
[/LIST]
Maya seemed to be built to run in a pure KDE environment. I installed the Kubuntu desktop and boot with that when I want to work in Maya.

---

### Post by gobberpooper on 2009-08-26
It's pretty slow. It works fine but the right click menu just doesn't work.

---

