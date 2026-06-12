---
title: "Deploying ubuntu servers on ESXi"
date: 2010-01-21
forum: Virtualisation
---

### Post by samosamo on 2010-01-21
I was using ubuntu-vm-builder (known in later versions as just "vmbuilder") for ubuntu server deployment on VMWare Server 2.0.  With one quick command I could create a clean vm image in two minutes flat. It's not working for ESXi 4.0.  It complains about incompatible IDE hard drive, does not allow me to add a network card, etc etc.

The new vmbuilder utility might produce better results but I'm not able to use it because it's incompatible with 8.04 LTS.  Maybe I should just wait until 10.04 LTS?

---

### Post by samosamo on 2010-01-22
OK, found a solution.  vmbuilder is able to build hardy images. I just have to run vmbuilder on machine with a more recent version of ubuntu.  So I created a karmic virtual machine, installed vmbuilder, and it creates hardy images for me in the same exact way the older ubuntu-vm-builder does.  Just had to change the shell script to match vmbuilder's new arguments.

This will all be useless in April 2010 when 10.04 LTS comes out.

---

