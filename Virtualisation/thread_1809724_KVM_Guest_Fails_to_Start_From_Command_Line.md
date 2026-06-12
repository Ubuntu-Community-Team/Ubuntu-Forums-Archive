---
title: "KVM Guest Fails to Start From Command Line"
date: 2011-07-22
forum: Virtualisation
---

### Post by Aaron80 on 2011-07-22
I'm running Ubuntu Server 10.04 as a headless server on my home network and I've installed a VNC interface so that I have remote access to a GUI when needed. I've got my box configured so that the host machine doesn't do much except host my guests and provide NFS access to the media I'm using my guest machine to share. My host and guest machines are working beautifully, but I recently discovered, I can't start my guest from the command line using:

virsh --connect qemu:///system start GuestMachine

I can start the GuestMachine within the GUI using the Virtual Machine Manager, but that's not really a fix to my problem. 

Looking through my log files I found that the Guest will not boot due to an empty CDROM (on my system /dev/sr0) and this is a known bug.

Does anyone know how I can fix this problem my Google searches have not turned up much.

---

