---
title: "[VBox] Virtualize a physical windows"
date: 2013-03-24
forum: Virtualisation
---

### Post by N3mesis98 on 2013-03-24
Hello all,

I'm actually trying to virtualize my windows 7 partition in virtualbox.
I have already done this thing with a windows as host but until there it didn't work on Ubuntu...

So here is what i've done:
- execute the command: sudo VBoxManage internalcommands createrawvmdk -filename ex.vmdk -rawdisk /dev/sda1
- there is confirmation that the .vmdk have been created
- launch VBox in root
- create a new virtual machine with the .vmdk as file system

And then when I launch the virtual machine I just have a black screen...
No error but just a black screen...


An idea to fix this?
Thx in advance

---

