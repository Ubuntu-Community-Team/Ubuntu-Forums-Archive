---
title: "Faking apt-get's installed packages info"
date: 2005-10-20
forum: Repositories &amp; Backports
---

### Post by agro1986 on 2005-10-20
I have an Ubuntu machine at home. This machine has no connection to the internet. There is an Ubuntu machine at the computer lab. This machine is connected to the internet. Of course, packages installed on my machine may differ from those on my lab's machine.

My question is, how can I emulate my computer's installed packages on my lab's machine. For example, when I do a "sudo apt-get --print-uris install octave" apt-get checks what packages octave depends and then compares them to packages installed on the current computer. I want apt-get to use my computer's installed packages info, not my lab's computer.

Any way to do this? I hope it's as simple as copying a file/some files from my computer and then giving a specific argument to apt-get (like "sudo apt-get --use-db=/media/usb/default.db ...").

Thanks a lot!

---

