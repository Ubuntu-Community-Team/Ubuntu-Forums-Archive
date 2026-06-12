---
title: "Ubuntu 2204 sever installation issue"
date: 2023-09-01
forum: Server Platforms
---

### Post by vinod1989 on 2023-09-01
Hello all,
Recently I have tried to install ubuntu2204 with usb stick. After the basic installation and reboot a system , system was not booting from hard drive. It was  booting from usb stick to install os again.  How do we unmount usb drive After reboot a system and make it boot it from hard drive After basic installation

---

### Post by guiverc on 2023-09-01
After you finish install, you're asked usually  to reboot, and on most hardware told to remove the installation media which means the usb-stick isn't there to boot from after the  reboot.

Whilst I'm aware some ISOs don't show the remove media message on all hardware (*desktop ISOs anyway as that's what I mostly use sorry*), when the machine is rebooting is when you can remove your installation media. If you want to be safe, just shutdown the box, remove media & boot it without the installation media installed. 

I'd expect the installed system will boot, once the installation media is removed.

You didn't provide any architecture or hardware details, ie. 22.04 for *armhf *(32-bot), *arm64*, *amd64, ppc64el, riscv64, s390x* etc

---

### Post by scorpking2 on 2023-09-01
You might have to change the boot order of your devices in the BIOS if you would like to leave the USB plugged in during boot.

---

### Post by vinod1989 on 2023-09-01
It's amd and it was showing errors like "unmount failed /cdrom/ due to device busy" and automatically detecting usb stick again  after the reboot. If we remove usb stick and reboot  the system by using ctrl+alt+delete , then it was going to boot from hard drive. But this issue happing while installing ubuntu2204 server version only. So I'm expecting here is i don't wanna remove my usb stick any more till end and system should boot from hard drive After basic installation. 
Kindly please suggest me something here to fix it, thank you in advance

---

### Post by vinod1989 on 2023-09-01
I think not required. For ubuntu2004 sever installation,  we are not facing this type of issue without changing any BIOS setting. I don't know why it's happing to ubuntu2204 only

---

### Post by MAFoElffen on 2023-09-02
I just ignore...

I get that with both Physical flash drives and with ISO files if i am using an ISO file as the device. Both the images are read only... I don't care about them at this point, and out of about 15 to 20 thousand Linux OS installs, I have never had a problem at "that point"... I just try to ensure I get "to that point" before rebooting or shutting down the device.

---

