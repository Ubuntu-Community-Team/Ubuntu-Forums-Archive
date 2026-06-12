---
title: "edit dansguardian.conf in ubuntuce 9.04"
date: 2009-09-30
forum: Ubuntu Christian Edition
---

### Post by cgar436 on 2009-09-30
How do I edit dansguardian.conf in ubuntuCE 9.04?  It appears that the file is owned by the Root and no edits can be made.  The file cand be edited in wordpad but changes cannot be saved.. Help!!

---

### Post by Dragonbite on 2009-09-30
You can run it as root by using sudo. Open a terminal and type ```
sudo gedit /path/to/the/file
``` or if you don't want to type all of that in then you can type ```
sudo nautilus
```at which point it will open up a Nautilus window with root privileges and you should be savable.

When you say "Wordpad", do you mean you are accessing it via Windows?  From Windows, I don't know how to increase my privileges on a Linux box.  Gedit is the default text editor in Ubuntu.

---

### Post by cgar436 on 2009-09-30
It should be said very new but yes it is Gedit.  Thanks

---

### Post by david_kt on 2009-09-30
> **Dragonbite said:**
> You can run it as root by using sudo. Open a terminal and type ```
sudo gedit /path/to/the/file
``` or if you don't want to type all of that in then you can type ```
sudo nautilus
```at which point it will open up a Nautilus window with root privileges and you should be savable.


For graphical application, we should use gksudo instead of sudo.
Please see explanation below:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

DK

---

### Post by Dragonbite on 2009-09-30
> **david_kt said:**
> For graphical application, we should use gksudo instead of sudo.
Please see explanation below:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

DK

Ok, so revised it would be ```
gksudo gedit /path/to/config/file
``` and ```
gksudo nautilus
``` I just keep forgetting the "gksudo" part.

Also, can't you just run it from Alt+F2? That way you don't have to keep a terminal window open (sorry,.. I'm in front of a Windows machine right now)

---

### Post by david_kt on 2009-09-30
> **Dragonbite said:**
> 
Also, can't you just run it from Alt+F2? That way you don't have to keep a terminal window open (sorry,.. I'm in front of a Windows machine right now)

Yes you can.

DK

---

