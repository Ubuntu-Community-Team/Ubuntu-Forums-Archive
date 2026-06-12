---
title: "One or more virtual hard disks, CD/DVD or floppy media are not currently accessible"
date: 2012-04-12
forum: Virtualisation
---

### Post by soniqck on 2012-04-12
after running avast anivirus for linux, it found a virus on mi virtual machine and I moved it to the chest but then the chest was empty and now my windows virtual machine can't open.

every time I run my windows7 virtual machine I have the following message
"One or more virtual hard disks, CD/DVD or floppy media are not currently accessible. As a result, you will not be able to operate virtual machines that use these media until they become accessible later".

Please advise.
:confused:

---

### Post by gareththered on 2012-04-13
The file your Anti-virus moved to the chest is your Windows 7 hard drive  image.  The error messages you are seeing is VirtualBox complaining  that it cannot find the drive image - which is correct as you've moved  it to the chest, or have you?  Did you press 'Delete' by mistake?

Why not search your host machine for all files that end in 'vhd' to see if it turns up?

Good luck

---

