---
title: "Braille claiming USB port"
date: 2007-08-07
forum: The Cafe
---

### Post by djconnel on 2007-08-07
I'd been unable to access my USB port from various programs which had been able to do so prior to my 7.04 upgrade.  The following was returned by dmesg :

usb 1-2: usbfs: interface 0 claimed by ftdi_sio while 'brltty' sets config #1 

britty, the braille reader code, was for some reason claiming the USB port.  It was recommended I uninstall the braille code, which I don't use and never requested:

% sudo apt-get remove brltty 

The USB problem was solved.

I'm not sure why braille, an extremely rarely used feature, would be installed by default.  Folks experiencing USB problems may want to consider this as a possible cause.

Dan

---

### Post by Polygon on 2007-08-07
is there some external piece of hardware or something that gets used in combination with britty? maybe britty thought that you were using and thats what was causing the usb port conflicts...

---

### Post by 23meg on 2007-08-07
I too had to uninstall it, when trying to establish communication with an [Arduino]("http://www.arduino.cc/") board.

---

### Post by sedition on 2007-09-01
My Arduino board just arrived in the mail. I uninstalled brltty, pulled down the dependencies, hooked it up, but I'm getting the flashing light that supposedly gets resolved with the sudo apt-get remove brltty I already performed. Anyone else still getting this error on 7.04? 
 ---EDIT --- 
Got it working after some Java shoe-horning. In the process of throwing together a Feisty/Diecimila how to and I'll be sure to post it once done.

---

### Post by 23meg on 2007-11-14
brltty seems to be disabled by default in Gutsy, and can be enabled in System / Administration / Services.

---

### Post by DoctorMO on 2007-11-14
Can you run `udevmonitor` and then plug in the device and see what it says? (perhaps attach it here)

I'm not sure if the above message  should be moved into the help forum.

---

