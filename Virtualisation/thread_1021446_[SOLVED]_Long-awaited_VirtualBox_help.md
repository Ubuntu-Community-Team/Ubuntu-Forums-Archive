---
title: "[SOLVED] Long-awaited VirtualBox help"
date: 2008-12-25
forum: Virtualisation
---

### Post by Cadeyrn on 2008-12-25
I posted a topic about this problem a long time ago and no one ever replied, so I'm posting anew and fresh. I have a VirtualBox problem where during the Windows installation (through an .iso of my Windows disk), the installation couldn't format the virtual hard disk to NTFS. It would just automatically abort without shutting off or anything.

So when I got help I was told to use GParted to format a partition of the virtual drive, so I launched my VM with a GParted .iso. I tried auto-configuration *and* force VESA driver, but both result in this:

[ARGH](http://img387.imageshack.us/img387/3663/vboxbug2ew6.png)

What the crap do I do???

---

### Post by albinootje on 2008-12-25
> **Cadeyrn said:**
> I posted a topic about this problem a long time ago and no one ever replied, so I'm posting anew and fresh. I have a VirtualBox problem where during the Windows installation (through an .iso of my Windows disk), the installation couldn't format the virtual hard disk to NTFS. It would just automatically abort without shutting off or anything.

So when I got help I was told to use GParted to format a partition of the virtual drive, so I launched my VM with a GParted .iso. I tried auto-configuration *and* force VESA driver, but both result in this:


This is very strange.
Can you successfully run other installed VMs with VirtualBox ?

---

### Post by Cadeyrn on 2008-12-25
Apparently not. I just now tried emulating Ubuntu Intrepid (inside of Ubuntu Intrepid XD) and it did the same kind of crash right in the middle of loading the live CD preview.

(I mean the crash that happens when I format through the Windows installation, not launch GParted.)

---

### Post by bodhi.zazen on 2008-12-26
Just launch the Ubuntu iso and use gparted from there (no need for the gparted iso).

How much RAM did you give to the Guest ? And how much video RAM ?

---

### Post by Cadeyrn on 2008-12-26
I just tried launching Ubuntu. It crashed in mid-installation. And there's really no point, because VBox wouldn't let me use the same hard drive as my Windows installation.

Anyway, I gave more or less 256 MB RAM to each machine, and... Aha! That is probably the problem! The video memory (which I never changed from default) is only 8 MB! I set it to 60 and now I'll see what happens.

---

### Post by bodhi.zazen on 2008-12-26
You need more ram to each virtual machine ...

I suggest 512 mb

---

### Post by Cadeyrn on 2008-12-26
Alright, 80 made no difference, then I saw your post and... Strangely, VBox forced the max video RAM to be 128. I could go no higher.

But if 128 video MB gives the same result, maybe the problem is coming from something else?

---

### Post by albinootje on 2008-12-26
> **Cadeyrn said:**
> Alright, 80 made no difference, then I saw your post and... Strangely, VBox forced the max video RAM to be 128. I could go no higher.

But if 128 video MB gives the same result, maybe the problem is coming from something else?

I've *never* seen trouble installing MS-Windows as guest VM in VirtualBox with the default VirtualBox settings.
I think VirtualBox recommends 192 Mb of RAM for a Windows-2000 guest VM (or perhaps it was XP).

Are you using VirtualBox or the vboxgtk package ?

---

### Post by Cadeyrn on 2008-12-27
I downloaded the newest version from the official VirtualBox website and installed the thing from there...

---

### Post by albinootje on 2008-12-27
> **Cadeyrn said:**
> I downloaded the newest version from the official VirtualBox website and installed the thing from there...

Yesterday I tried wattOS in VirtualBox, and it got stuck while loading the GUI.
You should double-check your installation-cdrom to be sure it's not the cdrom which gives problems.

---

### Post by Cadeyrn on 2008-12-27
I don't see how it could be the disk--I installed Windows on this computer before switching to Ubuntu with it.

---

### Post by Cadeyrn on 2009-01-02
Well, I'm gonna mark this topic as solved because long story short, my Windows XP disk was needed for a friend's computer, and it totally crashed at the same spot every time.

It's a faulty disk. I have no idea what was wrong with the GParted iso, but it looks like I don't have to have an idea. I need to call Microsoft and get my install disk replaced.

---

