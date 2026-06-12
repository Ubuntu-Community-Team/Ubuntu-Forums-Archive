---
title: "PCI to USB card freezes my Dell Latitude C510/C610"
date: 2008-05-20
forum: Windows
---

### Post by stephenbrazier on 2008-05-20
[I]Hey,
I have a Dell Latitude C510/C610 and a NEC PCI to USB card. When i put my wireless adapter into it (Wireless-G U2KG54L) It shows that a new device has been connected. However, after a couple of seconds EVERYTHING stops. I cant turn on the CAP locks, move my mouse, and my system stops COMPLETELY. Yet, when i remove the PCI card, everything continues.

Very Rarely, it connects without problem.

It has also happened when i had linux as my OS.

I am using Windows XP Profession SP3 now.

Hence, it doesnt seem to be a OS problem.

Thankyou loads,

Stephen.[/I]

---

### Post by dca on 2008-05-20
Sounds like a kernel panic in both 'ntoskrnl' and linux from using incorrect drivers...  Or possibly the drivers for the PCI-to-USB host controller versus the device itself...
 
In Windows go to the device manager and make sure there are no exclamation points indicating missing driver files for any host controllers...  Make sure the driver for your device is also the latest.

---

### Post by stephenbrazier on 2008-05-21
> **dca said:**
> Sounds like a kernel panic in both 'ntoskrnl' and linux from using incorrect drivers...  Or possibly the drivers for the PCI-to-USB host controller versus the device itself...
 
In Windows go to the device manager and make sure there are no exclamation points indicating missing driver files for any host controllers...  Make sure the driver for your device is also the latest.

[I]All checked, No exclamation points, question marks, big evil red X's... alls in order...
Im not 100% sure its latest; I did check by clicking update driver. However, It said a better one couldnt be found (using Windows Updates)

Thankyou for you time,

Stephen :) [/I]

---

### Post by rickyjones on 2008-05-21
> **stephenbrazier said:**
> [I]All checked, No exclamation points, question marks, big evil red X's... alls in order...
Im not 100% sure its latest; I did check by clicking update driver. However, It said a better one couldnt be found (using Windows Updates)

Thankyou for you time,

Stephen :) [/I]

Did you check the manufacturer website for a more up-to-date driver?

---

### Post by stephenbrazier on 2008-05-21
> **rickyjones said:**
> Did you check the manufacturer website for a more up-to-date driver?

[I]Thankyou for your help. It was, in fact, the USB card requiring extra powering as it could not manange internet without a powerlead connected  :S.

I send everyone who helped by posting a thankyou.

:) 

Stephen.[/I]

---

