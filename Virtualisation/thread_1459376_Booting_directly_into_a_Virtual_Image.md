---
title: "Booting directly into a Virtual Image?"
date: 2010-04-21
forum: Virtualisation
---

### Post by SonicSteve on 2010-04-21
Good Morning all,

I know that Virtualbox is developing it's own hypervisor, but I have a related question from a slightly different angle. 

Is there a way to boot up a scaled down Linux, that directly loads Virtualbox, that then can load various images on a local hard drive? I know that there would be various disadvantages to doing this, such as 3d support and perhaps even many others that I'm not yet aware of. However I would love to test an Idea like this out. It would be a virtualbox linux of sorts I suppose. 

Advantages. 
1. I would no longer need to have multiple windows images on my clonezilla server for every different hardware configuration. Instead one image for each purpose would work instead of multiple images for multiple purposes, on each different hardware configuration. 
2. Re-installation would be a snap, just copy a VDI file or re-image the drive with a clonezilla image of a preloaded virtualbox. 

So can this be done, or do we need to wait for the first level hypervisor that virtualbox is working on?

---

### Post by factory909 on 2010-04-22
I have often wandered this also! Maybe change your run level, and load vboxmanage startvm "my.vbox" from a script, i am sure there are other switches to throw at it. i am ready for the hypervisor also.

---

### Post by phrostbyte on 2010-04-26
I've done something similar before. 

Not sure the exact directory (/usr/share/gdm/sessions ?), but there is some directory with a list of sessions. You can add one that calls VboxSDL or some such. Then when you log-in, you can log-in directly into the VM. If I figure out the exact way I did it (it was awhile ago), I'll post a how-to. :)

---

### Post by MicroMouFenetre on 2010-04-28
Actually I was thinking about something similar:

In  Windows you can configure a UserId to auto-start an application uppon login.  User cannot use anything else than this application, closing the application triggers a logout.  Mostly used for Terminal Server access.  I'm searching an equivalent under Ubuntu.  You could assign "VBoxManage startvm my-guess-os" to a user and this would acomplish what you ask for.

I'm maintaning Windows users/PCs and am tired of re-installing the OS because too-laze-to-ready click OK and accept to download and install a malware and are ashamed so don't tell before after it's too late.  I'd love to install Linux, top it with VBox and Windows.  Except during the bootup sequence user couldn't see Linux but this would allow me to just Roll-Back instead of going through a re-install.

BTW : Microsoft included a joke in their Windows installation process.  It reads: "Windows Installer could not find driver software for your ethernet device.  Do you wish to connect to internet to try to find one?"

MicroMou Fenetre
I'm a PC and Ubuntu is a better idea.

---

