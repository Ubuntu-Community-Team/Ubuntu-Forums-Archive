---
title: "Is my Kubuntu VM borked?"
date: 2009-01-16
forum: Virtualisation
---

### Post by MoebusNet on 2009-01-16
Kubuntu 8.10 (guest) in VirtualBox 2.0.6 (with Guest Additions installed) on Ubuntu 8.04.1. The last set of updates for Hardy resulted in a messed-up desktop for Kubuntu.

Kubuntu is running, X is running but no taskbar on the desktop. The desktop can't be resized to fit the screen and full-screen doesn't reveal the lower taskbar either. When updates have messed up my VM's before, I was able to reinstall Guest Additions to straighten up the VM. This time, I can't get to Terminal in the guest to reinstall the Guest Additions. Trying to get to a VT drops me back to the host OS.

Any suggestions before I have to reinstall K8.10VM?

(see attached screenshot)

---

### Post by Dedoimedo on 2009-01-16
Hello,

Try the following, in the descending order:

Try booting guest in the safe graphic mode.
Try booting with acpi=off added interactively to grub entry.
Try alt+f2 to launch commands; when prompt appears, write terminal and then try to get things done, including VB Guest Additions.
Try reconfiguring xorg.conf or resetting to defaults.
Try reinstalling VB driver.
Try reinstalling VB.

Dedoimedo

---

### Post by MoebusNet on 2009-01-17
**[SOLVED]**
Thanks, I'll try your suggestions!
EDIT - Being pretty much of a command-line idiot, I didn't have much luck with your suggestions; I just don't know enough yet.
WARNING - This will be kinda long-winded. Don't say I didn't warn ya!  ;)

What did work for me was a lot of fumbling around in the GUI to find Konsole (Terminal). When I used Ctrl-F to use Fullscreen mode and fished around in the bottom-left hand corner of the desktop, I was able to pop-up the menu that allowed me to select Kate. My next issue, following the directions in VirtualBox Help, was that after: BEGIN CODE cd /media/cdrom0  sudo sh ./VBoxLinuxAdditions-x86.run END CODE
I got the error message "unable to open ./VBoxLinuxAdditions-x86.run" When I checked for the contents of cdrom0, it showed empty, even after telling the VM to mount VBoxGuestAdditions.iso. I wound up shutting down the guest OS, mounting the .iso in "Settings" then booting Kubuntu 8.10 guest again. I selected "Devices>Install Guest Additions" (for about the 6th time it seems) even thought the cd image did not appear on the desktop. In Kubuntu, the cd image did not appear in "/media/cdrom0" even though it showed up in "Computer>Removable Storage". After opening Kate (again) as described above, the Help File commands from above still didn't work. 
WHAT DID WORK:
BEGIN CODE sudo /media/cdrom0/VBoxLinuxAdditions-x86.run END CODE

---

