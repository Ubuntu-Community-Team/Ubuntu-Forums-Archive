---
title: "New Virtual Machine wont Power on"
date: 2008-05-04
forum: Virtualisation
---

### Post by Apex-jb on 2008-05-04
I installed VMware Server and have it running. I set up a new machine to install XP Pro on but when I try to Power it on for the first time it opens the console as if it were booting but then it powers off. Anyone know how to fix this?

---

### Post by fjgaude on 2008-05-04
You are working from the command line? or from an icon in the Applications menu?

---

### Post by Apex-jb on 2008-05-04
Im working in the GUI.
However, I restarted my computer and now it does not even see the virtual machine and when I try to create a new one it says it does not have permission to create the disk (it is on a separate partition).

---

### Post by fjgaude on 2008-05-04
Okay, exit vmware console. I think if you simply go to a terminal and do this:

```
sudo vmware
```

you will get the console back and then you will see where you installed your first VM. After you run it and then exit, you can use the GUI and see the VM from then on out.

Let us know how you do.

---

