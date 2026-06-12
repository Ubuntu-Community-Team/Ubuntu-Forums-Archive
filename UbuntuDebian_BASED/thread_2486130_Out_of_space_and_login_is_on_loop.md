---
title: "Out of space and login is on loop"
date: 2023-04-20
forum: Ubuntu/Debian BASED
---

### Post by robynlep on 2023-04-20
I am running Linux 1.2023.1.0 on VirtualBox on my Windows computer. I ran out of space and tried to add disk space under settings in VirtualBox, but I do not know how to partition it. I have watched a few videos on how to do it using the Windows terminal, but it never works. Now I can't even log in to Linux. The login page is stuck in a loop. When I sign in, it doesn't load. It just refreshes the login page. I have tried Ctl-Alt-F12 and F11 on the login page, and that doesn't do anything. Any advice is appreciated. TIA!

---

### Post by TheFu on 2023-04-20
No clue what "Linux 1.2023.1.0" is.  That's not a valid Ubuntu release.  

Someone new to Linux should install Ubuntu 22.04 - pick a flavor of desktop that you like - Gnome/KDE won't run great inside a virtual machine because they want direct, exclusive, access to the GPU. That requires that the computer have 2 GPUs.  
You should NOT run the Ubuntu released this week, 23.04, since it has less than 1 yr of support and is a wide testing release. Stick with 22.04 until you have 1-3 yrs of Linux experience.

I'd suggest running Xubuntu or Ubuntu-Mate from the 22.04 release for a lighter desktop. They are both user friendly.  You can watch a few youtube videos about the XFCE and Mate DEs, so you'll have an idea BEFORE doing the install.

There is lots of great advice in these forums. Some is general and timeless.  Those threads are usually in the "sticky" threads at the top of each subforum.

---

### Post by ActionParsnip on 2023-04-21
Isn't "Linux 1.2023.1.0" related to Kali Linux?

---

### Post by coffeecat on 2023-04-21
Indeed. As far as I can make out, if Google has not led me astray, it's not just Kali but the Microsoft WSL version of Kali, which makes it about as far from Ubuntu as one could get. I've moved this to the sub-forum for Debian based distros.

---

### Post by TheFu on 2023-04-21
> **ActionParsnip said:**
> Isn't "Linux 1.2023.1.0" related to Kali Linux?

Kali shouldn't be used for daily use. It is a specific distro, for specific use.   It shouldn't be used for any other purpose than on a red-team engagement.  DO NOT TRY TO USE KALI as a typical desktop.

---

### Post by robynlep on 2023-04-21
I am using it for cybersecurity competitions

---

### Post by TheFu on 2023-04-21
If you are using virtualbox, then you want this [https://cdimage.kali.org/kali-2023.1/kali-linux-2023.1-virtualbox-amd64.7z](https://cdimage.kali.org/kali-2023.1/kali-linux-2023.1-virtualbox-amd64.7z) version of Kali.
[https://www.kali.org/get-kali/#kali-virtual-machines](https://www.kali.org/get-kali/#kali-virtual-machines) is the source, which you should use (not my direct link). After all, don't trust random people on the internet.  

There are other VM images for other hypervisors.  For example, since I use KVM/QEMU hypervisor, that's the easier image for my needs.

---

### Post by SeijiSensei on 2023-04-21
Start again and allocate more space during installation. You should allocate 20GB, 40 if you think you'll be using this system often and collecting data files. 

It's just a VM. A good reason to have them is so you can blow them away if things don't work out correctly.

---

