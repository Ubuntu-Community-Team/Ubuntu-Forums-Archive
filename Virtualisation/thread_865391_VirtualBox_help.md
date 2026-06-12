---
title: "VirtualBox help"
date: 2008-07-20
forum: Virtualisation
---

### Post by nssone on 2008-07-20
I have installed VirtualBox and and trying to install XP to it. But when I do I keep getting this error popup:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Any clue? I tried install all the modules listed in Synaptic so... what could possibly be wrong here?

---

### Post by Vitamin-Carrot on 2008-07-20
Wot versio of ubutnu are you running?

Where did you get Vbox from?

I ask these as its a common problem after a kernel update the vbox available in add\remove tends to throw up that error but downloading the application again from the actualy website tends to fix it.

It also means that you as the user may not be part of the vboxusers group.

*Linkies*
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by HotShotDJ on 2008-07-20
> **nssone said:**
> Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic.Have you tried the fix given in the error message?

---

### Post by nssone on 2008-07-20
I tried to install it all through synaptic. I know my account is part of the vboxusers group already, I just checked it.

---

### Post by nssone on 2008-07-20
I keep getting this now?

VirtualBox kernel driver cannot be opened.
VBox status code: -1911 (VERR_VM_DRIVER_OPEN_ERROR).

Well, what I did was create the /dev/vbixdrv folder. Now I get that. I don't get why nothing's being installed properly.

---

### Post by no_silhouette on 2008-07-20
> **nssone said:**
> I have installed VirtualBox and and trying to install XP to it. But when I do I keep getting this error popup:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Any clue? I tried install all the modules listed in Synaptic so... what could possibly be wrong here?

I did the same thing and installed all the modules listed, now when I turn on my computer, it wont go past the loading bar moving accross the screen. Or when I select what kernal I wish to run from start, I now have a long list of them and my wireless is gone. I have tried loading all of them but still the same thing. I tried to uninstall but they are still there. What do I do now???

---

### Post by HotShotDJ on 2008-07-20
> **no_silhouette said:**
> I did the same thing and installed all the modules listed
:shock:

ALL the modules LISTED??  I'm surprised you get as far as you do in the boot process.  Please REMOVE all the modules listed (one at a time).  You'll probably have to do it using the command line in recovery mode.  Now, just install the **_ONE_** that applies to your system.

---

### Post by orangeworx on 2008-08-05
i'm having this same problem too and like nssone, i've created the folder and i'm getting the same error msg: 
VirtualBox kernel driver cannot be opened.
VBox status code: -1911 (VERR_VM_DRIVER_OPEN_ERROR).
i believe i loaded the generic driver. i'm not that knowledgeable in ubuntu but i have common sense...


thanks for any help guys

---

