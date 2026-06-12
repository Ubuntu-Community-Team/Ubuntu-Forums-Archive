---
title: "Virtual Machine Manager and qemu-kvm problem"
date: 2011-10-15
forum: Virtualisation
---

### Post by Keith_Beef on 2011-10-15
I set up a virtual machine, installed an image of Windows XP from a bootable DVD with Symantec Ghost, and evrything went well, so it seemed.

But now, when I try to start it up again, using ```
gksu virt-manager
``` I get this:
```
Traceback (most recent call last):
  File "/usr/share/virt-manager/virt-manager.py", line 452, in <module>
    main()
  File "/usr/share/virt-manager/virt-manager.py", line 395, in main
    icon_dir, data_dir)
  File "/usr/share/virt-manager/virtManager/config.py", line 99, in __init__
    gconf.CLIENT_PRELOAD_NONE)
GError: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Command line `dbus-launch --autolaunch=49399f56ec92fc1b6f1035e500000148 --binary-syntax --close-stderr' exited with non-zero exit status 1: No protocol specified\nAutolaunch error: X11 initialization failed.\n)
```

Any ideas why?

---

### Post by iburry on 2011-10-17
Hmmm, gksudo and virt-manager do not seem to get along well. I can get it up and running by calling:

```
gksudo "virt-manager --no-fork"
```but it will not connect to any VMs. I think it still has no d-bus session. Is there a reason you need to run it with sudo?  It works fine as a normal user for me.

---

