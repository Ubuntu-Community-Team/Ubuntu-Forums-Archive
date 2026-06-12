---
title: "Grub error with Hd install"
date: 2009-03-05
forum: Virtualisation
---

### Post by Midgetprawn on 2009-03-05
I have been following the instructions on how to run windows through Virtualbox. Having coped my grub to an Iso file and so on. However when I try to run the /iso/Boot/grub I get the old error 25. If my grub files have been copied and they work in a normal boot what have I done wrong?

---

### Post by Midgetprawn on 2009-03-05
As a bit of further info on my system. I am running 8,04 on an old 1ghz machine nd 512Ram. I have 2 hard drives with Ubuntu and Grub on a slave and windows XP on the master. I use this machine for teaching and some software is Windows based and I wanted access to both systems.

Is there a way to shortcut this error? I tried having SBM as an image in my virtual floppy but when I tried to install from hard drive it came back with the same stage 1 5  error 25 message

---

### Post by Midgetprawn on 2009-03-05
Hmmmm I bet I haven't installed the ISO file for grub. Where does the command save the file? Is it in my home folder?

---

### Post by riskomt on 2009-03-16
Yes It should be in your home folder. The copy of menu.lst is in /home/'whoami'/iso/grub/menu.lst

You have to mount the grub.iso into cd-rom to make the virtual machine boot

What for the error 25 message. I removed it by adding a second boot option to grub. As you see, I removed all other boot options to remove the risk of booting to my running system. But grub needs at least 2 options otherwise it is useless.

---

