---
title: "Boxes on Fedora Silverblue w/ Ubuntu 20.04 LTS VM + AWS VPS - Need to copy files"
date: 2021-08-25
forum: Virtualisation
---

### Post by liam-jdev on 2021-08-25
Hi Everyone,

I'm using Gnome Boxes for an Ubuntu 20.04 LTS virtual machine and I've set up the VM so that I could follow a course to build a WordPress Hosting Platform, which I've done on AWS using the Ubuntu 20.04 LTS AMI (AWS) here in the US. I need to move the files from that VM and VPS (that I SSH into) onto my flash/thumb drive, so I'm assuming that I first copy them from the VPS to the VM then from the VM to my actual computer - which came shipped with Fedora and I switched from Workstation to the immutable desktop on Silverblue - which I believe stores everything in VAR - then be able to copy it to the flash drive from there. If there are GUI instructions on how to do all of this then it'd be greatly appreciated as I've only been using Linux for just shy of nine (9) months. I believe that one can actually set up a GUI desktop environment on the Ubuntu 20.04 LTS AMI through AWS but I'm not quite sure which tool that is? Any help would be greatly appreciated! 

Thanks so much,

L

---

### Post by QIII on 2021-08-25
After some thought, moved to Virtualisation.

This might also be viewed as an exercise in moving records between any two or three machines, but the fact that virtualization is involved may complicate things.

---

### Post by MAFoElffen on 2021-08-26
Well... LOL... The problem is not with Ubuntu nor Fedora, but with Gnome Boxes.

It has had a long standing problem redirecting local USB devices. In fact the current version has an open bug report on the same.

You have some options. 
1. You could just open up a terminal on yourhost and use SCP to copy the file over to your USB thumb drive, host-to-host.
2. Gnome Boxes uses RDP (and/or VNC) for connections. You could use an RDP client from your Host to connect to the VM from your host. and use USB redirection from that client. Fedora user's top choice for RDP clients are still TigerVNC, Remina and X2GO aren't they? They have USB redirection, as long as you connect via RDP or Spice.

---

