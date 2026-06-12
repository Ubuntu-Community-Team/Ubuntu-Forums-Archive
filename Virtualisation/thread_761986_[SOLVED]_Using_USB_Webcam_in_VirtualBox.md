---
title: "[SOLVED] Using USB Webcam in VirtualBox"
date: 2008-04-21
forum: Virtualisation
---

### Post by kestrel1 on 2008-04-21
I have got USB enabled in VirtualBox, but Windows XP does not recognise my Logitech Quickcam Connect Webcam.
I have installed the software for the cam, but Windows doesn't even detect the USB device.
Any advice on getting this working would be great.
Thanks

---

### Post by kestrel1 on 2008-04-22
bump

---

### Post by Mangust22 on 2008-04-23
did you install driver for linux? (web-camera is working fine in ubuntu?)

---

### Post by ajopaul on 2008-09-20
could someone tell me how was this solved ?

---

### Post by dragos_iliescu_2005 on 2008-11-24
You must to enable the usb before trying to use it in VirtualBox. For instruction on how to do that, refer to the following links:

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html")
[https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

---

### Post by jprather on 2009-06-25
This thread is improperly marked as [SOLVED] when it is clearly not.

The very first post clearly states that USB -IS- enabled.  Clearly the solution is not to enable USB.

A few minutes of googling will confirm for you that this is an ongoing issue with VirtualBox.  It does not handle most webcams.

[http://www.virtualbox.org/ticket/242](http://www.virtualbox.org/ticket/242)

The bug thread states:

"Actually the VBox EHCI controller (used for the USB 2.0 emulation) currently does not support isochronous transfers. Older webcams for USB 1.1 should work (we tested some in the past) but I admit that missing EHCI support will make many USB webcams currently unusable with VirtualBox."

There is still no ETA for a fix.

This thread should not be marked [SOLVED] as there was no solution mentioned which in any way solves the problem described in the initial post.

---

### Post by kestrel1 on 2009-06-26
Must admit I never bothered working on this any further, I have gone back to a dual boot system. I still use VBox, but mostly for trying out different Linux distro's now.
Not tried Windows & my webcam in the latest version of VBox, so it may even work.
Don't know who marked it as solved though. Not me. :-)

---

### Post by jprather on 2009-06-26
Most likely won't work on latest version.  I'm using VBox 2.2.4, and it still doesn't work.

There appear to be lots of people who want this to work, but I haven't been able to figure out how much attention VBox is giving to this, other than aknowledging the lacking functionality.  They offered no ETA, but that doesn't mean it isn't being looked into.

---

### Post by aniketvb on 2009-07-09
Upgrade to virtual box v3 . I just did that on my fedora 11 box and the yahoo messenger in the windows XP VM is able to use the webcam. EHCI is finally properly implemented now in Vbox.

---

### Post by jprather on 2009-07-10
Yup, seems that some people still having problems which may be another issue between some specific webcam drivers (apple iSight?) and the vbox video drivers, but many, including myself, now have our windows guests happily using the webcams which are hooked up to our ubuntu host systems.

Don't forget to upgrade your guest additions!

---

### Post by Kunin on 2009-07-25
I have a Logitech E3500, it works under Ubuntu 8.10 fine, but Virtual box (V3) sees it as an unrecognized device so it doesn't work.

---

### Post by scatha on 2009-10-27
Hello :)

Trying to run an IDS uEye Camera under windows 2000/XP in VirtualBox - it is recognized properly by the camera manager (meaning USB works correctly), but the live image won't display- however a friend got it running under VMWare. I've been trying this in VBox versions from 1.6.x up to 3.0.8 - same result: camera is recognized and initialized but grabbing doesn't work. Could be a DMA issue alright!

---

### Post by styven on 2009-12-06
Hi all,

I to am havin problems getting a logitech webcam pro 5000 to be used in xp as a guest on top of linux mint. The tickbox to access the device is greyed out in Virtualbox devices tab.
I have installed the xp drivers in the guest OS. From experience you need to unmount usb devices in the host, but I can't umount the webcam. This I think is the reason that I can't get it to show in XP.
Any ideas.
Steve.

---

### Post by kestrel1 on 2009-12-06
> **styven said:**
> Hi all,

I to am havin problems getting a logitech webcam pro 5000 to be used in xp as a guest on top of linux mint. The tickbox to access the device is greyed out in Virtualbox devices tab.
I have installed the xp drivers in the guest OS. From experience you need to unmount usb devices in the host, but I can't umount the webcam. This I think is the reason that I can't get it to show in XP.
Any ideas.
Steve.
Are you using the latest version of VBox & got the guest additions installed on XP?

---

### Post by Ginsu543 on 2009-12-06
I run Windows XP using VirtualBox 3.0.12 and it recognizes my HP Deluxe webcam just fine once I mount it in Devices --> USB Devices. I didn't have to do anything special; it just worked "out of the box" for me.

---

### Post by jocampo on 2010-03-12
> **styven said:**
> Hi all,

I to am havin problems getting a logitech webcam pro 5000 to be used in xp as a guest on top of linux mint. The tickbox to access the device is greyed out in Virtualbox devices tab.
I have installed the xp drivers in the guest OS. From experience you need to unmount usb devices in the host, but I can't umount the webcam. This I think is the reason that I can't get it to show in XP.
Any ideas.
Steve.

HI Steve

did you fix this problem? same cam here, no recognized...Vbox 3.0 with XP Pro as guest and Jaunty as host ...

---

### Post by kestrel1 on 2010-03-13
Personally I would start a new thread if you are having problems as Virtual box has moved on a fair bit since the last post. Do you have the latest version?

---

### Post by areteichi on 2010-03-13
I was able to fix the greying out issue of USB devices by adding my user name in Ubuntu to the group 'vboxusers'.
You can do this by going to:
System > Administration > Users and Groups > Manage Groups (authentication required)
and adding yourself by checking your username in the group named 'vboxusers'.

However, I am still not able to get my webcam to work in Virtualbox as the guest Windows XP does not recognize my camera as Logitech Quickcam for Notebooks Deluxe and so I cannot install the driver.

---

### Post by Francewhoa on 2010-12-01
The following works for me. Using Ubuntu 8.04 LTS, Virtualbox 3.2.10, Windows XP, Skype 4

[LIST]
[*]Close your skype in Ubuntu
[*]In VIRTUALBOX 3.2 select the Windows XP on the left side column
[*]Right click on Windows XP
[*]Select AUDIO
[*]Under HOST AUDIO DRIVER select the appropriate Ubuntu driver. In my case ALSA.
[*]Start virtualbox with Windows XP
[*]On the top left side of the Virtualbox/Windows XP window click on DEVICE > USB DEVICES > [YOUR WEBCAM NAME HERE]
[*]Windows XP will display a message saying "New device found"
[*]Wait a few seconds. Windows is installing the webcam driver.
[*]Open Skype. Navigate to OPTIONS > VIDEO SETTINGS
[*]Test your webcam. If successful you should see yourself
[*]If the person you're calling can't see your video then click TURN OFF your webcam. Then TURN ON webcam. The person you're calling might have to accept your video.
[*]Performance are really good
[/LIST]

---

