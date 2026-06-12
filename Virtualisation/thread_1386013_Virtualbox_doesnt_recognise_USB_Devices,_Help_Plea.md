---
title: "Virtualbox doesnt recognise USB Devices, Help Please"
date: 2010-01-20
forum: Virtualisation
---

### Post by Nightstrike2009 on 2010-01-20
Hiya everyone 

I have Virtual Box 3.1.2 running Windows Xp in Ubuntu 9.04, but I have a problem.

My VirtualBox is a .deb downloaded from [http://www.virtualbox.org/]("http://www.virtualbox.org/") and called 
virtualbox-3.1_3.1.2-56127_Ubuntu_jaunty_i386.deb

When I select the USB filter icon, bottom right of active virtualbox window I have:

Sandisk U3 Titanium [0200]                Greyed Out
Logitech USB-PS2 Optical Mouse [2200]     Greyed Out
Logitech Gaming Keyboard [070)            Greyed Out
G15 Keyboard [0103]                       Greyed Out
Canon Canoscan [100]                      OK
HUAWEI Technology HUAWEI Mobile           Greyed Out
i.Tech Dynamic BlueCON U2 [3164]          Greyed Out
HVR900H [0069]                            Greyed Out.

Also Windows Xp doesn't see any USB drives or Firewire drives in my computer.

I need at least the following to be functional for it to be of use to me:
Sandisk U3 Titanium [0200]                Currently Greyed Out
HUAWEI Technology HUAWEI Mobile           Currently Greyed Out

Can anyone please help me with this?

---

### Post by thatguruguy on 2010-01-20
Are you using the OSE version? It doesn't support USB.

Use the closed-source version from [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by thatguruguy on 2010-01-20
EDIT:  Sorry, I obviously didn't read your post.

Did you install the Guest Additions?

---

### Post by Nightstrike2009 on 2010-01-20
Its ok thanks for trying to help I am a relative noob myself though have been using ubuntu for over a year now so picking up quickly by diving in head first at everything. LOL

---

### Post by thatguruguy on 2010-01-20
More importantly, are you a member of the vboxusers group?

Here's a link to some helpful info:  [http://www.virtualbox.org/manual/UserManual.html#usb_linux](http://www.virtualbox.org/manual/UserManual.html#usb_linux)

---

### Post by thatguruguy on 2010-01-20
Even more helpful info: [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by Nightstrike2009 on 2010-01-20
I have fixed this problem now after a few searches on the internet it seemed to be a problem with usergroup setups anyhow here is my guide so new people don't have to suffer this annoying problem.

> BY Nightstrike2009:
FIXING USB SUPPORT IN UBUNTU VIRTUAL BOX

1)On Ubuntu 9.04 go to Administration>Users & Groups
2)Click &#8220;Unlock&#8221; button and type in root password on request.
3)Click &#8220;Manage Groups&#8221; button after your password has been accepted.
4)On the &#8220;Groups Settings&#8221; Screen, Scroll down and highlight &#8220;vboxusers&#8221;, double click on its name & Check the box in front of your username, then click &#8220;OK&#8221;.
5)Close &#8220;Vboxusers group properties&#8221; window, by clicking &#8220;OK&#8221;, then close &#8220;Groups Settings&#8221; and &#8220;User Settings&#8221; windows by clicking &#8220;Close&#8221; button.
6)Either log out and log back into Ubuntu 9.04 or reboot it, you should now be able to use your USB devices.

ADDING & DISABLING USB DEVICES IN VIRTUAL BOX

1)On Ubuntu select Applications>System Tools Sun Virtual Box.
2)In right pane (Information) scroll down to until you see a small USB icon with &#8220;USB&#8221; in blue text at its side, click the blue &#8220;USB&#8221; text.
3)Check both boxes for &#8220;Enable USB Controller&#8221; and &#8220;Enable USB 2.0 (EHCI) Controller&#8221;.
4)At the right side of &#8220;USB device filters&#8221; there is a little usb icon with a green add sign (this adds new usb devices).
5)After you have finished adding usb devices, check the boxes at the left side of all usb devices you wish to use.
6)NOTE: I had to disable the USB/PS2 mouse driver on my pc as it wasn't letting me use the mouse.

And that's it it works :-)

---

### Post by shank21101985 on 2010-10-12
thanks a ton.. it worked :D

---

### Post by Revjohn on 2010-10-28
I have done all of these things... and I still have my USB Greyed.  

Looking to access my ScanDisk Memory Stick.  

I see it... it registers as the right stick, but it is still grayed.

Does the fact that I am running Kubuntu change anything?  I have edited Groups in the KUsers as well as the other one mentioned above.

Thanks!

John

---

