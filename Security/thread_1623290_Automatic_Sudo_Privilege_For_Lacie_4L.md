---
title: "Automatic Sudo Privilege For Lacie 4L?"
date: 2010-11-16
forum: Security
---

### Post by NoVista on 2010-11-16
Users of Lacie's 4L which is used to burn labels for your Lightscribe disks, are required to have the app run with sudo privileges, (the command being: gksudo 4L-gui).
On an older version of an Ubuntu install, I had it set up so that it did this automatically, without it, (or me), being asked for a password.
How did I do this, as I forgot?

I thought it was something I added to the sudoers file, to give 4l-gui automatic authority, but I forgot how i did it..
Help please.
For clarification, I am not talking about just lengthening the sudo-timeout length.

---

### Post by bodhi.zazen on 2010-11-16
> **NoVista said:**
> Users of Lacie's 4L which is used to burn labels for your Lightscribe disks, are required to have the app run with sudo privileges, (the command being: gksudo 4L-gui).
On an older version of an Ubuntu install, I had it set up so that it did this automatically, without it, (or me), being asked for a password.
How did I do this, as I forgot?

I thought it was something I added to the sudoers file, to give 4l-gui automatic authority, but I forgot how i did it..
Help please.
For clarification, I am not talking about just lengthening the sudo-timeout length.

[http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

See the nopassword option.

---

### Post by NoVista on 2010-11-16
Much appreciated.

---

