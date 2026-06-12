---
title: "no sound"
date: 2008-02-21
forum: System76 Support
---

### Post by hodad on 2008-02-21
I reinstalled 7.10 after a crash on my Pangolin a few weeks ago.  All is well, but no sound.  I have the sound icon, have gone thru all of the settings, and searched thru ubuntu forums, no luck.    All of the apps I try have no sound, tho it's not muted, and the sound is turned up.

Any ideas?  Do I need to reload the system76 drivers (which got wiped when I reinstalled)? 

Thanks

---

### Post by thomasaaron on 2008-02-22
**LET THERE BE SOUND!**

-----------------------------------------------------

Make sure you're connected to the Internet.

From a command line, enter:
sudo wget [http://planet76.com/repositories/system76-driver-2.1.3.deb](http://planet76.com/repositories/system76-driver-2.1.3.deb)
sudo dpkg -i system76-driver-2.1.3.deb

Then go to System > Administration > System 76 Driver
Click the restore tab and restore button.

Reboot your computer

------------------------------------------------------

**AND THERE WAS SOUND!**

---

### Post by edc80 on 2008-02-22
This is my first posting to these forums.  I am having the same problem but the solution above doesn't seem to work for me.

I have a System76 Gazelle Value gazv4.

I'm using Ubuntu 7.10 (fresh installation, complete new).

I've downloaded and installed system76 drivers (version 2.1.3).

In System > Administration > System 76 Driver I've done both the Restore System and Install Drivers (each separately, each followed by a reboot, each twice).

I've checked the sound icon in the corner of the screen, the controls are for HDA Intel (Alsa mixer), Master and PCM both up and not muted.

Still no sound.  Any suggestions?  (Much thanks for your help.)

---

### Post by edc80 on 2008-02-23
Woohoo!!! I just found a solution to this problem after 2 nights of exploring.  Here's what worked:

- double click the little sound icon in the upper right corner of the screen

- when its window opens, Edit > Preferences, then check all the boxes to make everything visible that you can

- then Switches tab, disable the External Amplifier (it was checked, I unchecked it)

And Voila, sound!!!

---

