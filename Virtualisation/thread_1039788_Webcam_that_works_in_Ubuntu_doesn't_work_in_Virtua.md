---
title: "Webcam that works in Ubuntu doesn't work in Virtualbox XP machine"
date: 2009-01-14
forum: Virtualisation
---

### Post by diablo75 on 2009-01-14
Someone I know has a Logitech 5000 webcam that works just fine in Ubuntu.  But in a Windows XP virtual machine hosted by Virtualbox, I get the results seen in the screenshot attached.

The camera lights up with a green light when you go to view video off the camera from within XP.  So the connection between the VM and the camera seems to be made, but not completely... or something.

Drivers are up to date.  I went to the device manager, Imaging Devices, selected the web cam, selected "Update drivers".  Next thing I knew the logitech update manager came up, downloaded the software... more or less appeared to reinstall the entire package of software (and not just the drivers).

Yet I get the same results.

Using the Microsoft Explorer window instead of the logitech software produces similar results.  But instead of that gradient blue as seen in the screen shot, it's just solid black.

---

### Post by HotShotDJ on 2009-01-15
I did a little research via Google for you, and have learned that this is a known bug in Virtualbox that effects many (if not all) webcams.

See: [http://www.virtualbox.org/ticket/242](http://www.virtualbox.org/ticket/242)

---

