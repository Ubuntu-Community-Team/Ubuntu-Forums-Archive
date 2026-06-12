---
title: "VirtualBox 3.14 Installation Errors Karmic"
date: 2010-03-23
forum: Virtualisation
---

### Post by mikey5555 on 2010-03-23
Hello all, 
I am experiencing a problem with installation of v**irtualbox-3.1_3.1.4-57640_Ubuntu_karmic_amd64.deb** in Ubuntu Karmic X64.  I get the following error message when installing from either Synaptic or via command line in a terminal:

> E: /var/cache/apt/archives/virtualbox-3.1_3.1.4-57640%5fUbuntu%5fkarmic_amd64.deb: trying to overwrite '/usr/share/virtualbox/VBoxGuestAdditions.iso', which is also in package virtualbox-guest-additions 0

 I have tried deleting the file **VBosGuestAdditions.iso** in /usr/share/virtualbox , checked the permissions on that dir (they are:drwxr-xr-x) and the Ownership of the file/directory - owned by root:root .  I deleted the VBox .deb file from **/var/cache/apt/archives/** and downloaded directly from [virtualbox.org](virtualbox.org) and ran the install using **sudo apt-get install virtualbox-3.1_3.1.4-57640_Ubuntu_karmic_amd64.deb** - with the same error message.
I had VirtualBox installed and running just fine with this same Ubuntu release until I did a fresh install and am now trying to re-install VirtualBox so I can restore my virtual XP installation which I saved to a different drive before I re-installed Ubuntu.
Has anyone else experienced thius problem?  Does anyone have any ideas on how to get this installation to complete?  
Any help will be appreciated...

Regards...
mikey5555

---

### Post by codfather on 2010-03-23
Does running "dpkg -l | grep virtualbox" show virtualbox as still being installed?

Are you using the OSE version or have you installed the Sun's Virtualbox repository in your software sources?

If it does then I would delete it fully using dpkg --purge, and then check to see the status of the package again. 

If it doesn't show as installed then retry the install.

hth

Nick

---

