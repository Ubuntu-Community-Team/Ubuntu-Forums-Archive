---
title: "Resolution Problem - Ubuntu in Virtualbox"
date: 2009-12-09
forum: Virtualisation
---

### Post by bar338 on 2009-12-09
I'm attempting to install ubuntu in virtualbox.  View the image below to see my problem.  I would like to figure out how to get ubuntu to stretch to the full width of virtualbox.  Right now ubuntu is limited to 800x600 which doesn't look good on my 24'' monitor.

Thanks for your help.

Image:
[IMG]http://babbage.cs.missouri.edu/%7Ebar338/resProblem.png[/IMG]

---

### Post by argosreality on 2009-12-09
Click on System -> Preferences - Display and choose a resolution there

---

### Post by bar338 on 2009-12-09
The problem is that it only lists 2 resolutions: 800x600 and 640x480.  I'm running virtualbox off windows 7 where my resolution is 1900x1200 so my system is capable of much higher resolutions then the one ubuntu lists. How can i get it to realize that higher resolutions are possible?

---

### Post by fouadatmeh on 2009-12-09
You might need to enable the option "Auto Resize guest Display" option, so the guest resolution will remain the same as the window size..

---

### Post by kelvin spratt on 2009-12-09
You need to install guest additions for Linux 1st in vbox you will then be able to use full-screen mode. 
I don't think it will work in snapshot mode.

---

### Post by Dennis N on 2009-12-09
Installing Guest Additions

From the Devices Menu of the VirtualBox window:

```
Devices > Install Guest Additions
```

After the installer runs, you need to restart the guest os. Then you can resize the VB window, or run full screen with Rt-Ctrl+F. You also get seamless mouse integration, which means the mouse is not captured in the VB window.

---

### Post by krustybaguette on 2009-12-29
[QUOTE=kelvin spratt;8470397]You need to install guest additions for Linux 1st in vbox you will then be able to use full-screen mode. 

I've engaged full-screen mode but still only get 800x600 with either a black or white empty space surrounding it.

I've tried installing guest additions but get an error message stating 'file not found' plus which one do I install? 

I'm running VBox in Windows7 on Acer One netbook and Karmic Koala Desktop, although I have a second virtual disk with Ubuntu netbook remix. That second install wouldn't start the last time I tried to check it so I will probably chuck it since I prefer the desktop setup anyway.

I tried to edit the xorg.conf file and found nothing in it. I wonder if it wasn't generated during installation???? I have three variations of karmic images burnt on CDs...desktop, alternate, and netbook remix. Perhaps I could even find a Jaunty install disk around somewhere.

I really want Ubuntu to become my first alternative for most of my computing but I need to be able to use the full screen of my netbook since the 800x600 not only looks bad, it hides either the top or bottom of the desktop as well as part of one side or the other.

[COLOR="Red"]**[SIZE="3"]PROBLEM SOLVED[/SIZE]**[/COLOR]

Found the Virtual Box User manual in pdf format and followed seps 1-3 in section 4.4.1. Commands have to be executed in terminal as sudo but it was really quite painless and logical once I [[COLOR="Blue"]found the manual[/COLOR]]("http://download.virtualbox.org/virtualbox/UserManual.pdf") at download.virtualbox.org/virtualbox/UserManual.pdf 

Now I'm onto the next challenge...mounting my NTFS formatted external USB hard disk which I use for data storage.

---

### Post by Uncle Spellbinder on 2009-12-29
> **fouadatmeh said:**
> You might need to enable the option "Auto Resize guest Display" option, so the guest resolution will remain the same as the window size..

Exactly. I had the same 'problem' (looked just like the image above). Clicked the "Auto Resize guest Display" option and all was perfect.

---

