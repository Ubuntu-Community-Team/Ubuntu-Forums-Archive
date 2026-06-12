---
title: "[SOLVED] Can I update virtualbox?"
date: 2008-09-16
forum: Virtualisation
---

### Post by slughappy1 on 2008-09-16
I currently have Virtualbox 1.6.6 installed. I have Windows Vista installed in virtualbox and I want to have the newest version of VB. Is there a way to update or install the new version and keep Vista installed?

---

### Post by Joeb454 on 2008-09-16
If I recall correctly, you can update to VBox 2.0 with no changes to your VM :)

You could always backup the .vdi file just in case

---

### Post by howefield on 2008-09-16
Just to confirm, updating the virtualbox program won't affect your virtual machines. It is also a good idea to back up your virtual machines just in case ;)

VBoxManage clonevdi source destination

---

### Post by WRDN on 2008-09-16
I upgraded Virtual Box myself today by removing it (in Synaptic) then installing the latest version. I can confirm that, when you remove/ install it, the settings for the virtual machines are not removed. These are stored in ~/.VirtualBox. As others have mentioned though, it's good to have a backup, just in case.

---

### Post by slughappy1 on 2008-09-16
Yeah, so I went to the virtualbox site and added the repository. I then installed it in Synaptic, which uninstalled the old one and installed the new one. Works perfectly

---

### Post by caco on 2008-09-17
Just install the .deb using dpkg -i 'package'.
Do remember to reinstall your guest additions though.

Have fun

---

### Post by griztown on 2009-02-23
I installed virtualbox following a HOWTO on this site and following the link in the HOWTO I installed 1.5.6.  So I tried to upgrade to 2.1.  I should note that earlier I had the OSE version installed but I successfully uninstalled it and added 1.5.6.  Now I uninstalled 1.5.6 and am trying to add 2.1.  I get the following error:

E: /var/cache/apt/archives/virtualbox-2.1_2.1.4-42893%5fUbuntu%5fhardy_i386.deb: trying to overwrite `/lib/modules/2.6.24-23-generic/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.24-23-generic

Thinking something was left behind from Virtualbox-OSE I marked it for complete removal in the Synaptic Package Manager, rebooted and tried again.  Same error.  The file mentioned '/lib/modules/2.6.24-23-generic/misc/vboxdrv.ko' does not exist on my system, at least that I can tell so I can't figure out how to fix this.  Any advice would be greatly appreciated.

---

### Post by griztown on 2009-02-23
Fixed it.  Stupid me.  In the synaptic package manager I scrolled down and there were many OSE module packages.  Down near the bottom were a couple that were still installed.  After marking those for complete removal it worked fine.  Sorry for the interruption.

---

### Post by shashank86 on 2011-10-29
> **slughappy1 said:**
> Yeah, so I went to the virtualbox site and added the repository. I then installed it in Synaptic, which uninstalled the old one and installed the new one. Works perfectly

Thanks, it worked great! Followed the instructions on this page: [Virtualbox for linux](https://www.virtualbox.org/wiki/Linux_Downloads)

> **WRDN said:**
> I upgraded Virtual Box myself today by removing it (in Synaptic) then installing the latest version. I can confirm that, when you remove/ install it, the settings for the virtual machines are not removed. These are stored in ~/.VirtualBox. As others have mentioned though, it's good to have a backup, just in case.

> **howefield said:**
> Just to confirm, updating the virtualbox program won't affect your virtual machines. It is also a good idea to back up your virtual machines just in case ;)

VBoxManage clonevdi source destination

Backed up though, just in case.

Cheers!

---

