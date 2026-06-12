---
title: "Sun Virtualbox will not start"
date: 2009-07-28
forum: Virtualisation
---

### Post by DoubleCross on 2009-07-28
My Sun Virtualbox is running Windows Vista and wil not start a session. I can not uninstall the virtual box and I cannot update the program. When I start virtual box, I get the error message

[CENTER]
[/CENTER]
  p, li { white-space: pre-wrap; }  Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


I have opened a terminal and entered the command line but nothing happens. 



I am relatively new to Ubuntu so any help will be greatly appreciated.

---

### Post by Devastator9 on 2009-07-28
did you reboot afterwards i had too.

---

### Post by bodhi.zazen on 2009-07-28
```
sudo /etc/init.d/vboxdrv setup
```If that fails, what version of Virtualbox did you install ? OSE or PUEL ?

---

### Post by jbrown96 on 2009-07-28
You probably are not added to the vboxusers group. run ```
sudo usermod -aG vboxusers $USER
``` then logout and login then try again.

Edit: You can check first by running ```
groups $USER
```

---

### Post by bodhi.zazen on 2009-07-28
> **Devastator9 said:**
> did you reboot afterwards i had too.

I have not had to re-boot

Although If you just installed virtualbox, you do need to log out and back in (for the group changes to take effect).

---

### Post by Devastator9 on 2009-07-28
Bodhi
i had to on both computer here.

---

### Post by bodhi.zazen on 2009-07-28
> **Devastator9 said:**
> Bodhi
i had to on both computer here.

next time you install virtualbox, next log out and back in. If virtualbox will not start run

[cdoe]sudo /etc/init.d/vboxdrv start[/code] in a terminal.

I have never had to reboot after installing Virtualbox.

---

### Post by DoubleCross on 2009-07-29
sudo /etc/init.d/vboxdrv setup worked. Virtual box now work fine. Thanks for the help.

---

### Post by bodhi.zazen on 2009-07-29
Thanks for the feedback and we are happy you got it working.

---

