---
title: "How to Enable USB Devices in Virtualbox"
date: 2011-01-06
forum: Virtualisation
---

### Post by peterthegeek on 2011-01-06
I'm trying to connect my iPod to Virtualbox, but it isn't showing up. I've tried installing Guest Additions and have added myself to the vboxusers group. USB Devices isn't showing up in the vm's settings, nor is it showing up in the menu. Any ideas on what's wrong?

-Peter

---

### Post by marl30 on 2011-01-06
> **peterthegeek said:**
> I'm trying to connect my iPod to Virtualbox, but it isn't showing up. I've tried installing Guest Additions and have added myself to the vboxusers group. USB Devices isn't showing up in the vm's settings, nor is it showing up in the menu. Any ideas on what's wrong?

-Peter
Try to log out of Ubuntu then sign back in. If that doesn't work. Install VirtualBox 4. I believe it has better USB support than the older versions. [http://www.webupd8.org/2010/12/install-virtualbox-40-stable-in-ubuntu.html](http://www.webupd8.org/2010/12/install-virtualbox-40-stable-in-ubuntu.html)

---

### Post by howefield on 2011-01-06
What version of VirtualBox are you using ?

If it is version 4 from the VirtualBox site, have you installed the extension pack ? (different to guest additions)

---

### Post by peterthegeek on 2011-01-06
Thanks for the replies.

About an hour ago I read in another thread that VB OSE doesn't support USB devices, so I installed VB 4. It detected the iPod fine, but Windows Vista wasn't any different.

---

### Post by kevxh on 2011-01-06
Download the version from their website and check you have virtualbox permission, it let's you run it even if you don't but the usb screws up.
Open Users and Groups, click on advanced, then user privileges and check virtualbox

The version in the repositories is garbage.

---

### Post by peterthegeek on 2011-01-06
I checked it, and it is selected. Also, it is the version from their website.

---

### Post by peterthegeek on 2011-01-06
I just looked under Device Manager, and it lists "Apple Mobile Device USB Driver". When I click on it, it says:

> This device cannot start. (Code 10)

Click 'Check for solutions' to send data about this device to Microsoft and to see if there is a solution available.

---

### Post by Matadewa on 2011-01-07
> **howefield said:**
> What version of VirtualBox are you using ?

If it is version 4 from the VirtualBox site, have you installed the extension pack ? (different to guest additions)

i used virtualbox version 4, and i already install extension pack too 
but my usb still not active. . .
how to fix it?

---

### Post by sdowney717 on 2011-01-07
are you using a long extension cable for the usb ipod hookup?
oddly, I found if I plug an ipod in with a 6 foot extension cable, it is not working.
But if I plug it in without the extension it works fine.

that extension cable works with anything else I plug into it.

---

### Post by peterthegeek on 2011-01-07
No, I'm just using the cable that came with it. When I install the drivers it says they weren't properly installed. Could it be an issue with Windows?

---

### Post by therieb on 2011-01-15
I was having the same problem, using Virtual box 4, extension added, users and groups permissions set correctly.  I found the answer here:

[http://ubuntuforums.org/showthread.php?t=1622404&highlight=virtualbox+usb](http://ubuntuforums.org/showthread.php?t=1622404&highlight=virtualbox+usb)

I followed "Diametric's" advice and opened Virtual Box with sudo from the terminal:

sudo virtualbox

I had to reconfigure the virtual machine I was using, but after that it worked.  No idea why I would need to sudo the program after having changed the permissions for my group, but if it works it works.  

Also, I noticed that the usb 2.0 extension doesn't load properly unless you save it somewhere and then import it from within Virtual Box.  Hope that helps.

---

### Post by vidtek on 2011-01-17
> **Matadewa said:**
> i used virtualbox version 4, and i already install extension pack too 
but my usb still not active. . .
how to fix it?

I had this problem with my swimming pool controller and solved it here [http://ubuntuforums.org/showthread.php?t=1661697](http://ubuntuforums.org/showthread.php?t=1661697)

Enable the usb device using extensions and additions as well.

Make sure the host system isn't accessing the device in any way,
 i.e. no tsr's or little programmes running in the background.

Then run the install software that came with the device in the virtualbox system, that should work.

Tony.

---

