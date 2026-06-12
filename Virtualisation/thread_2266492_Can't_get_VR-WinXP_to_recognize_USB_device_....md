---
title: "Can't get VR-WinXP to recognize USB device ..."
date: 2015-02-23
forum: Virtualisation
---

### Post by Rick St. George on 2015-02-23
Have latest UbuntuStudio running on 8 core processor with plenty HD space. Also running WinXP in Oracle VirtualBox.

Trying to use a USB scanner, but V-Box is not recognizing anything plugged in via USB.
In the VR Mgr I see USB and "enable USB controller" is checked. 
Added one filter, but don't know what good that does as it is blank (don't know what to put in it).

Any help would be appreciated.

Thanks!
Rick

---

### Post by coldraven on 2015-02-23
You need to install the VirtualBox Extension Pack for USB support
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by TheFu on 2015-02-24
Check my reply to the other USB 2 thread in this sub-forum. There are links with instructions.

---

### Post by Rick St. George on 2015-02-24
Hi Fu, 

I have the ext. pak, but in the USB settings - "Enable USB 2.0 (EHCI) Controller" is greyed out.
So is "Enable USB Controller", but it is checked. And I have a filter, but nothing filled in as it doesn't make sense.
I remember following MastaBlasta recomendation (following your links) when I installed end of Dec. 2014. I added
the Key, then used Software Center to add VBox. Is that the PPA you mention? I believe I downloaded the deb file
first, but it didn't seem to work or want to install.

As for Update and Upgrade, I rely on Ubuntu to automatically update. Are you saying we should manually update Vbox?
I am runing Vbox v4.3.20, and am confused what to do next to get the USB recognized.

---

### Post by TheFu on 2015-02-24
If the hostOS has "grabbed" the USB device, it cannot be used by any guest.  Please review the links back to the virtualbox.org website.  You may need to blacklist the hostOS driver for the USB device.  lsusb on the host should provide that information.

---

### Post by Rick St. George on 2015-02-24
This is it;
"Bus 005 Device 003: ID 0461:0371 Primax Electronics, Ltd Visioneer Onetouch 8920 Scanner"

Maybe its as simple as AddUser, will try .... maybe I have to reboot Vbox.  Nope - but I did notice, the "Enable USB 2.0 Controller" was not greyed out.
When I clicked on it, it showed an Error Msg. at the bottom. "Need to add Ext. Pkg." Thought I had it installed, but think I had confused "Guest Additions", with the Ext. Pkg. ?!?!?  Am trying to get the Ext Pkg. and will post back.

---

### Post by Rick St. George on 2015-02-24
Worked ! ! !  After add Ext. Pkg. for v4.3.22, then Reboot entire computer.
in Vbox WinXP identified the USB device. Added it, then WinXP added it.
Now can Access USB OneTouch 8920 scanner with PaperPort software.

Thanks a Million Fu!
Rick

Posting as Solved.

---

