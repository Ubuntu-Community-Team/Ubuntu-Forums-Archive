---
title: "Installation of Windows7 in Virtual Box Hangs"
date: 2011-10-15
forum: Virtualisation
---

### Post by gateway67 on 2011-10-15
I'm trying, in vain it seems, to install 64-bit Windows 7 as a guest OS on my Ubuntu 11.04 system.  I have chosen to experiment with VirtualBox OSE, and although it seems like a fantastic product, I cannot seem to enjoy it because Windows 7 fails to completely install its software.

So, I'm at the stage where Windows 7 is "installed", however during the post-installation stage, the setup stage stalls when the system is attempting to install the Dritek Launch Manager (whatever that is); please refer to the screen shot that I have attached.

Is there a way to skip this phase of the installation?  Perhaps it is possible to boot into safe-mode, or something like that?  I must confess that I'm not an expert with Windows, thus even if going into safe-mode is possible, I would not know what to do next.

P.S.  Info about my system:  Gateway, Intel I5 processor, 4GB RAM, running 64-bit Ubuntu 11.04 (Natty), and with VirtualBox OSE 4.0.4.

---

### Post by CharlesA on 2011-10-15
How are you installing Windows? That doesn't look like the usual windows 7 installer.

---

### Post by gateway67 on 2011-10-15
> **CharlesA said:**
> How are you installing Windows? That doesn't look like the usual windows 7 installer.
When I first acquired my PC (laptop), the first thing I did after powering it up, was to make Factory Default Discs ( using 3 DVDs).

Immediately afterwards, I "waxed" the system to install Ubuntu.  Following that, I installed VB, then created the appropriate configuration for installing Windows 7 as a guest OS.  I was able to use the Factory Default Discs to get Windows 7 installed, however the issue I have now is that the Windows installation stalls when attempting to "setup the system for the first time".

It appears thus far that I have no choice but to go through this first-time setup, and there's no obvious way to abort the operation, so that I can actually see the Windows 7 desktop.

---

### Post by CharlesA on 2011-10-15
Ok, that's what I figured. I don't know if you'll be able to set up Win7 in a VM using the restore cds, since those are tied to the hardware of the machine they are from.

---

### Post by gateway67 on 2011-10-15
> **CharlesA said:**
> Ok, that's what I figured. I don't know if you'll be able to set up Win7 in a VM using the restore cds, since those are tied to the hardware of the machine they are from.
I'm on the same system from which the Restore CDs (RCD) originated from; I just prefer Linux over Windows, and thus I chose to use Linux as my primary OS.

I don't know if it will make a difference or not, but the computer manufacturer just notified me that the RCDs that I made are defective!  I don't know how they know that, but I was told that new RCDs will be sent to my residence.  Thus I will have to wait for another 10 days (till I receive the new disks) to see if I can succeed with the installation of Win7 as a guest OS.

Thanks for your replies.  I realize now that the issue my system is having is beyond the realm of Win7, and more related to 3rd-party software.

---

### Post by CharlesA on 2011-10-15
The thing is that the virtual machine is not the same as the physical hardware you are running. That's probably why it is having problems.

---

