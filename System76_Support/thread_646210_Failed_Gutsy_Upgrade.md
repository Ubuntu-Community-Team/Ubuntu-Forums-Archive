---
title: "Failed Gutsy Upgrade"
date: 2007-12-20
forum: System76 Support
---

### Post by scholarwarrior on 2007-12-20
I tried to upgrade to Gutsy and it failed halfway through the install.  I now do not have a GUI and can't do any updates or upgrades.  Help!

---

### Post by K.Mandla on 2007-12-21
Does your computer boot to the command line?

---

### Post by thomasaaron on 2007-12-21
Are you booting into a Busybox prompt?

If so, please also provide the System76 model number of your comptuer. There may be a model-specific fix (especially if you have a Gazelle Value or an older Darter).

---

### Post by scholarwarrior on 2007-12-21
Yes, it boots to the command line.

---

### Post by thomasaaron on 2007-12-21
And the System 76 Model Number?

---

### Post by scholarwarrior on 2007-12-23
It's a Pangolin Value.  S96FM for the model number.

---

### Post by thomasaaron on 2007-12-24
OK, let's try to re-do the update from the command line:

Boot the computer up with a wired internet connection.
When you get to the command line:

sudo ifdown eth0
sudo ifup eth0
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade
sudo reboot

Let me know if you get any errors.

---

### Post by scholarwarrior on 2007-12-24
I do have one error.

"Couldn't configure pre-depend python-central for python-apt, probably a dependency cycle."

then I rebooted and it booting to KDM failed.  KDM is what I had as my default.

I am still at the command line.

---

### Post by scholarwarrior on 2007-12-24
ok, i managed to get to a GUI.

---

### Post by scholarwarrior on 2007-12-24
But I am still at 7.04

---

### Post by scholarwarrior on 2007-12-24
Is there a way to do a clean install and keep the System76 driver and all the configurations the way they were when I go the system?

---

### Post by palintheus on 2007-12-26
> **scholarwarrior said:**
> Is there a way to do a clean install and keep the System76 driver and all the configurations the way they were when I go the system?

A 'clean install' is just that, you start with a clean slate, so to retain any settings or data would not be a clean install. you could backup your /home directory and restore your data, but if you are having issues with configurations and errors I would just cut my losses and reinstall without restoring any backups.

---

### Post by scholarwarrior on 2007-12-26
Basically that is correct.  I just want to get the System76 driver back.

---

### Post by palintheus on 2007-12-26
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

