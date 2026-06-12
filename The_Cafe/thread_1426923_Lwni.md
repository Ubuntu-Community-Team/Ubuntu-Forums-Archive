---
title: "Lwni?"
date: 2010-03-10
forum: The Cafe
---

### Post by MasterNetra on 2010-03-10
Just curious as to why their isn't a Linux-based Windows Installer or Lwni, designed to install windows into Linux in a somewhat similar way as Wubi, now I get Wubi is built into Ubuntu. But couldn't their be something that sets it up so a virtual disk is setup, that can fake a windows install CD/DVD to load its setup files and have you restart the computer. It would load up but instead of jumping to the login screen, it first loads a menu with a option to continue to Ubuntu or choose the/a virtual partition, from which you could continue setting up windows then later just load into it? So that you can have both Linux and windows but have Linux as a host. Also unlike VMing it from within the actual OS, your system resources are being used solely on windows when your running it.

Just wondering.

---

### Post by themarker0 on 2010-03-10
Because microsoft would rather you only use Windows then using both.

---

### Post by juancarlospaco on 2010-03-10
***Ok, give me the Source Code of Windows, i will fix that, i promise.***

---

### Post by phrostbyte on 2010-03-10
Closed source :o

---

### Post by Giant Speck on 2010-03-11
Isn't Wubi tailored toward novice Linux users?  It seems far more likely to me that a user would be trying Linux for the first time after using Windows for years than trying Windows for the first time after using Linux for years.

Also, if you've already fully installed Linux before, why would you want to attempt a Wubi-like install of Windows?  If you've fully installed Linux, then chances are you know how to install an operating system from a disc.  Wouldn't installing Windows on a separate partition or in a virtual desktop be more favorable?

---

### Post by murderslastcrow on 2010-03-11
No, it'd be nicer for the times when someone forces you to use Windows software that doesn't work well in virtualization, but you're planning to get rid of it soon and don't wanna' recustomize your Ubuntu machine in the process.

However, since Microsoft has a free trial CD for XP on their website, why not a free .vdi/virtual disk as well so you don't have to set up a VirtualBox or Virtual Partition with Lwni, if this ever ends up being the case?

Oh, that's right, because Linux only exists if you're getting rid of it, in their eyes. Nevermind, we'll keep doing it the hard way.

Personally, I would never use anything but Virtualization for Windows programs. Even 1 GB of RAM can be enough for things like Photoshop or some light MMOs.

---

### Post by MasterNetra on 2010-03-11
I don't think you folks get what I'm saying I know the Wubi-like thing is not do-able 

on windows end at least not unless MS decides to do it themselves. 

Pretty much the Lwni would be completely from the Linux host. Granted I don't see 
avoiding VMing the installation up until the first reboot sense Windows needs to load up its installation files into the Virtual Partition. But afterwards you should be able to restart and load up Ubuntu to the Virtual Partition Selection Screen, which loads before the login. From there you can load into Window's Virtual Partition and continue setup. No windows source needed just VMing in a way similar to the Wubi layout. The VM image would rest in Ubuntu as one big fat file.

---

### Post by juancarlospaco on 2010-03-11
Wubi is not VM*ing*, Wubi install Linux on FAT/NTFS.

The VM images rest in Ubuntu as one big fat file on all mayor Virtualization software actually.

But still diferent from Wubi...

---

### Post by swoll1980 on 2010-03-11
Wouldn't the program require a Window's installation image? Good luck with MS allowing that to happen.

---

### Post by MasterNetra on 2010-03-11
> **juancarlospaco said:**
> Wubi is not VM*ing*, Wubi install Linux on FAT/NTFS.

The VM images rest in Ubuntu as one big fat file on all mayor Virtualization software actually.

But still diferent from Wubi...

I said Wubi-**LIKE** as in simliar in appearance, at least on surface anyway, underneath the hood they would be different. And I know VM files rest in Ubuntu and probably in all OS's as one big fat file my issue though is that running VMs as it is. Is not optimal in terms of resources. I mean your wasting what at least 150MB of ram running things that have little to nothing to do with the actual VM? Plus having to split your video card's resources. I mean what minus the GUI aspect of the VM the actual VM processes required eat about what a couple of MB's of ram?

> **swoll1980 said:**
> Wouldn't the program require a Window's installation image? Good luck with MS allowing that to happen.
Not if you own the CD/DVD.
I suppose what I'm essentially talking about is VMing outside all the unneeded processes of the Host and having only what is essential to run the vm.

---

