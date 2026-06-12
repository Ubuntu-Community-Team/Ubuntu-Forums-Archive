---
title: "Comm Program for Ubuntu?"
date: 2007-07-05
forum: The Cafe
---

### Post by Bungo Pony on 2007-07-05
Hey all! One thing I do a lot of in Windows is use my serial port. I usually use Telix to communicate from one computer to another. This is really useful for transferring large programs or files between computers, especially if one of the computers doesn't have USB or a CD drive (I hate wasting CDs for mundane things like drivers).

Anyway, is there anything like Telix or Procomm for Linux?

---

### Post by saulgoode on 2007-07-05
I believe ['minicom'](http://linux.about.com/od/commands/l/blcmdl1_minicom.htm) is still pretty much the standard for that.

---

### Post by jbeiter on 2007-07-05
Try seyon.

Just be aware something is broken with gnome-terminal. You will need to call xterm (or rxvt) with the following command:

"seyon -emulators xterm -modems /dev/ttyS0" (for com1)

---

