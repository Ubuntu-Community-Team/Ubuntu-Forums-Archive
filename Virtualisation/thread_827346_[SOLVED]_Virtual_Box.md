---
title: "[SOLVED] Virtual Box"
date: 2008-06-12
forum: Virtualisation
---

### Post by Drakkor on 2008-06-12
Yeah, I can't seem to find the video drivers for Windows 2000 Pro. I went through some driver agent sites, and one of them had VirtualBox grahics adapter, but I can't find that. Any help gladly appreciated.  :)

---

### Post by p_quarles on 2008-06-12
Moved to Virtualization. 

You don't need any video drivers. The virtualized graphics card used by VirtualBox is very basic, and Win2K should handle it without any configuration. For full resolution, you will need to install the VirtualBox Guest Extras package, though.

---

### Post by Drakkor on 2008-06-12
Any idea where to find the "VirtualBox Guest Extras" package, I have v. 1.5.4 , there were mouse problems with the new version. :)

---

### Post by p_quarles on 2008-06-12
Under the "Machine" menu in the toolbar, there is an option to download and install the Guest Extras.

---

### Post by Drakkor on 2008-06-13
Yeah,I don't have that option on my version, I found something in the help section about editing my xorg.conf,but that didn't work either. :confused:

Section "Screen"
        Identifier    "Default Screen"
        Device        "VirtualBox graphics card"
        Monitor       "Generic Monitor"
        DefaultDepth  24
        SubSection "Display"
                Depth         24
                Modes         "2048x800" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by p_quarles on 2008-06-13
> **Drakkor said:**
> Yeah,I don't have that option on my version, I found something in the help section about editing my xorg.conf,but that didn't work either. :confused:
Yes you do. It's under the machine menu for the running machine's window, not under the VirtualBox control panel's menu. There is no version without this.

---

### Post by Drakkor on 2008-06-13
Oh,ok,I found it,lol, but when I click on it nothing happens ! About ready to give up on this 2000, I got XP working fine with VB.

---

### Post by trdc on 2008-06-13
Try starting again. Go to the Devices menu, click Unmount CD/DVD-ROM and verify that it unmounted correctly. Then go back to Devices, click on Mount CD/DVD-ROM then click CD/DVD-ROM Image, highlight the VBoxGuestAdditions.iso and click Select. Go to My Computer, open up your CD Drive and then hopefully you will be able to install them by running the VBoxGuestAdditions.exe file.

---

### Post by Drakkor on 2008-06-13
Hooray !! :) Finally got it,lol Thanks, trdc that did the trick,here's 
windows 2000 in full screen,with great graphics !!

---

