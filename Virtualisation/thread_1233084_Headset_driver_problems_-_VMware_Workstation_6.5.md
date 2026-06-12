---
title: "Headset driver problems - VMware Workstation 6.5"
date: 2009-08-06
forum: Virtualisation
---

### Post by syntic on 2009-08-06
I'm using a VOIC over IP Client (Swyx), which just works on Windows. Firstable i got the message, that the guest operating system (XP pro) can not load the driver, because the host system (kubuntu) uses it. After this 
I solve this problem by modprobe -r snd-usb-audio. 

But now I even not possible to load the driver for the headset because i get the message that the host system is using the usbhid, as you can see in the screenshot in the attachement. 
I think it is the mouse driver and i shouldn't delete it from the host system... ????

Nevertheless, as you can see in the other screenshot, the headset is shown under the removeable devices in the VM-settings.

Any ideas what could i do next? 

Thank you very much.

greetings
syntic

---

