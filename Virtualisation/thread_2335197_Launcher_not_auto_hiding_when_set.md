---
title: "Launcher not auto hiding when set"
date: 2016-08-26
forum: Virtualisation
---

### Post by greg-dance on 2016-08-26
I am fairly new to Ubuntu 16.04 and have fresh installed it in Virtualbox 5.1.4 r110228 (Qt5.5.1) the latest version to date.
I also installed all updates for it.

It runs fine except the launcher strip on the left side is a problem because when opening the file manager and some other apps they open with their left edge hidden behind it and cannot be dragged to the right to make their closing and nin/max buttons visible.

So I went into settings and set the launcher to auto hide but it fails to do this.

So 2 mysteries please for you patient folk, why don't the windows allow dragging to the right and why doesn't the launcher auto hide?

Many thanks

---

### Post by howefield on 2016-08-26
Do you have guest additions installed, which includes improved graphics drivers iirc.

Also not a solution, but windows can be dragged with Alt + left mouse click and drag.

---

### Post by greg-dance on 2016-08-26
Thanks Howefield for the Alt-left mouse tip. That works though as you say its not a fix.

I can't find the 'guest additions' you mention in the Ubuntu Software App, is there another way to find it please?

---

### Post by howefield on 2016-08-26
From memory, select *Insert Guest Additions CD Image* from the Devices menu, the rest *should* be self explanatory. The installation should start automatically.

---

### Post by ajgreeny on 2016-08-26
Just as a "heads-up" I had big problems with displays and the things that the Guest extensions usually makes work in VBox 5.1 and quickly went back to VBox 5.0 which works much better for me.

It might be worth seeing if your problem goes away with 5.0.

Where did you get the VBox package?

---

### Post by greg-dance on 2016-08-26
I don't know what vbox is and haven't been able to find it on my system in system settings or installed progs so maybe its not installed?

---

### Post by ajgreeny on 2016-08-26
> **greg-dance said:**
> I don't know what [COLOR="#FF0000"]vbox[/COLOR] is and haven't been able to find it on my system in system settings or installed progs so maybe its not installed?
Sorry, that is just my own shortcut for virtualbox to save my (very bad) typing.
**5.0.26-108824~Ubuntu~trusty** is what it is short for in my case.

---

