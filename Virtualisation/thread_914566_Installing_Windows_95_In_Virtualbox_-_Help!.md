---
title: "Installing Windows 95 In Virtualbox - Help!"
date: 2008-09-08
forum: Virtualisation
---

### Post by Bye1918 on 2008-09-08
So, I'm sitting here trying to install Windows 95 in VirtualBox. I've got it to the point where all I need to do is run the setup. But I can't figure out how!

See, Windows 95 didn't come on self booting cds. You needed to use a boot floppy. So I went and got my boot floppy, mounted it in VirtualBox, and booted everything up. But now I can't point that floppy to my CD image.

The says "A:\>" and I need to write "X:\setup.exe" where "X" is the letter of my CD drive. But I have no CD drive letters in Ubuntu! How the hell do I get this to work?

---

### Post by pytheas22 on 2008-09-09
When you mount the boot floppy in VirtualBox and boot your virtual machine, the virtual machine should boot to a DOS prompt.  From there, in the virtual machine window, you should be able to launch the Windows CD (which you should also have mounted in VirtualBox before starting the VM) by typing d:\setup.exe (or whatever; the letter assigned to the drive may not be d).  So you're not supposed to be running 'setup.exe' from a command-prompt in Ubuntu; you run it from within your virtual machine, which should be booted to DOS.

Are you not getting to a DOS prompt in your virtual machine?  If you're confused by all this, please post screenshots showing what exactly you do see in VirtualBox when you start your VM with the floppy disk mounted.  There are other ways to work around this (DOS boot-CD images) if necessary...

---

### Post by Bye1918 on 2008-09-09
I've got a DOS prompt. I'm trying to run setup through the virtualbox interface. But I can't figure out which letter virtualbox uses for it's virtual disk drives, so I can enter "X:\setup.exe" where "X" is the right letter. 

You say D? I'll try it out.

---

### Post by pytheas22 on 2008-09-09
VirtualBox doesn't assign the drive letters; it just creates virtual drives, and when DOS boots (from your floppy), it decides which letters will be associated with which drives.

You'd think there would be a DOS command to list all drives on the system, but unfortunately, Microsoft never foresaw the need to be able to figure out easily which drives have which letters.  So the only way to know is to guess.  Generally the first CD drive would be assigned D:\, though.  If not, you'll just have to work your way up through the alphabet...

---

### Post by NickCollide on 2009-06-28
I downloaded the w95 bootdisk images from allbootdisks.com - when i booted the virtual machine, i got the cd driver message just before the a: prompt. the drive letter is listed in the very last line before the prompt (mine was r:)

Good luck!

NC

---

