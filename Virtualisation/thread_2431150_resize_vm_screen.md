---
title: "resize vm screen"
date: 2019-11-12
forum: Virtualisation
---

### Post by mechanic on 2019-11-12
My Xubuntu install is a VM running under VirtualBox on a Windows host. The guest additions package is installed. The choice of display screen sizes does not include the native 2560x1440 of the screen, and if I select 'full screen' under the VB settings bar, all I get is a blank screen - fortunately the system recovers when I reverse the selection.

How to get a full-screen display from this Xubuntu?

---

### Post by lammert-nijhof on 2019-11-13
Try pressing Right-CTRL + F or look in the Virtualbox menu belonging to the Guest Window, select View + Full-screen Mode!
Don't use the Xubuntu Display function.

---

### Post by ajgreeny on 2019-11-13
-It will also be useful to know which versions of both the Virtualbox application and the Guest-Additions you have installed; they must both be exactly the same version for them to work properly together.

It may also be worth trying the different display graphics controllers in the Display tab of the machine settings; I understand VMSVGA is now the default for Linux guests, though at present some of my Linux guests also seem to work well on VBoxSVGA.

Try them one by one to see if one of them works but the others don't.  Interestingly, the default display setting when creating a VM does not appear to be the one needed for best graphic output.

---

### Post by mechanic on 2019-11-14
Thanks for the hint re graphics controller, that made a difference! Although the full screen doesn't work properly, I now can use the 'adjust screen' mode (Host + a) to get the window covering the whole screen. Pressing Host+f shows the window across the full screen but then the mouse dissapears! Still that's an improvement on the setup previously so I can live with that.

There was a message on screen about updating guest additions but that went away before I could really take in the content. Updating/upgrading the system seems to have affected the virtualbox-guest packages though. And rather suprisingly the fonts seem un-affected by the changes in screensize whereas I was half expecting them to be distorted.

---

### Post by ajgreeny on 2019-11-14
Normally in a Linux host, when you open the VirtualBox manager application it will tell you if the guest additions are outdated and offer to download and install them; accept that offer.  If you do not get that when your host OS is Windows I am not sure that I can help any further as I do not run Windows any more except as a VM. 

I still believe you should update the guest-additions to get the best from your VMs, so see what happens if you go to the Devices menu at the top (or maybe the bottom of the full screen) and click on "Insert Guest Additions CD Image".

That may add the guest additions CD as a virtual disk which you can find in the file manager of your VM.  If it does you can open that CD in file manager and drag/copy the ***VBoxLinuxAdditions.run*** into a terminal and run it with sudo.

---

### Post by mechanic on 2019-11-17
Yes, updating the guest additions package (reported as moving from 6.0.10 to 6.0.14) and repeating the install method using the VB guest install virtual cd improves things still further; now I have a pretty full screen Voyager distro running as a VM under Win10. I'm seriously wondering if I have this the wrong way round and I should run a Xub host with Windows as the VM.

The only tricky part so far is in the mounting of the GA virtual CD, this didn't happen automatically so I ran - as root - 'mount /dev/cdrom /media'.

Thanks for the help!

[Note added later] I'm not convinced that this update to the GA did in fact enable this function to work; a later installation of the Voyager 18.04 vm but before the GA were updated to 6.0.14 now works with a full-screen (host + f) setting on this monitor (2560x1440) mouse pointer an' all!

---

