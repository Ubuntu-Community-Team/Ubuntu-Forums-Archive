---
title: "which of these 2 ways is easier/better? VM or 2nd hard drive to run windows programs"
date: 2007-11-08
forum: Virtualisation
---

### Post by alize on 2007-11-08
im not even sure if one of these options is possible but let me know...

so there are a few programs I have/need to run sometimes, (photoshop, illustrator, and dreamweaver)

my first option would be to install a virtual machine (vmware or virtualbox etc) and install xp to run the programs that way...

OR

I have a few spare hard drives, is it possible to install a fresh copy of XP on my spare hard drive with my programs (photoshop, illustrator etc) and run them from that 2nd hard drive from Ubuntu? I know ubuntu can read the ntfs format but is there a way to be able to run the windows programs executable files that will be on the 2nd hard drive from within ubuntu?

Which way would be best/fastest/not bog down my system etc...

THANKS

---

### Post by Shazaam on 2007-11-08
The first thing you have to remember is that there is very little support ATM for 3d with virtualization programs. And, there are a large number of linux programs that either duplicate or come VERY close to duplicating the features of your favorite programs.
That aside, there are a number of ways to get to your favorite programs. First and foremost is a dual boot/dual drive setup. Run your programs natively with a normal install of Windows.
Second, some have had success with Wine. Others haven't.
Third, you can run a  Windows guest on top of linux.
Fourth, one that you might have some luck with, is to run linux as a guest on top of Windows.
Fifth, which is a little complicated but doable, is to use a program such as VMware Converter to convert a physical Windows install to a virtual machine.
Sixth, and MORE complicated , is to use a virtualization product to run a physical Windows/linux install (NOT a vm)  as a virtual guest.

There are many more, so you have a lot of choices. As far as speed and compatibility, native is the way to go.

---

### Post by alize on 2007-11-09
Thanks! 
just to clarify your respons. I don't want to do a dual boot on this drive but it is possible to run it from a second drive that windows is loaded onto correct?

---

### Post by jpkotta on 2007-11-09
> **alize said:**
> Thanks! 
just to clarify your respons. I don't want to do a dual boot on this drive but it is possible to run it from a second drive that windows is loaded onto correct?

No.  The only way to use that is to boot into Windows.  If you go the VM(ware) route, there is a tool to convert a physical Windows installation into a VM, but it is a conversion, not using the installation "in place".  If you go the Wine route, the same applies: you will have to have a separate Wine installation of your Windows software.  Personally, I would go with a VM.  As long as you don't need 3D acceleration, it will be the easiest and most robust option.

---

### Post by penguin steve on 2007-12-23
> **jpkotta said:**
> No.  The only way to use that is to boot into Windows.  If you go the VM(ware) route, there is a tool to convert a physical Windows installation into a VM, but it is a conversion, not using the installation "in place".

actually in my VMware Workstation 5.5 i can create a virtual machine that uses a physical disc rather than a virtual one in the advanced settings. this means you can run a windows install in a VM that is on a physical disc/partition. i'm thinking that you would have to install windows through the VM onto the physical disc because otherwise windows would write to the MBR and you would not be able to get into linux without reinstalling GRUB. i have never personally used this feature but i know its possible.

i hope this makes sense:)

---

