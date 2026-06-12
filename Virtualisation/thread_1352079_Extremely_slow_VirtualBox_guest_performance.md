---
title: "Extremely slow VirtualBox guest performance"
date: 2009-12-11
forum: Virtualisation
---

### Post by Tralce on 2009-12-11
I posted this in General Help as I didn't realise there was a virtualization forum. 

So I just installed 9.10 on my MacBook2,1. Almost everything is lovely. However, guest performance is VirtualBox 3.1.0 (closed source version) is abysmal. I've used the same version of VirtualBox on OS X, and on other computers, and it's run wonderfully. Host machine's specs are 2.16GHz Core2 Duo, 2GB DDR2667.

It's not just that's it's slow... it's almost like VirtualBox keeps pausing the emulation...

---

### Post by ubu-for on 2009-12-11
Which Ubuntu version did you choose? 32bit or 64bit?

---

### Post by lmarmisa on 2009-12-12
Is 3D acceleration of your VM enabled?. In my PC, the performance decreases a lot when 3D acceleration is enabled. Check also the base memory size (400 MB would be ok).

Host machine's specs looks fine.

Best regards,

Luis

---

### Post by Tralce on 2009-12-13
3D Acceleration is turned off. The base memory is set to 512. Never had an issue running XP with settings like these before, either.

---

### Post by Tralce on 2009-12-14
I've googled and read articles about similar problems with VirtualBox. The solution was to install an older version. Presently I'm using the closed-source 3.1, so I installed the closed source 3.0 to no avail and the OSE in the repository, also to no avail. Are there any tweaks I can try? I've tested some of my other VMs (xUbuntu 9.10, MS-DOS 7.10, and XP Pro) and all of them are just as laggy.

---

### Post by Tralce on 2010-01-08
So there's no difference between 32bit Ubuntu and 64bit Ubuntu. I'm using 32bit right now. 

The particularly off thing, here, is that approximately half the time, VirtualBox uses ALL of CPU2, and half the time it uses NONE of it. I'm talking statistically, here. Note the attached screenshot of GNOME System Monitor. All of the activity on CPU2 is caused by VirtualBox. I'm only running one VM: Windows XP Home with iTunes running inside, so that I can sync my iPhone.

---

