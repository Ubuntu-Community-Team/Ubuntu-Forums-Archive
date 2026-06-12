---
title: "Vbox"
date: 2013-01-27
forum: Virtualisation
---

### Post by XBMC old School on 2013-01-27
Hey Everyone.

I have VBox runnning and have kernel issues with my machines. I do have a recompiled linux kernel (3.7.4) but when i reboot into the 3.2.0.29 generic kernel i still have the same issues. I did all the suggestions in [this thread  ]("http://ubuntuforums.org/showpost.php?p=11484984&postcount=1")and got no results. The paste bin below shows the Vbox errors.

```
Failed to open a session for the virtual machine 'machine'
The virtual machine 'machine' has terminated unexpectedly during startup with exit code 1.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}


Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.]
```

And when i ran s[COLOR=Blue]udo modprobe vboxdrv[/COLOR] i got[COLOR=Blue] FATAL: Module vboxdrv not found[/COLOR]

then ran [COLOR=Blue]sudo /etc/init.d/vboxdrv setup [/COLOR]and got nothing

I also went to recompile my kernel to see if anything was missing in the virtualization section and saw everything was tagged a module.

i am at a loss here. i don't really want to go through the process of fully uninstalling Vbox and reinstalling it if i can avoid it.

thanx.

---

### Post by heiko_s on 2013-02-01
> **XBMC old School said:**
> Hey Everyone.

I have VBox runnning and have kernel issues with my machines. I do have a recompiled linux kernel (3.7.4) but when i reboot into the 3.2.0.29 generic kernel i still have the same issues...

What happens when you boot the 3.7.4 kernel?

---

