---
title: "Unable to resize screen in Vitrual Box with Ubuntu server on it"
date: 2011-02-15
forum: Virtualisation
---

### Post by quigzinator on 2011-02-15
Hello,

I have a laptop with Windows 7 installed on it, which I then put virtual box with Ubuntu Server and Ubuntu Desktop running in it. At first the screen size in both virtualizations where at 800x600 the desktop handled the change to a larger resolution using the guest add-ons; I followed a few examples on the internet of people resizing the screen via command line, but once I rebooted I still had the 800x600. 

I mounted the cd then ran the script on the CD both the autorun and the VboxLinuxAdditions.run .  Durring Start up I can see the module for the Add-ons loading but the screen still has the same size on the command prompt. 

Any help is appriecated.

---

### Post by mciverza on 2011-02-16
The ubuntu server isn't running the graphical system "X" (unless you've manually installed it).
The VirtualBox addons only affect screen resizing when X is running. 

If you install the "ubuntu-desktop" metapackage you will get a normal ubuntu-like graphical interface, which, after running the VirtualBox Addons Autorun, will be resizable.

---

### Post by quigzinator on 2011-02-17
so you are saying that there is no way to resize the viewable command line interface unless Xorg is running?  Is there perhaps a way to make the font smaller on the command line interface so more is viewable at the smaller resolution? I know resizing the CLI is possible when a distro is installed on the harddrive, my friend did it for me once but i was hoping this was possible in virtualbox, i haven't seen any info on this so far. Thanks for the reply mciverza.

---

