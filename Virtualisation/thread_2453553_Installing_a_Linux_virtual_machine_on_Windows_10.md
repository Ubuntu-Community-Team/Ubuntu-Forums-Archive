---
title: "Installing a Linux virtual machine on Windows 10"
date: 2020-11-12
forum: Virtualisation
---

### Post by garagon4279 on 2020-11-12
Hello everyone,

I am fairly new to Linux operating system and I am seeking help on how to install Linux on my Windows 10 machine without removing the Windows 10 OS. Is there a way to install Linux as a virtual machine that can be used while using Windows 10? As I said, I am new to Linux and all the help would be appreciated.

---

### Post by CelticWarrior on 2020-11-12
Welcome.

Yes, it can.
What help are you seeking exactly?

---

### Post by wildmanne39 on 2020-11-12
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by garagon4279 on 2020-11-13
Just a basic installation of Linux. Nothing too complicated. Thank you for replying to my post.

---

### Post by tea for one on 2020-11-13
Have you installed any Virtualisation software on your Windows 10 yet?

---

### Post by DuckHook on 2020-11-13
A decent step&#8209;by&#8209;step guide for installing VirtualBox on any of the three big OSes (Windows is the first section): [https://www.wikihow.com/Install-VirtualBox](https://www.wikihow.com/Install-VirtualBox)

If you are not using VBox, there may be other guides out there, but VBox is no cost (for personal use) and relatively "user friendly" for those familiar with Windows, so is a pretty good choice for newbies.

---

### Post by garagon4279 on 2020-11-13
No, I have not installed a virtualization software yet.

---

### Post by garagon4279 on 2020-11-13
Yes, I have heard the VBox is a good start for a virtualization machine. Thank you for the help, DuckHook.

---

### Post by SeijiSensei on 2020-11-14
Install [VirtualBox for Windows]("https://download.virtualbox.org/virtualbox/6.1.16/VirtualBox-6.1.16-140961-Win.exe") and the [Extension Pack]("https://download.virtualbox.org/virtualbox/6.1.16/Oracle_VM_VirtualBox_Extension_Pack-6.1.16.vbox-extpack"). Now download your choice of a [Linux]("http://cdimage.ubuntu.com/focal/daily-live/current/") [distribution]("http://cdimage.ubuntu.com/kubuntu/focal/daily-live/current/") [ISO]("http://cdimage.ubuntu.com/xubuntu/focal/daily-live/current/") and put it on your desktop. Open the VirtualBox Manager, click New, then follow the steps provided. Point to the ISO when asked for the installation medium. Accept all the defaults except for the size of the virtual drive and the amount of memory to allocate to the VM. For Linux VMs, I usually go with a virtual drive in the 20-40 GB range depending on how much free space you have on your drive and how much stuff you expect to put in your home directory. Try to allocate at least 2 GB of memory to the virtual machine.  If you're on a Windows machine with 4 GB total, I'd allocate 1.5 GB to the Linux VM and leave the rest for Windows. In this situation you should [create a swap file]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F") in Linux.

The VM is self-contained and cannot see the rest of your hard drive. If you need access to the Windows files, look into the Shared Folders option in VirtualBox. This lets you designate one or more directories as available to the VM.

---

