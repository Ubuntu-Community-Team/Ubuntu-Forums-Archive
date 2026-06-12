---
title: "Server Install Problem... Keyboard not working??"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Skyflyer4life on 2012-04-17
Ok... feel like an idiot for even having to ask about this here... but I've been trying to install Server 12.04 for the past 6 hours and can't seem to figure out how to get it installed.  The problem is with the keyboard I believe but I'm not certain.  Either booting from the CD or the USB drive... I start the installation just fine... boot from CD lets say, Grub comes up, I select "Install Ubuntu Server" everything good so far until the next screen.  "Select Language"  ... stuck.  Keyboard no longer working.  Try to hit enter for "English" but I'm just stuck at this page.  I'm using a Logitech K400 wireless USB keyboard with ASUS P8Z68V-LX board.

Does anyone have any suggestions for a work around?  I don't have an old school keyboard laying around.. .looked everywhere and Wal-Mart only has wired USB boards which wouldn't help either (I believe).  Any help would be MUCH appreciated!

(This is so embarrassing)

---

### Post by Skyflyer4life on 2012-04-17
SOLVED

Found a 15 year old PS/2 style keyboard in box in the basement.  Yeah!  Menu navigation is working!

---

### Post by NHclimber on 2012-04-17
Feel free to go 'me too' this bug [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/975198](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/975198)
Make sure to update the title to: 'alternate & server iso missing hid-logitech-dj driver'

Also, you should go here [http://iso.qa.ubuntu.com/qatracker/milestones/204/builds](http://iso.qa.ubuntu.com/qatracker/milestones/204/builds) and indicate that the specific server iso failed (scroll down to 'Ubuntu Server')

---

### Post by cariboo on 2012-04-17
The Ubuntu server is designed to run headless, so the point about a wireless keyboard is moot. If you need a gui to do your server administration, you'd be just as well off to install the desktop version, and just add the services you want to run.

---

### Post by NHclimber on 2012-04-18
> **cariboo907 said:**
> The Ubuntu server is designed to run headless, so the point about a wireless keyboard is moot. If you need a gui to do your server administration, you'd be just as well off to install the desktop version, and just add the services you want to run.
He's complaining about the install.
Drivers are missing on several of the install isos that make keyboard input impossible.
Although that brings up an interesting point:  maybe the server install should be designed to be headless if the result is designed to be headless?

---

### Post by cariboo on 2012-04-18
What I was getting at was that because the server is designed to run headless such amenities as wireless mouse and keyboard drivers may not be included in the iso. I personally think it's a bug, as I've used both the Live desktop and alternative iso while using a wireless keyboard and mouse without any problems.

When I do a server install, I usually have it connected to a KVM, once it's done, I disconnect the monitor and mouse/keyboard, and run it with only the power cord, network cable and USB connection to the UPS.

---

