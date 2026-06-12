---
title: "Dual Windows / Ubuntu system with Virtualbox access between partitions?"
date: 2011-07-05
forum: Virtualisation
---

### Post by slowtrain on 2011-07-05
I'm thinking of setting up my new computer as follows:  separate partitions for Windows and Linux, so each can be run independently, but also setting up Virtualbox in each OS so the other one can be run from it (Virtualbox would need to be set up to use a hard disk partition rather than virtual disk).  I'm wondering whether this is a feasible and not too problematic setup and how to bring it about.

Does anyone have a setup like this?  Any issues or problems?  What happens with the raw disk access when Virtualbox is upgraded (Oracle is releasing once a month it seems)?

I'm starting with a computer that will have Windows installed on it, so am wondering how to get to the above configuration.  I guess gparted on a flash drive would allow me to create the disk partition--hopefully w/o erasing any of the Windows partition?  Am a bit worried because last time I used gparted, it left overlap between the partitions.  Not sure how I get the dual boot starting with Windows.  I have set up dual boot, but only from within Ubuntu.  As for mapping the Ubuntu partition to VBox, I've seen some instructions online--hope they're still accurate.

---

### Post by maxim_86ualb2 on 2011-07-06
I think you will not be able to get the same installation of windows to both run in the VM and on the actual machine.

---

### Post by slowtrain on 2011-07-06
Thanks maxim_86ualb2!  I guess there's some type of copy protection involved on the windows side?

---

### Post by lmarmisa on 2011-07-07
I have a similar installation to yours with a Ubuntu 10.10 / XP Pro dual boot system. I have installed VirtualBox in each OS.

I defined a virtual machine in XP storing the virtual disk file (vdi) inside the NTFS partition. Then I defined a second VM in the Ubuntu VirtualBox program using the same virtual disk stored in the NTFS partition.

The result is good. I can run the same VB virtual machine (really the same virtual disk) from both operating systems.

Anyway I impose to myself some limitations. I am not using the disk snapshot feature of VirtualBox and I am not saving the virtual machine status. The context of these two options is not saved inside the virtual disk (file vdi) and this saved context is not available for the VirtualBox program running in the other OS. Therefore, I select always the shutdown option on the shared virtual machine. If you follow this recommendation, you will have no problem with this shared virtual disk.

---

### Post by slowtrain on 2011-07-14
Hi lmarmisa:  Thanks for the words of encouragement!  I kind of figured that snapshots and states would be out on this setup.  I'm actually planning on doing something a bit more radical:  I'd have a windows and a Ubuntu partition on my real hard disk and possibly a third data partition.  Then, I'd use VB in Windows to run Ubuntu off the *real disk* Ubuntu partition and vice versa for VB in Ubuntu.  I've found some instructions online for making VB treat a real partition as its hard disk.  I hope those instructions work and w/o causing too many problems!

slowtrain

---

