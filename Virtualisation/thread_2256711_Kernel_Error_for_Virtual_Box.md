---
title: "Kernel Error for Virtual Box"
date: 2014-12-14
forum: Virtualisation
---

### Post by Ben_Briggs on 2014-12-14
So, I'm a fairly new user of Lubuntu who has just installed VirtualBox successfully, looking to run Kali-Linux on my ThinkPad. I have therefore downloaded the correct Kali-Linux iso file that I am using to obviously install into VirtualBox. However, when I try to start the virtual machine running the new O.S it pops up with an error message which reads:

[COLOR=#000000][FONT=Verdana]""" The [VirtualBox]("https://www.virtualbox.org/wiki/VirtualBox") Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]'/etc/init.d/vboxdrv setup'[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary. """[/FONT][/COLOR]

Apparently for some users who then run the command shown in the error message in the terminal are then perfectly fine and can continue with their installation; not me. My second and most important problem therefore is that when I type this command into Terminal it pops up with a stream of error messages as follows:

"Stopping VirtualBox kernel modules ...done.
Recompiling VirutalBox kernel modules/etc/init.d/vboxdrv: 334: /etc/init.d/vboxd
rv: cannot create /var/log/vbox-install.log: Permission denied
 ...failed!
 (Look at /var/log/vbox-install.log to find out what went wrong)"

This stream appears instantly after the command is entered and I also tried to enter the command shown to find out what went wrong like it told me to... and this error message was shown:

"bash: /var/log/vbox-install.log: Permission denied"

So, basically nothing works so I am completely stuck on what to do especially as it is a permission error. Please, I am begging someone to help me in any way they can even if they just refer me to another website or tutorial I am open for suggestions and don't mind what is said.

P.S: Please don't have a go at me if there is an obvious and/or easy fix to this because as I said, I am a new user and am a bit of a noob at this.

Thanks,
            Ben. :)

---

### Post by ibjsb4 on 2014-12-16
It says permission denied, did you use 'sudo' with that command?
> Please don't have a go at me
This is a friendly forum :)

---

### Post by QIII on 2014-12-16
Moved to Virtualisation.

And if anyone "has a go at you", we'll take care of that quickly.  :)

---

