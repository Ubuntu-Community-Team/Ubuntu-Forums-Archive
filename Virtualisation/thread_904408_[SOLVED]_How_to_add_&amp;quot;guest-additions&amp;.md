---
title: "[SOLVED] How to add &amp;quot;guest-additions&amp;quot; in Virtual Box from command line?"
date: 2008-08-29
forum: Virtualisation
---

### Post by randykelli on 2008-08-29
I'm stuck in VB WinXP with Ubuntu as the host.  Does anyone know how to install "guest-additions" from the command line? This way, in theory, my mouse which is frozen in WinXP limbo should be freed to go out of VB from WinXP to the lovely land of plenty known as Ubuntu.    ](*,)

[And BTW, my right control key will NOT get me out of VB, thus the reason for the post.]

---

### Post by Shazaam on 2008-08-29
Do you have the Guest-Additions iso mounted in the XP vm and does the keyboard work in the vm? You might be able to use the "Tab" button to navigate around in XP.

---

### Post by randykelli on 2008-08-29
> **Shazaam said:**
> Do you have the Guest-Additions iso mounted in the XP vm and does the keyboard work in the vm? You might be able to use the "Tab" button to navigate around in XP.

No, I don't have the Guest-Additions iso mounted in the XP vm.  Yes, the keyboard and everything else works fine in the vm WinXP, with the exception of the right CTRL key not letting me out into Ubuntu.

---

### Post by Shazaam on 2008-08-29
Ok. Shut down the XP vm (Start>Shutdown). Go to Settings for your XP vm, then "CD/DVD-ROM" and check "Mount CD/DVD Drive". Check "ISO Image File" and make sure "VBoxGuestAdditions.iso" is in the box, then hit OK. This will mount the .iso on the XP desktop (or in My Computer).
Open the .iso and you will find an .exe for Guest-Additions.
Once you have it mounted if you want to try inside the XP vm open a dos prompt then type in the filename including the full path then hit enter.

---

### Post by randykelli on 2008-08-30
Thanks for the tip.  I did get the VB WinXP to install guest additions from the .iso file.  In my system, the path to the .iso is /usr/share/virtualbox, just in case someone else needs it.  The system rebooted, but unfortunately, a VB dialog box on 'mouse pointer integration' came up with my mouse frozen on top of it. :( 

Seems as though the host Ubuntu freezes.  I can sense a functional "shadow mouse" under the frozen dialog box in the VB well enough to shut down the VB WinXP to escape to Ubuntu.  The problem persists.  Any other suggestions to make this mouse work correctly?

---

### Post by randykelli on 2008-09-02
I figured out the problem!!  Hopefully, this will help someone else save many hours of work.  In my case, I went to the virtual box details and clicked on USB.  I noticed that I had a filter for USBPC2 installed.  I uninstalled it and now everything is coming up roses!   :popcorn:

---

