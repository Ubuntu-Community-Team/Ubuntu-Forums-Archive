---
title: "Is there a way to gain SU rights in my virtualbox install?"
date: 2017-02-19
forum: Virtualisation
---

### Post by magicchords on 2017-02-19
Hey guys.
So I have to use a program called Phamerator for my DNA annotation class. The only platform it's available on is Ubuntu because the developers are short sighted I suppose.
I originally had planned to run a fresh install of Ubuntu and just install the program from a tarball, but it seemed like it had other plans. There was just one problem after another with installation, so I gave up and downloaded the Sea Phages virtual machine image.
However, the file is 2 years old and needs a lot of updates. There are three accounts, SEA Admin, SEA Faculty, and SEA Student. I only have access to SEA Student which has no administrative rights. So, the machine and the program is virtually useless unless I can gain root access to the machine.
Is there any way I can do this?

---

### Post by Impavidus on 2017-02-20
It's quite common for more scientific software to be Linux-only. Or every operating sytem except Windows. That's why I switched to Linux and never switched back.

As you have "physical access" to that virtual machine, [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword). But I never tried that on a virtual machine. And I don't know if your virtual machine image is actually Ubuntu-based, so it may not work.

As this is for a class, there must be more people around you trying to install that software. Have they not succeeded in installing it from that tarball? I'd expect that to be the easiest way. You probably have to install some dependencies or set some environment variables. In general installing from a tarball is not the easiest way, but the more attractive options seem unavailable to you.

---

### Post by mastablasta on 2017-02-21
it's not silly they chose Linux. however, their method of install is just bad and overly complicated: [SIZE=2]http://phamerator.webfactional.com/PhameratorNativeInstallation.pdf
[/SIZE]
they could have used a script to do all that for the user or create a .deb file.

---

### Post by howefield on 2017-02-21
Thread moved to the "*Virtualisation*" forum.

---

### Post by SeijiSensei on 2017-02-22
Do you see the Ubuntu boot menu when the VM starts up? If not, hold down the shift key while booting.  Now you can choose "recovery mode" which will let you change the passwords.  See this for details: [http://askubuntu.com/questions/32623/how-to-boot-into-single-user-recovery-mode](http://askubuntu.com/questions/32623/how-to-boot-into-single-user-recovery-mode)

---

