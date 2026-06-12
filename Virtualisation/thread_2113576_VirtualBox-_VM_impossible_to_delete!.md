---
title: "VirtualBox- VM impossible to delete!"
date: 2013-02-07
forum: Virtualisation
---

### Post by GameX2 on 2013-02-07
Hi,

I've configured a Windows XP VM today, but did the mistake of creating 2 snapshots, while my Linux partition was quite small.  I ended up running out of disk space..  Tried to delete snapshots from VirtualBox, but not only this is taking forever (VMware is faster), but I also felt like deleting a snapshot was taking up disk space instead of freeing some.

Well, with 100 KB of free disk space, I couldn't start many programs, Firefox kept crashing, so well.  I got kind of frustrated and deleted the whole VM folder from Nautilus.  Heck, I'm going to configure this VM again..
Now, the VM is still present in the VirtualBox menu, but I can't even remove it from the library, the option is greyed.

When I go to "Snapshots", I find the 2 snapshots that I manually deleted earlier.  If I try and press "Delete" in VirtualBox, it juste freeze forever.

I've tried deleting the " .VirtualBox " folder from my Home folder, and even removing VirtualBox with " sudo apt-get remove virtualbox ", cleaning the remaining configuration with Ubuntu Tweak, and this useless deleted VM still show up in the library.

..... What the hell ? O__o

What I can do to fully reset VirtualBox so that VM would finally goes away?

EDIT: Got it.  Thanks Synaptic.  Manage to delete the remaining configuration from here, and deleted configuration from Ubuntu Tweak as well.  Now the VM was shown as "innacessible", but was deletable.

Thanks!

---

