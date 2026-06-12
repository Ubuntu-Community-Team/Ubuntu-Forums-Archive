---
title: "Errors when trying to install Virtualbox guest additions"
date: 2015-09-11
forum: Virtualisation
---

### Post by AbleTassie on 2015-09-11
I am using Lubuntu 14.04.3 LTS and have Virtualbox 5.02 installed. I am running Windows XP as the guest operating system. It seems to work well, but there are two problems: 1) Windows does not sense the USB ports and 2) I also cannot drag and drop between the Host (Lubuntu) and guest (Windows).  I am aware that Installing guest additions is important for both of these two functions. I installed 5.02 Guest additions, (both types the 3D experimental using safe mode and the regular). 

But when I do the installation of Guest Additions I get two error messages about Guest additions software not passing the Windows logo test, one error message has to do with mouse and pointing device software for Virtualbox, the other error message has to do with Virtualbox Graphics Adapter; see 2 attached screenshots below. I installed the Guest Additions software in spite of the error messages.

Even after the installation of the guest additions, I cannot drag and drop. When I try to drag and drop Windows aborts; yes the drag and drop feature is enabled. I tried it enabled host to guest and bidirectional and it does not work.

Windows also does not seem to sense the USB ports, for example a printer connected to the USB port is not sensed by the Windows install wizard, despite the fact it is supposed to sense a printer connected to the USB. If you click on My Computer in Windows, under "Devices with Moveable Storage" you see an icon labeled "Virtualbox Guest Additions (D: )."

Is there any way to get the drag and drop features working? Or to get Windows to sense the USB ports?

Thanks,

Able

[ATTACH=CONFIG]264357[/ATTACH][ATTACH=CONFIG]264358[/ATTACH]

---

### Post by v3.xx on 2015-09-12
I find your screenshots confusing.  It looks as if you have windows (MS) as a host and not Lubuntu.

---

### Post by AbleTassie on 2015-09-13
No, in fact Lubuntu is the host and Windows is the guest. The screenshots were taken to record the two error type messages when trying to install Virtualbox Guest Additions for Windows as guest.

Thanks,

A.

---

### Post by AbleTassie on 2015-09-16
I was able to get a satisfactory solution to this problem by activating the shared folders system. This allows folders and files to be shared between the host and guest. Instructions on how to do this are given under "4.3 Shared Folders" in the Help Section of Virtualbox. If I had not been able to do this, the only way to share files between the host and guest would have been via the internet--a real pain. I will mark this thread as SOLVED.

:p):P

A.

---

