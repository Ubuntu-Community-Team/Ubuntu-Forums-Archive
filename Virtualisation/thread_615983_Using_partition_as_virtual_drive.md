---
title: "Using partition as virtual drive"
date: 2007-11-17
forum: Virtualisation
---

### Post by DDRFreak21 on 2007-11-17
So I know that Parallels can run the partition of XP as a virtual machine within OSX, but is there a way to use my XP partition as a virtual disk in Virtualbox.

What I want is to have the same machine whether I reboot into XP or run Virtualbox.

---

### Post by x64Jimbo on 2007-11-17
You have to remember that Parallels is made by the same people that make the computer itself, and they have worked out all the kinks that are involved in moving a Windows OS from one set of "hardware" to another. Windows is designed to detect when it has been moved to a new hardware environment, and it will ask for reactivation when you boot it on new hardware. I believe Parallels is designed to emulate the exact same physical hardware of its host computer so that Windows does not realize that it is running virtually rather than physically. VirtualBox will not have this luxury because it's designed to run on any system configuration, and unlike Macs, PCs are completely diverse. Parallels only has to maintain a small database of devices that it must emulate, but with PCs, the permutations of hardware configurations are nearly endless. I'm afraid that the best solution for you would be to run just one operating system and virtualize the other. If you have to have Windows running natively on the computer, I suggest using the Windows version of VirtualBox for your Linux needs. 
Be advised that VirtualBox passes many hardware elements through to the guest operating system, including USB devices, so many of the reasons to keep Windows native have been taken away by VirtualBox.

---

