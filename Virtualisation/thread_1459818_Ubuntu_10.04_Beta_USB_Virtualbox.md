---
title: "Ubuntu 10.04 Beta USB Virtualbox"
date: 2010-04-21
forum: Virtualisation
---

### Post by afz12 on 2010-04-21
I recently upgraded to Ubuntu 10.04 64 bit and installed Virtualbox for U9.10 (10.04 isn't ready yet) and it runs fine except it doesn't see the USB port despite previous settings. Is there a command I should use?

---

### Post by awam66 on 2010-04-24
Yes I have the same problem, I get this message from Virtualbox:> Could not access USB on the host system, because neither the USB file system (usbfs) nor the DBus and hal services are currently available. If you wish to use host USB devices inside guest systems, you must correct this and restart VirtualBox.
The USB Proxy Service could not be started, because neither the USB file system (usbfs) nor the hardware information service (hal) is available.
I don't know what to do next, so also looking for help.

---

### Post by Morons on 2010-04-30
[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

Seems to work

---

### Post by manco on 2010-04-30
> **afz12 said:**
> I recently upgraded to Ubuntu 10.04 64 bit and installed Virtualbox for U9.10 (10.04 isn't ready yet) and it runs fine except it doesn't see the USB port despite previous settings. Is there a command I should use?
I think I might know the problem.

[From the VirtualBox PUEL Edition Guide:]("http://ubuntuforums.org/showthread.php?t=1074160")

> III. Add User(s) to the "vboxusers" Group

Go to System &#8594; Administration &#8594; Users & Groups. Unlock "Users Settings" using the "Unlock" button near the lower right of the box (next to the close button) then click on “Manage Groups”

Scroll through the list of group names until you find “vboxusers” then click on it to highlight and click on the “Properties” button. You'll see a list of users on your system. Check off all the users who you will want to give access to VirtualBox. Do NOT check off “root”. After you've made your changes, click "OK" and then close groups settings and user's settings.

A reboot should not be required. Simply log out, and then back in. If you get an error when you try to start your guest OS, then go ahead and reboot and then try again. Leave a message on this thread if you find that you need to reboot before you are able to run your virtual machine so that I can change the instructions.
BTW, you're not running the OSE, right?
I just installed 10.04 and I want to get the PUEL version of VirtualBox running (and run 64-bit OS' on it)

---

