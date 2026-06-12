---
title: "VirtualBox Ubuntu wont restart after running tasksel"
date: 2020-09-11
forum: Virtualisation
---

### Post by Dave_Davis on 2020-09-11
I have been trying for ten days to create a virtual Ubuntu server using Oracle VirtualBox which is running on Windows 10.

In general I am able to create the virtual machine with no problems.

I then run tasksel to install LAMP and Samba.

Now, after a restart I see a message like

[B]/dev/sda5: clean, 129507/4571136 files, 2058864/18269184 blocks

[/B]and the restart hangs.

A second attempt at restart throws me into a terminal from which I can't seem to do anything.

I suspect it has something to do with the configuration of the virtual drive but nothing I've tried seems to help.

Any suggestions? Thanks

---

### Post by SeijiSensei on 2020-09-11
You could start over and not use tasksel.  Just install the packages from the command prompt:
```

sudo apt install lamp-server^
sudo apt install samba

```
I've never encountered problems like these when installing Ubuntu Server to a VM.  (You do know it has no GUI, so you should expect to see a terminal, right?) I'm not sure what you mean about the configuration of the virtual drive. I just choose the default, a "VirtualBox disk image" and everything works as expected.

---

### Post by wildmanne39 on 2020-09-11
Moved to virtualisation.

---

