---
title: "[SOLVED] Launch VM directly?"
date: 2008-07-02
forum: Virtualisation
---

### Post by prshah on 2008-07-02
Hello,

I have Virtual-box-ose setup and running with an XP guest OS. Currently, I click Applications-System Tools-Virtual Box OSE-wXP-Start to get the VM running. Is there any way for me the run the "wXP" virtual machine _directly_, (command line or otherwise) without launching the virtual-box virtual machine manager window?

---

### Post by quonsar on 2008-07-03
Create a new launcher on your desktop. Name it Win XP, in the command field type 

```
VBoxManage startvm "VM Name" -t gui
```

Choose an icon (attached is a nice one you can put in /usr/share/pixmaps and use) and close the window. You will now have a desktop icon you can use to start the VM directly.

---

### Post by prshah on 2008-07-04
> **quonsar said:**
> 
```
VBoxManage startvm "VM Name" -t gui
```


Thanks, that worked great! As a matter of interest, what is the "-t gui" part? It runs fine even without that switch.

---

### Post by quonsar on 2008-07-04
ah, so it does! gui must be the default. -t takes one of two values for choosing gui or remote "headless" operation. that's from memory, i seem to have deleted or misfiled my manual!

---

