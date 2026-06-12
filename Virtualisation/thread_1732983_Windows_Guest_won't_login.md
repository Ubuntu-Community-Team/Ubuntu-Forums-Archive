---
title: "Windows Guest won't login"
date: 2011-04-18
forum: Virtualisation
---

### Post by freakinjonathan on 2011-04-18
Okay I have a Windows XP Guest machine that will automatically restart after it says Windows is Starting up. After is says this it will invariably reboot. This is right before it actually finishes logging in. I can boot into safe mode just fine however. I am only not able to start the Windows vm Normally, and it's only on this box.
I have tried cloning this virtualmachine via the VBoxMange clonehd and exporting this vm to other machines without a problem. I'm not sure what could be causing this but it is a major pain in the butt!

---

### Post by CharlesA on 2011-04-18
Did you enable 3d support in the VM settings?

---

### Post by freakinjonathan on 2011-04-23
I enabled 3D and 2D acceleration.
Settings > Display > Video > extended features > Enable 3D acceleration
Settings > Display > Video > extended features > Enable 2D acceleration
Also, I did some updates to my machine it wanted me to do this cmd: /etc/init.d/vboxdrv setup. I guess I did some kernel updates so I had to rebuild the module. Upon rebuilding this message came up

* Stopping VirtualBox kernel modules                                            *  done.
* Uninstalling old VirtualBox DKMS kernel modules                               *  done.
* Trying to register the VirtualBox kernel modules using DKMS                  
*** Failed, trying without DKMS**
* Recompiling VirtualBox kernel modules                                         *  done.
* Starting VirtualBox kernel modules                                            *  done.

None of these steps solved the issue, however.

---

### Post by CharlesA on 2011-04-23
Turn off 3d acceleration.

---

### Post by freakinjonathan on 2011-04-24
Okay I turned them both back off.
Also I made sure that the account I am currently logged onto is a member of Vboxusers.
Still this issue has not been resolved. I'm not really sure what else to try.

---

