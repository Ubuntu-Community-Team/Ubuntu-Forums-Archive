---
title: "[SOLVED] No windows in Virtual Box?"
date: 2008-11-14
forum: Virtualisation
---

### Post by johnhouk on 2008-11-14
OK day 2 with ubuntu.

Everytime i try to install windows in Virtual Box i get to the format portion. no mater which option i choose it freezes the computer at either %0 or %20.  Im thinking maybe theres a file size limit restricting the virtual drive size? 
I first tryed an expanding drive, then a fixed drive.
THIS IS MY PROBLEM^

im haveing to run Virtual Box with
sudo virtualbox
not sure why the installed "Item" dosn't work
or why my custom applicatoin launcher with this command wont work.

---

### Post by tarps87 on 2008-11-14
It is a very bad idea to run any programs with sudo without a real reason.
How did you install VirtualBox?
What happens when you type virtualbox into the terminal, without using sudo?

---

### Post by SIGTERMer on 2008-11-14
you can't run virtualbox from the menu because you don't have enough permissions. that's why you use sudo (root)

as for the freeze thing, check the disk size you allocated for windows

---

### Post by johnhouk on 2008-11-14
check [here]("http://ubuntuforums.org/showthread.php?p=6174964") for that info

---

### Post by tarps87 on 2008-11-14
virtualbox-ose-modules-2.6.24-21-generic should have installed the modules, when you first installed it how did you do that?
Any program that you run with sudo has read and write access to the system files on your computer which is why it is never a good idea to run programs with root privileges.
As you are running it from a terminal does it tell you what is happening in the terminal?
I haven't experienced this problem before but I also don't have to run it as root

---

### Post by bodhi.zazen on 2008-11-14
First, you should not run virtualbox as root. Add your user to the vboxusers group, log out, and back in (which it sounds like you have already done).

Second, an new disk is very much a raw disk and at times OS have difficulty recognizing it. Boot your windows installation with an Ubuntu ISO and use gparted or the command line to format the disk as NTFS. Then try re-installing windows.

---

### Post by johnhouk on 2008-11-14
I cant find a command line, or gparted in the menu of the bootable ubuntu disc

I have things such as
Install ubuntu
Check CD for Defects
Test Memory...

---

### Post by maybeway36 on 2008-11-14
Choose "try Ubuntu without installing," and then Ubuntu will boot in your VM. From there you can use GParted.

---

### Post by Carl Hamlin on 2008-11-14
> **johnhouk said:**
> OK day 2 with ubuntu.

Everytime i try to install windows in Virtual Box i get to the format portion. no mater which option i choose it freezes the computer at either %0 or %20.  Im thinking maybe theres a file size limit restricting the virtual drive size? 
I first tryed an expanding drive, then a fixed drive.
THIS IS MY PROBLEM^

im haveing to run Virtual Box with
sudo virtualbox
not sure why the installed "Item" dosn't work
or why my custom applicatoin launcher with this command wont work.

When I had this happen it was because I had assigned too much RAM to the instance. Bring it down to about 192MB and see if that changes anything for you.

---

### Post by johnhouk on 2008-11-14
No matter which of these selections i make, the emulator stops. The other situation made the whole OS freeze.
I wander if its because the virtual drive is still set to xp. let me check that out.

---

### Post by johnhouk on 2008-11-14
2 for 2, your the man Carl.







...Hey.. make that pirate sound.

---

### Post by Carl Hamlin on 2008-11-14
> **johnhouk said:**
> 2 for 2, your the man Carl.

Yarr. :D

---

