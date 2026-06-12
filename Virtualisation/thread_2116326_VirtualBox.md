---
title: "VirtualBox"
date: 2013-02-15
forum: Virtualisation
---

### Post by jsampson45 on 2013-02-15
I am trying to install Ubuntu on the same computer as Windows 7 Home Premium
using VirtualBox. I have come to a message that the new installation is the only
operating system on the computer. This indicates that Windows 7 has not been
detected when it should have been. It offers to install the GRUB boot loader
to the master boot record. It will make Windows unbootable, though apparently
GRUB can be manually configured later to boot it. By an expert, yes, but dare
I continue with this installation? Why has it not detected Windows?

---

### Post by DuckHook on 2013-02-15
Must be absolutely clear here. If you are trying to install Ubuntu *inside* VirtualBox, then what you are doing is creating a sandboxed "virtual" machine inside your real machine (Windows 7). Since Ubuntu is fooled into thinking that this virtual machine is real, it is natural that it sees no other OS. Your Windows 7 install is invisible to it because it resides on a separate and unknown platform.

This is different from dual booting, which installs Ubuntu *alongside* your existing Win 7 as equal partners. If you were installing Ubuntu in a dual boot configuration, then it would be very concerning if the install does not detect Windows and your instinct to not proceed further would be accurate.

Good instinct, though. If in doubt, stop and ask. Whatever you do, firstly:

**BACKUP** **BACKUP** **BACKUP**

---

### Post by QIII on 2013-02-15
Remember that you have created a "virtual machine".  That means that, in most respects, the new OS will believe it is on an entirely independent "computer".  It will not generally understand, or even care, that it is installed on a Windows computer.  So it won't "see" your Windows OS.

VirtualBox provides a hardware abstracton layer that the guest OS assumes is its own machine.

If you are installing inside the VirtualBox GUI -- that is if where you see this message is inside VirtualBox -- then it will not keep Windows from loading.  Check the size of the disk you are installing to.  If you have created a virtual disk of, say, 50GB, and that is the size of the disk being used in the installation then you are OK.  If the size of the disk matches the size of your physical disk, then you are not installing in VirtualBox.

---

### Post by R3dW00t on 2013-02-15
If i understand correctly, you're trying to get a virtual pc going, running linux, right?

Can you list the steps you've taken up to the error message?
That way i can take a look at what went wrong.

(oops, seems i was a bit late with my reply.)

---

### Post by QIII on 2013-02-15
*Thread moved to **Virtualisation***

---

