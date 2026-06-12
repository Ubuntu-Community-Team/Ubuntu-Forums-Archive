---
title: "Ubuntu 8.04 and Qemu resolution problems"
date: 2008-07-31
forum: Virtualisation
---

### Post by bojack on 2008-07-31
Ok I have ubuntu 8.04 installed to a Qemu hard drive thing and everything is going good, but I can't for the life of me get the resolution to go above 800X600, and it is useless at that resolution because some programs take up way more space than that and end up having parts of them cut off rendering them frusturating and in some cases useless. I have tried to manually edit the Xorg file and it didn't work. I tried to install the Nvidia drivers with Envy and it couldn't detect a video card. I tried to change the monitor selection in low graphic mode and it does resize to a much better size but it renders the screen filled with odd looking blackish patterns only and then resizes back to the normal size. Is it possible to rezize the qemu window or change the resolution of ubntu 8.04 in Qemu? Please help with this if you know, it is very frusturating for me.

I have seen a lot of people around the internet with similar issues but no one seems to know how to fix it.

---

### Post by LinuxRocks713 on 2008-08-04
You have three ways out of this:

1. Install QEMU Virtual Video Card drivers. They are floating around the web somewhere; just find them and install them.

2. Install another virtualization solution, such as VMWare or VirtualBox.

3. **Forget Ubuntu** and stick with Windows if you are still stuck.

---

### Post by fajifazeel on 2008-08-05
how to reduce the resolution of ubuntu

---

