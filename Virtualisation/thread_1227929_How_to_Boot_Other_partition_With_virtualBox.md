---
title: "How to Boot Other partition With virtualBox"
date: 2009-07-31
forum: Virtualisation
---

### Post by matessim on 2009-07-31
i heard its possible to load a different partition when you have a Dual boot using Virtual box, anyone mind telling me how to do it?

---

### Post by aesis05401 on 2009-07-31
> **matessim said:**
> i heard its possible to load a different partition when you have a Dual boot using Virtual box, anyone mind telling me how to do it?

Hello, 

You will get a better answer if we can clarify your terms a little.  Dual boot is when you make a decision at boot-up about what Operating System you want to use.  In a typical dual boot situation you only use one Operating System at a time.  Switching to the other OS requires rebooting the machine. 

VirtualBox can be used in several ways, but most commonly it is used to run another operating system inside your current OS.  So in this situation you would boot into Ubuntu every time you turn on the computer, then turn on VirtualBox from within Ubuntu when you wanted to access the other OS.  

Do you know which of these options you prefer?

---

### Post by matessim on 2009-07-31
i have a dual boot already.... but lately i heard some people talk about the ability to make some sort of P2V of another partition,while running the other OS with virtualbox.

---

### Post by aesis05401 on 2009-07-31
> **matessim said:**
> i have a dual boot already.... but lately i heard some people talk about the ability to make some sort of P2V of another partition,while running the other OS with virtualbox.

Yes, it is pretty straight forward. 

You do not need to worry about creating a new physical partition for the virtual machine so long as you have enough free space on your local hard drive.  Virtual Box has the tools needed to create virtual hard drives using free space from your current partitions.

Anyhow, the tools are relatively easy, so the best thing to do may be to download VirtualBox, open it, and let it walk you through an installation.

Please note: There are two free versions of VirtualBox.  The OSE version comes with source code, but does not have some features like USB support.  

The other free version does not come with source code, but you are allowed to use it for personal use without any license.  That version has additional functionality.

---

### Post by matessim on 2009-07-31
Sigh, i know VirtualBox, i don't want a new VM, i don't want to do P2V and get done with it, i want to have VirtualBox boot the other partition(i know its possible)
so i can keep a "live" copy in the dual boot, so if i need more horse power i can simply reboot and go into the windows, if not, host it as a guest in ubuntu

---

### Post by bodhi.zazen on 2009-07-31
Read the links posted in the Virtualization sticky at the top of these forums.

If you have questions post back.

booting a physical partition is, IMO, beta and it is better to convert your partition to a VM.

---

### Post by matessim on 2009-08-03
I found what i meant: [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

i read a little, i think your right bodhi, its quite... stringy, and it will break will make it unbootable normally from what i read, i guess ill have to come up with another solution

---

