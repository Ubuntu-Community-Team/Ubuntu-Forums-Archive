---
title: "Starling startup issues"
date: 2011-02-27
forum: System76 Support
---

### Post by Speedwagon on 2011-02-27
I've had a few errors so far when booting this new Starling(Star4, 10.04 netbook remix) I have.  

Currently, this only happens sometimes:
It boots up, and gets me to the login screen.  I login just fine, but then the problem starts.  This time, just before I typed this, I got the desktop background, but then a dialog box started flashing in the middle of the screen.  Just a blank, gray dialog box.  Finally it stopped flashing, and reads:
> An error occurred while loading or saving configuration information for evolution-alarm-notify.  Some of your configuration settings may not work properly.

Details: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash.  See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. 

This has happened to me at least once before, if not a few times.  After I hit OK, I have nothing but a desktop background.  No icons, no bars, no nothing.

How do I fix this?

edit: I don't know if it is related, but I also have an issue where sometimes nothing will actually load, after I get the normal desktop.  Example: I try to start Firefox, and it just sits there.  Or I try to shutdown, and it just its there.  Doesn't actually do anything, but it acts like it is starting the program, then nothing.

---

### Post by Speedwagon on 2011-03-01
New problem just occurred: I logged in, and it logged me out.  Logged in again, and it logged out to a blank screen.  Rebooted with the power button, and everything seems fine.

---

### Post by Speedwagon on 2011-03-02
I ran a memtest, and everything came up fine(I assume, since it all looked ok, and didn't return any errors that I could see).  Everytime I do a reboot, everything seems to work.  All problems seem to be a cold boot issue.  Looks like I can confirm the cold boot issue, as I just tried to boot off a USB drive(which didn't actually work, but it did warm up the netbook), and once rebooted everything was fine.  Going to try to remake the USB drive, and see what I get.

---

### Post by isantop on 2011-03-02
Go ahead and try it from the fresh drive, and let us know what you get.

---

### Post by Speedwagon on 2011-03-03
Haven't had a chance to try the USB drive again, but I have noticed that if I let the computer sit at the login screen for a short while, I don't seem to run into the issue.

If this was my desktop, I would suspect a hardware connection issue that is fixing itself when things warm up.  But since this is under warranty, I don't want to take it apart and check the connections.

Does that sound like a reasonable solution to S76?  Are you willing to take it apart and check the connections if I drop it off?

---

### Post by isantop on 2011-03-04
You can help confirm that by booting cold, then immediately rebooting, so that the computer doesn't have time to warm up. Also, try running for a while (to heat the system up), then shutdown completely and boot it back up.

---

