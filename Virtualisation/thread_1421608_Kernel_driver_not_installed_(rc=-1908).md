---
title: "Kernel driver not installed (rc=-1908)"
date: 2010-03-04
forum: Virtualisation
---

### Post by gambothell on 2010-03-04
Ubuntu 9.10, Virtualbox 3.1 Puel, guest Windows XP

I had this problem before after installing virtualbox and searching the forums I followed instructions and ran /etc/init.d/vboxdrv.dpkg-bak setup to fix the problem. I also had to copy the vboxdrv.dpkg-bak to the init.d folder and name it vboxdrv. Everything was fine until today when I did an Ubuntu update which included new headers.

Now I get the "Kernel driver not installed (rc=-1908) error again. But this time when I try to rebuild by doing a sudo /etc/init.d/vboxdrv.dpkg-bak setup I get the error "command not found".

I guess I have to reinstall virtualbox again...:frown:

Any suggestions on what to do so I don't have to go through this with each kernel update?

Thanks for your assistance

---

### Post by gambothell on 2010-03-04
I rebooted and tried to run the setup again. The log follows:

Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.1.4

------------------------------
Deleting module version: 3.1.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.1.4/source ->
                 /usr/src/vboxdrv-3.1.4

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.31-20-generic-pae cannot be found at
/lib/modules/2.6.31-20-generic-pae/build or /lib/modules/2.6.31-20-generic-pae/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.


Hope this helps, any suggestions?

---

### Post by gambothell on 2010-03-05
Well, I decided to re-install Ubuntu. When I installed virtualbox, it now works normally. The only conclusion I can come up with is that virtualbox did not compile the headers properly originally or that I somehow removed some critical file. 

This was not lost time, because I wanted to revert to EXT3 instead of EXT4 because Acronis currently does not support EXT4.

---

