---
title: "Move from VM to physical partition"
date: 2008-12-01
forum: Virtualisation
---

### Post by KhipuX on 2008-12-01
Hello Folks

I've set up a fairly specialised system as a virtual machine on Virtualbox for testing and now I would like to shift this system from being a VM to a real system on a physical partition for booting up. The VM is based on Linux too.

Do I just transfer all the filing system from the virtual hard drive to the new partition _in the same way I would move a normal linux installation from physical to physical partition,_ or is there another way of doing this?

I did wonder about making a partition backup from the VM and then just restoring to a physical partition.

Any advice appreciated.

---

### Post by bodhi.zazen on 2008-12-01
Easiest way is to mount your physical partition in VBox , then use dd to copy the Virtual Machine to the Physical partition.

You will probably need to update GRUB and /etc/fstab

---

### Post by KhipuX on 2008-12-12
Woohoo, that worked, thank you!

---

### Post by El_Belgicano on 2008-12-12
I'm planning of doing the same as you are to update from Gutsy to Intrepid ... With that idea in mind, I already informed, and it's been told me to tar the virtual distro, install the minimal system on the physical partition where you want it to be and untar the whole thing in your newly created "/".
Not tried myself, but since I already did two recoveries of my full system using tar, I tend to trust it...

---

