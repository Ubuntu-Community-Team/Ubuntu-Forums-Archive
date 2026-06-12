---
title: "Ubuntu 13.04 VM as a guest, Windows 8 Host - sound not connecting"
date: 2013-08-19
forum: Virtualisation
---

### Post by RichardET on 2013-08-19
Say I have two main machines these days, a Dell 660 with Win. 8 core i5, and  Lenovo W530, also with Win. 8, and a core i7.  All VM's work flawlessly on the Lenovo,
but on the Dell, I have seen issues with the same VM not working on it, as far as getting sound goes.  The constant thread is GNOME based DE, which I think includes Unity.
KDE does not have this problem, but alas, I am not a KDE guy.  But I think I solved it for Ubuntu 13.04;  I copied the VM from the Lenovo to the Dell, then I deleted sound from the VM parameters, then added it back in after the VM was running.  Now it seems to work.   I am not sure if I just got lucky, or it is a permanent fix, but thought I would pass it along.
I have seen this bug before with other Dell's I have owned in the past, using a Suse Linux with GNOME.  I currently use the latest VMWare, version 9.03.

I have tested it with the latest LTS, 12.04 on the Dell, and it works as well now with sound.

---

