---
title: "checking lemur camera status"
date: 2010-05-16
forum: System76 Support
---

### Post by dnarnold on 2010-05-16
On the Lemur, a lot of the Fn-FX keys toggle hardware functions, e.g., Fn-F12 toggles bluetooth, Fn-F11 toggles wifi, and Fn-F10 toggles the camera.  For the first two there is an led to show the status, but there is none for  the camera.  It would be nice if there were a simple way to check (simpler than starting an application that uses the camera and seeing if it works).  E.g., a command line "camstatus" that returns the status, or a more general status check, which reports the status of all this hardware.  Is there such a thing, or could it easily be created?

---

### Post by msrinath80 on 2010-05-17
Something along the lines of "lsusb | grep ison" on a terminal could help with that. You could always write a simple bash script that checks the return value using echo $? and then prints out a friendly message based on that.

---

### Post by thomasaaron on 2010-05-17
Good idea. Right now, that's pretty much the best way to do it.

---

### Post by msrinath80 on 2010-05-17
Thanks Tom. A minor correction: For Lucid, the command on the lemur should be "lsusb | grep Acer" instead of what I said before. "ison" works only if you use dmesg apparently.

---

