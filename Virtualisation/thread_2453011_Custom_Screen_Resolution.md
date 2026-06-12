---
title: "Custom Screen Resolution"
date: 2020-11-01
forum: Virtualisation
---

### Post by Quarkrad on 2020-11-01
Just installed my first kvm running on my Ubuntu Mate 20.04 machine.  I have installed a win10 guest and all is fine except the screen resolution.  The display resolution of the win10 desktop is 1920 x 1400 but I have a scroll bar on the right on my virt manager window because the win10 window is too large.  The actual size of the screen of the virt manager window is 1900 x 935.  I have started to look at setting a custom resolution but, as I'm new to this, I'm discovering many many new worlds, and not sure where to start going deeper and/or if I'm on the right track.  I'm looking forward to getting into Spice, QEMU, etc but this is going to take (me) sometime. Any pointers to help with this screen resolution issue would be appreciated.  I am going to install a ubuntu guest next and assume I'm going to have the same problem re the scroll bar as the resolutions do not match.

---

### Post by ajgreeny on 2020-11-01
If I remember correctly I simply right-clicked on the Win-10 desktop and from the Personalise option managed to set the display resolution in my KVM Win-10.  However, I am almost completely out of date with Windows now and I can not be certain about how I set the resolution, and the machine with KVM Win-10 is not available at present

Apart from when I make changes to, for example, the USB redirection settings which need the virt-manager menu, I run all my VMs at full screen meaning I can easily set the guest resolution to the native resolution of my monitor or laptop screen.
The virt-manager window size is going to vary, of course, if you maximise or resize the window, so why not use fullscreen except when you need something from the host OS.

I use SSH to view or use any files from the host in the guest which I find much easier than setting up shared folders as I used to in VBox

---

### Post by Quarkrad on 2020-11-01
Thank you - I did try full screen but to be honest I find it useful having visibility of my host machine via the top tool bar.  If it is possible to change the resolution I would like to go down that path.  It seems in the (non kvm - native) win environment one can make a custom resolution but it involves the native graphics driver - in this case (kvm) the win10 Display Adapter is Red Hat QXL Controller.  I'm hoping that it is possible to config a file somewhere that enables one to set up a custom resolution.

---

### Post by ajgreeny on 2020-11-01
Sorry but I can't really help with that any more.
As I said, Windows in any form other than XP, the last version I used properly, is a bit of a mystery to me these days; I probably feel the same as many new Linux users feel, it's  all Greek to me, to quote Shakespeare!

---

### Post by Quarkrad on 2020-11-02
So are we going down the track that this is a Windows issue rather than a config setting in the visualisation environment (kvm/Spice/QEMU, etc)?  I will continue to pursue.

---

