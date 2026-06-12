---
title: "Problems with VirtualBox OSE in Ubuntu 8.04"
date: 2008-09-27
forum: Virtualisation
---

### Post by linux4life88 on 2008-09-27
When I go to run a virtual machine I get this message:
[I]
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..[/I]

So then I go into Synaptic Package Manager to download the file and get this message:
[I]
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

virtualbox-ose-modules-generic:
 Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed[/I]

So then I try to install that file and get this message:
[I]
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

virtualbox-ose-modules-2.6.24-20-generic:
 Depends: linux-image-2.6.24-20-generic  but it is not installable[/I]

All I'm getting is error messages. What am I doing wrong?

---

### Post by linux4life88 on 2008-09-27
I got the previous problem fixed and now have a virtual PC running. But I can't get the mouse to work in the virtual machine? How do I get the mouse to work?

---

### Post by linux4life88 on 2008-09-27
Ok, I think I now have everything fixed.

---

