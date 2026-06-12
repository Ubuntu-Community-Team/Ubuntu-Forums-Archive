---
title: "Virtualbox Guest Toolbars missing in Unity (Ubuntu 11.10)"
date: 2011-12-28
forum: Virtualisation
---

### Post by vedovatti on 2011-12-28
Hi guys,

I have been searching and I didn't find anyone speaking about his problem I have so I need a little bit of help.

I have a Guest Windows XP on my Ubuntu OS. I have been upgrading my Ubuntu since 8.04, including Virtualbox and guest OS. Now I have Ubuntu 11.10 and Virtualbox 4.1.8 (including Guest Additions installed and extra pack, all in correspondent version).

My problem is that the toolbar and menus are missing since Unity on the Guest OS (I attached a screenshot). On the Menu bar of Unity is empty and toolbar are not there anymore. So I can't basically choose to plug USB (that's my main problem). On the other hand, I have to say that from the performance and integration works like charm.

Does anybody knows how to solve the problem?

Thanks

---

### Post by howefield on 2011-12-28
Try rolling the mouse down onto the middle of the XP taskbar, you should get a pop up menu from which you can select USB Devices amongst other options, as per attached screenshot.

You should get this mode whenever you use Full Screen or Seamless mode with the VM.

---

### Post by howefield on 2011-12-28
Just to add that the VirtualBox Mini Toolbar should show as 1 pixel high on the bottom of the screen. Mouse needs to be on it to make it show.

The settings for the Mini Bar can be found in the main settings screen for your VM - General > Advanced tab.

---

### Post by vedovatti on 2011-12-28
Thanks howefield for your fast reply.

In fact, I have the Mini toolbar option added on the options of the Virtual Machine. Before Ubuntu 11.10 I used to have it on the top of the screen. Just that after upgrading to Unity (and Virtualbox version) it disappeared.

It is just not there. :confused:

---

### Post by Perryg on 2011-12-28
The mini toolbar seems to have a mind of its own sometimes.  Have you tried the host+home hotkey to see if it opens the menu for you?

---

### Post by vedovatti on 2011-12-28
That did the trick.

It seems that the Virtual Machine kept a misconfiguration from the display resolution not appropriated to the new Unity environment.

Using Right control (host hotkey) + F worked!. In the beginning it broke the XP display. But just a hard restart on the Virtual Machine and everything solved.

Thank guys.

---

### Post by sujith_s80 on 2012-01-08
Hi,

In my Dell laptop (Host OS-Windows 7) ,I have installed the Virtualbox 4.1.8 and installed ubuntu 11.10 inside the virtualbox.Installation was OK but I have some display issues.The ubuntu is not showing properly.I have enabled the 3D acceleration and also I have installed the guest additions.But still my display is not showing properly.In linux I can see two desktop portions.The desktop is showing small but I can see the background picture again.

Kindly help.

---

### Post by vedovatti on 2012-01-08
Hi there,

I really cannot help you as the problem you describe is the complete opposite of the one I had. In your case Windows is host and Ubuntu is guest.

Try to post it in the [https://forums.virtualbox.org/](https://forums.virtualbox.org/) to see if you could get some help ther or open a new threat.

Good luck.

---

