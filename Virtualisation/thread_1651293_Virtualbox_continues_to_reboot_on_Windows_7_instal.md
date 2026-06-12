---
title: "Virtualbox continues to reboot on Windows 7 install"
date: 2010-12-22
forum: Virtualisation
---

### Post by superheavy on 2010-12-22
TL;DR VirtualBox never gets to the installation view, it just keeps loading and rebooting.

Hello Everyone,
  I am trying to install a Windows 7 guest on an Ubuntu 10.04 host, both systems are 64-bit ( AMD-N950 Quad ).  I have installed VirtualBox before, but this time its different.  During the installation, the "Loading Windows Files" screen comes up, then the animation appears as well as the "Starting Windows" text.  After that, the virtualbox screen goes to a grey background.  It then resizes the window, and goes back to the Virtualbox splash screen. 
This cycle repeats ad-nauseam.  Does anyone know what I should do in terms of finding out where the problem is ?  I have attached the log file in a zip file.

Thanks for your help.

---

### Post by superheavy on 2010-12-23
Turns out I was using the recovery disk supplied by HP.  During installation it checks to see if it is running on the correct HP hardware.  If that check fails, it kicks the bucket.

---

### Post by dino99 on 2010-12-23
is that with latest 4.0 from Oracle ?

---

### Post by nonlinearly on 2011-02-05
I have the same problem but I tried to set a virtual machine with windows 7 from my laptop Toshiba satellite recovery DVD that I had previously created.
The installation procedure was ok. But every time windows starts and the desktop appear then after 2 sec I have restart... and again and again...
I have virtualbox 4.0.2 on ubuntu 10.0.4
I am not a fun of open source solutions for many reasons but I decide to give a try... But this is the result. And now? How can someone convince me for the opposite? 
(Not to mention that for 2 hours that I have installed ubuntu I often have problems)

Thanks

---

### Post by CharlesA on 2011-02-05
Normally you can't install Windows on a virtual machine by using a recovery cd.

---

### Post by nonlinearly on 2011-02-05
Thanks. Thanks for finally confirming my fears for open solutions ... And you know why? Because VMware all play just fine ... Good bye open source and if you see me again ... my hammer

---

### Post by CharlesA on 2011-02-05
> **nonlinearly said:**
> Thanks. Thanks for finally confirming my fears for open solutions ... And you know why? Because VMware all play just fine ... Good bye open source and if you see me again ... my hammer
That has nothing to do with open source software. It's due to running a recovery cd.

In any case, you whatever works for you.

---

### Post by nonlinearly on 2011-02-06
Ok... I take it back... The reason that works in vmware it has nothing  with vmware... The procedure from dvds recovery takes long long time...  with many restarts.. so much that makes you think there is a problem (let well Microsoft is not giving the dvd of windows 7 with the purchase of laptop and need to make a dvd recovery...)
&#921; left it accidentally run (I forgot it) on vmware and when I came back I saw it al-right. And so I thought the fault was the virtualbox. But when I gave the same time to virtualbox  all went well.
 Thanks and I apologize for the bias.

---

### Post by slooksterpsv on 2011-02-06
> **nonlinearly said:**
> Ok... I take it back... The reason that works in vmware it has nothing  with vmware... The procedure from dvds recovery takes long long time...  with many restarts.. so much that makes you think there is a problem (let well Microsoft is not giving the dvd of windows 7 with the purchase of laptop and need to make a dvd recovery...)
&#921; left it accidentally run (I forgot it) on vmware and when I came back I saw it al-right. And so I thought the fault was the virtualbox. But when I gave the same time to virtualbox  all went well.
 Thanks and I apologize for the bias.

Good deal, I know my **Gateway** recovery DVDs won't work in virtualbox, it looks for specific items. So I've had to use my Windows 7 family pack DVD to get Windows 7 loaded on VirtualBox. It tells me that it can only restore on an **Acer** computer (yes I said Gateway Recovery DVDs, but it looks for Acer hardware, I think Gateway is a branch of Acer or they stole Acer's code).

---

