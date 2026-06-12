---
title: "ubunutu 12.04 secret touchpad tap"
date: 2013-05-09
forum: The Cafe
---

### Post by layers on 2013-05-09
I discovered this completely by luck - when you mark a text, and you tap the upper right corner of the touch pad, it pastes it (eventough you havent copied it)

where can i find more of these little cranks of 12.04?

---

### Post by pqwoerituytrueiwoq on 2013-05-09
the top left of hte mousepad is mouse button 0, no idea what that is for but is is different
nice find, btw that is middle click not paste, it is like clicking with the wheel on your mouse

nrv it is "is_hint 0" what ever that is

---

### Post by layers on 2013-05-10
dude, and lower right is right click.
i'm on fire!

and why do i feel like everybody else knew these, just no one told us?

---

### Post by layers on 2013-05-10
> **pqwoerituytrueiwoq said:**
> the top left of hte mousepad is mouse button 0, no idea what that is for but is is different
nice find, btw that is middle click not paste, it is like clicking with the wheel on your mouse

nrv it is "is_hint 0" what ever that is

yeah, when I click on text that I'm editing with top left, the cursor doesn't go there. I wish I knew what it did.

---

### Post by pqwoerituytrueiwoq on 2013-05-10
> **layers said:**
> yeah, when I click on text that I'm editing with top left, the cursor doesn't go there. I wish I knew what it did.i guess we could bind it to a compiz function, maybe open dash or window picker or something

---

### Post by mikewhatever on 2013-05-11
> **layers said:**
> I discovered this completely by luck - when you mark a text, and you tap the upper right corner of the touch pad, it pastes it (eventough you havent copied it)

where can i find more of these little cranks of 12.04?

It's a property of the synaptics touchpad driver - pretty common in laptops, and not really related to Ubuntu. 
There are four variables for four corners: RTCornerButton, RBCornerButton, LTCornerButton, LBCornerButton. 
Each can take the value of 0,1,2,3, which stand for disable, left click, right click, middle click.
The top right corner is usually assigned the 3 - middle click value, and the bottm right 2 - right click, while the left corners are disabled.
You can change those, for example, to assign left click to the bottom left corner, try **synclient LBCornerButton=1**.

PS: If you like reading long manuals, take a look at **man synaptics**

---

### Post by Copper Bezel on 2013-05-12
> **mikewhatever said:**
> It's a property of the synaptics touchpad driver - pretty common in laptops, and not really related to Ubuntu. 
There are four variables for four corners: RTCornerButton, RBCornerButton, LTCornerButton, LBCornerButton. 
Each can take the value of 0,1,2,3, which stand for disable, left click, right click, middle click.
The top right corner is usually assigned the 3 - middle click value, and the bottm right 2 - right click, while the left corners are disabled.
You can change those, for example, to assign left click to the bottom left corner, try **synclient LBCornerButton=1**.

PS: If you like reading long manuals, take a look at **man synaptics**

Should be noted that synclient settings are non-persistent and reset on reboot or resume from suspend. However, you can create a script using synclient and have it run at exactly those times by setting its path in dconf as the "hotplug command." Navigate to org.gnome.desktop.settings-daemon.peripherals.input-devices and enter the path for your script (such as /home/username/.trackpadsettings.sh).

---

