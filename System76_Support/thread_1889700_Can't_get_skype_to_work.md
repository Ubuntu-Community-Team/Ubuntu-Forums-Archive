---
title: "Can't get skype to work"
date: 2011-12-01
forum: System76 Support
---

### Post by Eyore15 on 2011-12-01
I have a star1 running Ubuntu 10.04.  I just this afternoon updated the system76 driver and restored my system to factory defaults.  My wireless wasn't working.  That seemed to fix it.  The problem I have now is in trying to use skype.  Whenever I "invoke" Skype, the screen turns black, there is no cursor movement, and the only way to get control back is to re-boot the machine. Then the whole process starts all over again.  I'm going to be able to use Skype on my star1 or should I move to a different platform for that.

---

### Post by isantop on 2011-12-02
Let's run skype from the command line and see if we get any additional information. Please go ahead and open up a terminal, then run this command:

skype > ~/logfile

This will create a file called "logfile" in your home folder, which should be present even if the machine locks up. Simply reboot, then post the contents of that file and I'll have a look.

---

### Post by sfmadmax on 2011-12-07
Did you install sykpe from synaptics ? if not which deb did you use? Also is your host x64 or x32?   (uname -a)

---

