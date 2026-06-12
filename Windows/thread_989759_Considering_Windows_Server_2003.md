---
title: "Considering Windows Server 2003"
date: 2008-11-21
forum: Windows
---

### Post by RealG187 on 2008-11-21
I am trying to go all Linux. I installed  Ubuntu on my Laptop and did not leave a partition for Windows like I did when I installed Ubuntu on my IBM machine. I am still leaving IBM as my only Windows machine and I am thinking of playing around with Windows Server 2003. However, on [this page]("http://support.dlink.com/products/view.asp?productid=WUA-2340#drivers") there is no driver for Windows 2003. Could I use a WUSB54G?

---

### Post by K.Mandla on 2008-11-22
Moved to Windows Discussions.

---

### Post by Snappo on 2008-12-11
I installed windows 03 in the past on a viao, the XP drivers worked fine.

---

### Post by HermanAB on 2008-12-11
Win2003 runs fine on VMware and on Virtualbox on Ubuntu and when you do that, it is independent of the hardware so the drivers are no problem at all - it installs in a VM with no sweat.

Cheers,

Herman

---

### Post by RealG187 on 2008-12-11
I need to install Windows directly without VM. This will be my only Windows machine in case I need it.

---

### Post by d2globalinc on 2008-12-11
:S go with XP over 2k3 - whats the point of the server stuff if your not going to even be using it?  As for windows servers - we haven't ran one on bare metal hardware for over 3 years now.  Virtualize em - they suck for managing hardware, and when they freeze up and die you can reboot them or power em down with virtualization.  The linux host OS continues to remain solid and we have those servers running for over a year non-stop and no reboots.  Windows servers we tend to have to reboot once a month or more to get them back to their best performance.. Some we just have reboot daily :S to avoid the calls in the early AM all together.

Virtualization is your friend, and its where windows belongs until its phased out all together when software developers start making software appliances for virtualization where they can control their environment and sell to PC's, Macs, Windows all with the same code and without interference from whatever else the user has installed on their machine.

Ahh the future looks bright! Oh wait - its already here.

Shane Menshik
D2 GLOBAL INC
[http://www.d2global.com](http://www.d2global.com)

---

### Post by RealG187 on 2008-12-12
Virtualization makes the system requirements go up so I can't do that in my case.

---

### Post by Nessa on 2008-12-15
> **RealG187 said:**
> I am trying to go all Linux. I installed  Ubuntu on my Laptop and did not leave a partition for Windows like I did when I installed Ubuntu on my IBM machine. I am still leaving IBM as my only Windows machine and I am thinking of playing around with Windows Server 2003. However, on [this page]("http://support.dlink.com/products/view.asp?productid=WUA-2340#drivers") there is no driver for Windows 2003. Could I use a WUSB54G?

Bit confused. The model you gave is for a Linksys Wireless Adapter yet the website you checked out is D-link (a different company). Nevertheless, I checked the Linksys website and there is no driver for Win2003 either.

---

### Post by RealG187 on 2008-12-16
I know the WUSB54G is Linksys. I am saying I have two adaptors and was asking since the Dlink apppers not to work w/ 2003 I was asking if my Linksys would. Sorry for the confusion there.

---

### Post by HermanAB on 2008-12-17
Virtualize!  As a previous poster said, Windows hardware support is bad.  The result is that Windows works a lot better in a Linux hosted VM than natively on the hardware.  Your hardware requirements do not go up appreciably when using a VM, unless you want to run multiple VMs.  A single Windows VM runs at close to native speed.

Once you have made the jump to virtual systems you will never look back and you'll wonder why you haven't done so years ago already.

Cheers,

Herman

---

### Post by RealG187 on 2008-12-17
I think Windows hardware support would be better, my printer doesn't work with Linux. That's partly why I still need windows.

---

