---
title: "[half-solved] BSOD - Dual boot W7 - external hdd"
date: 2014-02-10
forum: Windows
---

### Post by alex-lleroux1 on 2014-02-10
Hey,

First of all, I'm not a native speaker nor writer, so please try to get over my writing skills.

Secondly, I've asked this on several forum windows forum but the answer where quite  closed minded, i hope the Ubuntu community won't deceive me :)

I've installed a ssd in my laptop a month ago and as the space on it is quite limited i didn't invest time to install/clone Windows as my main OS is under Linux.

The initial idea was to boot from the old hard drive mounted as an external one when i would like to use it (quite sheldom to game). Indeed when i boot, GRUB load (the interface which allow to chose between linux or windows) i have no problem booting my old Linux, but Windows crash. First there is a message about a hard-drive change, after that i have two possibilities :

    repair the system &#8594; do not detect any installation
    boot &#8594; BSOD ( and I cannot read anything it reboot immediately )

Here are the result from a boot-info made from linux: [http://paste.ubuntu.com/6832114/](http://paste.ubuntu.com/6832114/)

Any help would be likely appreciated

---

### Post by oldfred on 2014-02-10
Windows does not boot from external drives.

It builds in checkers to make sure you only run it on the system you installed it into, so you cannot use it on an external that you might use with a different PC.

---

### Post by alex-lleroux1 on 2014-02-11
That's what i though but i booted by "mistake" some years ago W7 from a hdd i wanted to recover. But w7 was installed on my internal hdd. 

Is a virtual machine installed on the external hdd is a solution? How can i know how much capacities running the VM will take ( as my notebook is already 4years old). I'm aware i'll be quite slow

---

### Post by sudodus on 2014-02-11
> **alex-lleroux1 said:**
> That's what i though but i booted by "mistake" some years ago W7 from a hdd i wanted to recover. But w7 was installed on my internal hdd. 

Is a virtual machine installed on the external hdd is a solution? How can i know how much capacities running the VM will take ( as my notebook is already 4years old). I'm aware i'll be quite slow

Yes, it is a solution. But Microsoft considers the virtual machine to be another machine than the bare metal machine, so you need another license for it. On the other hand, such an installation in a virtual machine is probably portable (I think you can port the virtual machine from one bare metal machine to another, at least it was possible with Windows XP).

It will be slower, of course. A machine with core2duo and 4 GB RAM will work fairly well. 2 GB RAM will be tight.

---

### Post by alex-lleroux1 on 2014-02-11
Ok thanks you :) i think i'll go for a VM, except if it exist a way to trick windows at boot. I read on a blog that it's possible to remove a license from a computer, i'll try that ( but need to swap my HDD ...). 

Does anyone have a good tutorial and information about virtual machines ? i never used that before :confused:

edit:i have 4gb RAM and a dual core 1,3ghz  so i guess it will work.

---

### Post by sudodus on 2014-02-12
You can start here

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by alex-lleroux1 on 2014-02-12
Thank you.

---

