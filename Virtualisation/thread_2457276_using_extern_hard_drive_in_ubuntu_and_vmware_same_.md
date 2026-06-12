---
title: "using extern hard drive in ubuntu and vmware same time ?."
date: 2021-01-29
forum: Virtualisation
---

### Post by jackyjoy123 on 2021-01-29
Hello,


[COLOR=#000000][INDENT]Im running xp in vmware and i have a extern hdd with 500gb, so now i want to used that hard drive at the same time with Ubuntu and xp. I think sharing might be the solution but I dont know how I can do that, hope you guys can help me.

[https://krogerfeedback.nl](https://krogerfeedback.nl) [https://talktosonic.onl](https://talktosonic.onl) [https://talktowendys.vip](https://talktowendys.vip) [https://whataburgersurvey.onl](https://whataburgersurvey.onl)

thanks
jackyjoy[/INDENT]


[/COLOR]

---

### Post by CelticWarrior on 2021-01-29
Welcome.

Have you tried reading the VMWare documentation? It's surely helpful: [https://www.vmware.com/support/ws5/doc/ws_running_shared_folders.html](https://www.vmware.com/support/ws5/doc/ws_running_shared_folders.html)

---

### Post by ajgreeny on 2021-01-29
A shared drive is surely not the same as an external hard drive so if vmware is similar to Virtualbox I don't think it will be usable by both host and guest at the same time; it will be one or the other but not both.

---

### Post by CelticWarrior on 2021-01-29
> **ajgreeny said:**
> A shared drive is surely not the same as an external hard drive so if vmware is similar to Virtualbox I don't think it will be usable by both host and guest at the same time; it will be one or the other but not both.

It depends.
If one or more folders form the external HDD can be shared then it's sorta like using it on both at the same time. Location of the shared folders shouldn't matter. 
Of course, if we use the option to use USB devices in the VM, then the devices passed to the VM will be unavailable to the host system.

---

### Post by ajgreeny on 2021-01-30
Good point CW!

I was thinking more of the normal use of a USB external drive and the need to pass the USB hardware to the guest from the host.

---

### Post by Morbius1 on 2021-01-30
I do not use VMWare but this is what I do in VirtualBox:

I create a VirtualBox Shared Folder of my /media/morbius folder for that Windows VirtualBox guest.

I have it Auto-mount, give it a Mount Point label, and made it permanent.

When I boot the Windows VirtualBox guest Windows automatically assigns a "drive letter" with that Mount Point label and is visible in Explorer.

Any USB device I attach to the host will automatically appear under that drive letter / label in the Windows guest.

The host operating system will always be in control of the usb device.

---

