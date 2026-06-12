---
title: "[SOLVED] Virtual Box USB  - Windows Guest"
date: 2008-12-24
forum: Virtualisation
---

### Post by jdpearson on 2008-12-24
Ok, so I have Intrepid and I've gotten Virtual Box installed and loaded my XP machine.  I've finally found out how to edit fstab to get USB support inside VirtualBox.  However, I can't seem to get my drive mounted.   When I plug it in Intrepid recognizes the drive, but not my XP guest.

What am I missing?

If I choose USB Devices from the VirtualBox menu it shows the drive, but it is greyed out.

---

### Post by nhasian on 2008-12-24
you have installed the guest addons?  did you install the new Virtualbox 2.1?

[http://ubuntuforums.org/showthread.php?t=1015045](http://ubuntuforums.org/showthread.php?t=1015045)

---

### Post by lkraemer on 2008-12-24
Have you enabled the USB for the Virtual Disk Image (VDI), and
created a filter?  If not, you must do this also.  Then you can
plug in the USB Flash Drive and Right Click on the USB Icon in
the lower Right Toolbar to Enable the Device, and XP should be
able to access it.  If you enable it and still can not access it,
try disabling it, Removing the USB Device, and Re-insert and
re-enable it.  Sometimes I have to do the process twice.  Can't
say what causes it, but it does happen for me at random times.
And like the previous message, make sure that Guest Additions is
loaded.  Ref The VirtualBox Web site FAQ for other info also.

lkraemer

---

### Post by jdpearson on 2008-12-24
> **lkraemer said:**
> Have you enabled the USB for the Virtual Disk Image (VDI), and
created a filter?  If not, you must do this also.  Then you can
plug in the USB Flash Drive and Right Click on the USB Icon in
the lower Right Toolbar to Enable the Device, and XP should be
able to access it.  If you enable it and still can not access it,
try disabling it, Removing the USB Device, and Re-insert and
re-enable it.  Sometimes I have to do the process twice.  Can't
say what causes it, but it does happen for me at random times.
And like the previous message, make sure that Guest Additions is
loaded.  Ref The VirtualBox Web site FAQ for other info also.

lkraemer


Thanks for the prompt replies gang.  First, I did install 2.1 so I'm good there.  I've also installed the guest additions.  

lkraemer:  I did figure out how to make a filter and I actually see the USB device in the lower right toolbar and under the VirtualBox devices menu, it's just grayed out so I can't select it.  Later on I'll try more than just this device.

---

### Post by bodhi.zazen on 2008-12-24
Moved to virtualization.

There are instructions on how to enable USB devices in the mega thread at the top of these forums.

---

### Post by jdpearson on 2008-12-24
> **bodhi.zazen said:**
> Moved to virtualization.

There are instructions on how to enable USB devices in the mega thread at the top of these forums.

Thanks!  I'll give that a try as those directions are much clearer than what I've found before.

Finding the answer is so often a result of the quality of one's Search Fu!

Thanks for the help!

---

### Post by jdpearson on 2008-12-25
Ok, still not working.

I can successfully create a filter and it even appears with the name of the device.  However, the option to select the device is still grayed out.

---

### Post by bodhi.zazen on 2008-12-25
Did you remount the usb file system, log out and back in, or reboot after configuring ?

---

### Post by jdpearson on 2008-12-25
> **bodhi.zazen said:**
> Did you remount the usb file system, log out and back in, or reboot after configuring ?

Yup, after today's reboot it works.  Thanks.  I had rebooted after making changes to my config files, but not after making the filters for Virtualbox, which seems to have done it.

Thanks again.

---

