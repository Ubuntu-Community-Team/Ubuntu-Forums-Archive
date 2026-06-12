---
title: "Impossible to boot after trying to install Anbox"
date: 2019-07-30
forum: Ubuntu/Debian BASED
---

### Post by gabrieldar on 2019-07-30
Hi everyone,
I tried to install Anbox to emulate Android on my laptop running Bodhi Linux, with following lines:
```

[LEFT][COLOR=#404040][FONT=SFMono-Regular]$ sudo add-apt-repository ppa:morphis/anbox-support
$ sudo apt update
$ sudo apt install linux-headers-generic anbox-modules-dkms
[/FONT][/COLOR][COLOR=#404040][FONT=SFMono-Regular]$ sudo modprobe ashmem_linux
$ sudo modprobe binder_linux
[/FONT][/COLOR][COLOR=#404040][FONT=SFMono-Regular]$ sudo snap install --devmode --beta anbox
[/FONT][/COLOR][/LEFT]
```
(I also had to install Snap meanwhile)
My laptop froze and since then the startup process fails each time and gives me a black screen. I succeeded twice over 100 attempts and it froze twice shortly after.
I don't know how to register boot process and time, but it seems to fail at different steps, for instance:
```

system.getty.slice 
networkmanager.service
colord.service

```

Booting in recovery mode and booting directly to the command line are not working.
When I try to disable kernel modules ashmem and binder from Grub, booting stops at "initial roamdisk loading". Linux kernel is 4.13.0-32.generic.

As you can see, I have a very basic knowledge, any advice would be much appreciated.
Many thanks

---

### Post by oldfred on 2019-07-30
Moved to Ubuntu based sub-forum since not Ubuntu and we are not sure of changes.
Also not sure what your ppa installed which probably is part of issue.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by gabrieldar on 2019-07-30
Thank you very much.
Problem solved, there was a bug with snapd, solved with:
```

$ sudo apt autoremove --purge snapd

```

---

