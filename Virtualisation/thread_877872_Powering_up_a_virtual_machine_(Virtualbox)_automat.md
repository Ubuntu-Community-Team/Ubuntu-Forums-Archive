---
title: "Powering up a virtual machine (Virtualbox) automatically"
date: 2008-08-02
forum: Virtualisation
---

### Post by nfox on 2008-08-02
Hey, does anybody know how to get a virtual machine to boot up automatically at login?

Running Virtualbox, I'd like to boot up LoseXP as soon as the app opens and add the app to the Autostart folder. That way XP users can feel at home running in seamless mode while having the advantage of free software to supplement XP-only apps.

Any ideas?

---

### Post by overdrank on 2008-08-02
moved to Virtualization :)

---

### Post by Jose Catre-Vandis on 2008-08-02
```
VBoxManage startvm nameofyourvm
``` is the command-line command to run a Vbox vm. You can then put this in your start up sessions or in rc.local. Depending on your setup you may want to use the VBoxHeadless command instead. read the Help file that comes with VirtualBox for more info.

---

### Post by nfox on 2008-08-04
I'm looking for a CLI way of getting seamless to start or a window-specific setting

---

### Post by Jose Catre-Vandis on 2008-08-10
If memory serves me right, if you shut down a seamlessly set VM, it will start up again seamless. Have a look over on [www.virtualbox.org](www.virtualbox.org) forums for further help

---

