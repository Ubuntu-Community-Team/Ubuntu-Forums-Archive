---
title: "How to explicitly fix the guest resolution so it doesn;t revert to 800x600 after rebo"
date: 2022-07-05
forum: Virtualisation
---

### Post by user_stu on 2022-07-05
I have Ubuntu 22.04 running as a guest in virtual box (hosted on Windows 10)

Since I installed virtual Box guest additions, Ubuntu reboots result in the resolution being reset to 800x600, so I have to explicitly reset it (to 1290x1080) via display settings after every reboot.

How do I fix this (literally fix it to 1290x1080)?

I found this post [https://forums.virtualbox.org/viewtopic.php?f=3&t=103812](https://forums.virtualbox.org/viewtopic.php?f=3&t=103812)  but cannot work out where/how to enter the command:


VBoxManage setextradata "VM name" "GUI/LastGuestSizeHint" "1024,768"       


(in my case, the resolution needs to be 1290x1024, so I assume I can just replace 1024,768 with 1290,1080  but no idea where the file(?) is that I need to edit).

---

### Post by TheFu on 2022-07-06
The vboxmanage command is for the hostOS.  Put it on that system.  If the file you want doesn't exist, create it.  I suspect it is a 1-time command that will alter the default GUI setup for the guest, so try running the specific command BEFORE you start the VM.

---

### Post by MAFoElffen on 2022-07-06
Or in the Ubuntu VM Guest... Set the desired resolution to 1290x1080 in the Grub Default file, so that the Kernel can use KMS to set the mode persistently at boot.

Please refer to my Graphics Resolution Sticky in my Signature line, Post #1... Search on 'how do I make it permanent?'

---

### Post by user_stu on 2022-07-07
Thanks guys

---

