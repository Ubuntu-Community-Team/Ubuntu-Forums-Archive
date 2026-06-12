---
title: "Virtualbox : Bluetooth unavailable"
date: 2008-06-27
forum: Virtualisation
---

### Post by msayed2004 on 2008-06-27
Hi everybody;
I want to use the Bluetooth from my guest XP (on Virtualbox).

I added it via the USB section of settings but when I start the machine the Bluetooth does not appear in the devices list (of XP), clicking on the USB icon on the statusbar and hovering upon the Bluetooth entry I see a tooltip with some info including that the device is unavailable :( , how can I fix this & make it available for my guest ?

Host : Hardy
Guest : Win XP SP3
VBox : 1.6.2

THANKS :D

---

### Post by sadohert on 2008-06-28
I would love to know the answer to this too.

---

### Post by msayed2004 on 2008-07-04
> **sadohert said:**
> I would love to know the answer to this too.
BUMP
---
I guess we need to make Ubuntu see the Bluetooth & prevent any app/service from using it.
---
I disabled the Bluetooth device management service but no luck, any ideas please ?

---

### Post by pieeater3142 on 2008-07-07
hey, would also love to know the answer to this  as i installed virtualbox so i could run ms outlook and i'm used to syncing my contacts etc with my phone.
Any ideas anyone?

---

### Post by turezky on 2008-07-25
Bump!

---

### Post by Skerit on 2008-07-27
bump again!

Basically we just need a simple button which allows us to disconnect a usb device, that is ALL!

I know we could also use eject /dev/<name of device> but I have no idea what the name of my device is!

---

### Post by distobj on 2008-08-07
Bumpity bump bump!  I'm having the same problem.

---

### Post by arkashkin on 2008-08-08
me 2  !

---

### Post by Skerit on 2008-08-14
Hmm, I can't even synch my phone over USB with the windows software because somehow linux is hogging it!

---

### Post by turezky on 2008-09-04
Maan, this thread looks dead :(
The issue is still there.
Today I downloaded and installed brand new VirtualBox 2.0 (btw, thanks virtualbox devs for giving repository back :) ) but it didn't solve the problem.

So, for the second time... BUMP!!!

---

### Post by binbash on 2009-01-17
bump, i have same problem at the moment

---

### Post by cufo on 2009-07-04
Hello,
as written at 

[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)
[B]Linux hosts
[/B]

USB: if you are having trouble accessing USB devices in a guest, make sure that you are a member of the **vboxusers** system group. 

So
1. just make sure you are a member of a vboxusers group[INDENT](System>Administration>Users and Groups>Unlock>"password">Autheticate>Manage groups>vboxusers>properties>[Tick desired user]>ok>close>close)
[/INDENT]2. then add to your virtual machine new USB filter with your bluetooth device[INDENT](Machine must be powered off>[Right click]>Settings>USB>Enable>Enable USB 2.0>Add Filter From Device button>[Your bluetooth device, for example Broadcom BCM2045B]>OK>[Start machine])
[/INDENT]3. in quest OS install proper drivers for your device the usual way[INDENT](Bluetooth device will appear as new hardware)

[/INDENT]Hope that works :-)

---

### Post by zivley on 2009-07-12
> **cufo said:**
> Hello,
as written at 

[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)
[B]Linux hosts
[/B]

USB: if you are having trouble accessing USB devices in a guest, make sure that you are a member of the **vboxusers** system group. 

So
1. just make sure you are a member of a vboxusers group[INDENT](System>Administration>Users and Groups>Unlock>"password">Autheticate>Manage groups>vboxusers>properties>[Tick desired user]>ok>close>close)
[/INDENT]2. then add to your virtual machine new USB filter with your bluetooth device[INDENT](Machine must be powered off>[Right click]>Settings>USB>Enable>Enable USB 2.0>Add Filter From Device button>[Your bluetooth device, for example Broadcom BCM2045B]>OK>[Start machine])
[/INDENT]3. in quest OS install proper drivers for your device the usual way[INDENT](Bluetooth device will appear as new hardware)

[/INDENT]Hope that works :-)

I was hoping this will help me too, but unfortunately this solution didn't work for me...
I have a Lenovo Thinkpad X61 with Ubuntu 9.01 Jaunty Jackalope and Virtualbox 3.0 and I'm trying to use the Bluetooth inside a Win XP SP3 guest, I can't believe this can't be done! I've also read that in the later versions of Virtualbox the USB filters work fine without needing to add anything to /etc/fstab nor needing to add your username to vboxusers which is taken care during VirtualBox installation, so what is the problem???
I'll keep trying and will post an update if I find the way to make this work.

---

### Post by zivley on 2009-07-12
OK guys, I've got it finally working!!!

If there are some that have been waiting for this too long as myself, here's the way I solved it:

[http://ubuntuforums.org/showpost.php?p=7603235](http://ubuntuforums.org/showpost.php?p=7603235)

Hope this helps

---

