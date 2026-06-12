---
title: "Suddenly, Gimp won't let me edit anything!"
date: 2008-12-17
forum: Ubuntu Studio
---

### Post by skullmunky on 2008-12-17
Using Gimp 2.4, in Hardy Heron.  Suddenly, I can't edit anything in Gimp.  All the drawing tools have no effect, the Fill tool has a little "No!" icon attached to its cursor, I can't select anything ... this is with brand new documents and also when I open different existing files.  Help!  How did I break it?

---

### Post by babarosa on 2008-12-17
Did you change the rights for accessing the program?

Remedy: 
For example, uninstall it either using synaptic or at the terminal "sudo ap-get remove gimp"

Get the newest gimp 2.6.2 for hardy from "www.getdeb.net" (the default site shows software for intrepid, change it to show software for hardy!).

Hope then it works fine again.

Regards, Michael

---

### Post by skullmunky on 2008-12-17
thanks, I'll try that.  Gimp 2.6 in Hardy??  Excellent!

---

### Post by skullmunky on 2008-12-30
Gimp 2.6 from getdeb works great.  Surprisingly the "No Editing" problem persisted.  

I deleted the .gimp preferences folder, and that fixed it.

---

### Post by RockOut on 2009-12-27
I am having the same problem. I'm on Karmic Koala. One day, I opened GIMP and suddenly I can no longer edit images using any tool in the toolbar.

I CAN open files and view them, but I can't change any image using any tool. About 4 weeks ago, I tried and failed to install a Wacom Bamboo tablet. Could this have anything to do with the problem? (My mouse works just fine with GIMP.)

I tried... Completely Removing GIMP via 1) Synaptic Package Manager 2) Via Ubuntu Software Center and 3) via the Terminal using both "Remove" and "Purge" commands with apt-get.

I considered deleting the GIMP Preferences folder, as was the successful case for the Original Poster Skullmunky, but I can't find the GIMP Preferences folder in the file system. I searched for it, and it didn't come up. I did find all the other GIMP program folders though.

HELP!?! This is driving me insane. I am considering reinstalling Karmic Koala in order to get my GIMP working.

---

### Post by skullmunky on 2009-12-29
the .gimp folder is in your home folder; it's invisible.  In Nautilus I think the command is "Ctrl+H" to show hidden files and folders; in Dolphin you can turn it on I think from the View menu or similar.

---

