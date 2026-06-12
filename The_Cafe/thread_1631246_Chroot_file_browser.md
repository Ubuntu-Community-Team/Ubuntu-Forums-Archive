---
title: "Chroot file browser"
date: 2010-11-26
forum: The Cafe
---

### Post by nerdopolis on 2010-11-26
Hi.

Does anybody know of any file browsers out there that emulates running in chroot? I am trying to make a live cd that simplifies chroot for the user. 

what I am looking for is that you specify a folder like /media/disk, and the file manager does not let the user go above /media/disk (so that they don't get confused), it shows /media/disk as /, and when the user executes a script from the file manager, it calls the script in chroot?

I can not install any stuff onto the chroot folder, as I can't assume the package manager, and I can't assume the package manager is in a working state, so thats why I need such a weird file manager. 


If not I'll probably end up creating a hashed up file manager with kdialog, shell scripts and FIFOs and sockets, which probably won't be that user friendly...

---

### Post by nerdopolis on 2010-12-11
OK. I found the best way is to run a ssh server in the chroot, and then use a graphical file manager like Dolphin that supports ssh. 

Any one know of a portable SSH server? one that can be extracted and run? I can't assume that the SSH server is installed in the chroot.

---

