---
title: "Gutsy won't install VirtualBox PUEL"
date: 2007-11-03
forum: Virtualisation
---

### Post by moonshinerat on 2007-11-03
Hi fellas

Can't see this message anywhere else in the forums so here goes...

I've tried to install VirtualBox (PUEL to get the USB support) and it won't install. I keep getting the following message:

Unpacking virtualbox (from virtualbox_1.5.2-25433_Ubuntu_gutsy_amd64.deb) ...
dpkg: error processing virtualbox_1.5.2-25433_Ubuntu_gutsy_amd64.deb (--install)                                                              :
 trying to overwrite `/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko', which is                                                               also in package virtualbox-ose-modules-2.6.22-14-generic
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 virtualbox_1.5.2-25433_Ubuntu_gutsy_amd64.deb

I don't really care if vboxdrv.ko is in the OSE version. I want to install the PUEL version so I can run the USB stuff. How do I get this installed? Innotek's install procedures are garbled rubbish and the "up-to-date" manual isn't up-to date to cover the new installation procedures. Thanks guys.

---

### Post by Delvien on 2007-11-04
Uninstall the OSE vbox first. then try again.

---

### Post by moonshinerat on 2007-11-04
Cheers Delvian.

Didn't even realize it was installed. It was actually the modules for OSE that were there not the main application and the package manager didn't show it.

Many thanks.

---

### Post by Delvien on 2007-11-05
> **moonshinerat said:**
> Cheers Delvian.

Didn't even realize it was installed. It was actually the modules for OSE that were there not the main application and the package manager didn't show it.

Many thanks.


Anytime : )

---

