---
title: "VMware Player 4.0.1"
date: 2011-11-19
forum: Virtualisation
---

### Post by dcstar on 2011-11-19
I see it now officially supports Ubuntu 11.10.

Still totally stuffs up my rc.d scripts when it installs.

---

### Post by fjgaude on 2011-11-19
You are correct... when I tried to load a 11.10 VM made with 4.0 Player 4.0.1 unloaded itself. <sigh>

Knowing VMware they will fit this quickly, eh?

---

### Post by dcstar on 2011-11-21
> **fjgaude said:**
> You are correct... when I tried to load a 11.10 VM made with 4.0 Player 4.0.1 unloaded itself. <sigh>

Knowing VMware they will fit this quickly, eh?

4.0.1 does not actually break the scripts any more, it is the 4.0.0 uninstall as part of the upgrade process that breaks them!

I did a fresh Player 4.0.1 on install on a new 10.04.3 system and it worked fine, unfortunately anyone with an existing 4.0.0 install will suffer.

---

### Post by fjgaude on 2011-11-21
Yes, I found what you report to be true.

---

### Post by Calculon64 on 2011-11-21
How do I install VMWARE 4.0.1 (64-bit) in Ubuntu 11.10 (64-bit)?

---

### Post by fjgaude on 2011-11-21
Go to vmware.com and download player 4.0.1. From where you have it on your computer run .bundle file from root. But first you have to make sure that file is executable by using Nautilus file manager and going to Permissions, or setting it by the command line.

---

### Post by Calculon64 on 2011-11-21
> **fjgaude said:**
> Go to vmware.com and download player 4.0.1. From where you have it on your computer run .bundle file from root. But first you have to make sure that file is executable by using Nautilus file manager and going to Permissions, or setting it by the command line.

Thanks for your reply.  Could you be a little less technical with your explanation... perhaps a bit of instructions... if is not too much trouble.

Thank you

---

### Post by tobcro on 2011-11-22
I usually install VMware Player updates just like fjgaude suggests. Maybe there is a more "correct" way, but this usually work 100% for me. The old version gets uninstalled correctly and the new installed without hassle (Installed 4.0.1 on my Xubuntu 11.10 yesterday). 

First, download the latest .bundle for 32- och 64-bit Linux, rightclick the downloaded file in File Manager, choose properties and make it executable (tick the checkbox).

Then open a terminal window and execute your File Manager as root, since i run Xubuntu i use:

> sudo thunar

A standard Ubuntu user would use:

> sudo nautilus

Then right-click the downloaded file and choose Execute. The installation should start.

After installation is done, do not forget to close the "rooted" File Manager.

---

### Post by fjgaude on 2011-11-22
Thanks, tobcro, for doing what I was to do.

Can you follow what is required, Calculon64?

If not we will try to be less technical.

---

