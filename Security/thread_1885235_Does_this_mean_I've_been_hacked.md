---
title: "Does this mean I've been hacked?"
date: 2011-11-22
forum: Security
---

### Post by TheNewbieGeek on 2011-11-22
The keyboard woudn't work at the login screen. I  reinstalled ubuntu using unetbootin and everything worked fine. Does this mean I had a virus? I had used the os before and everything worked just fine. What else could the problem be? 

Also I don't know how to turn off the internal mouse on my laptop. Do you know. Thanks for the replies.

---

### Post by mikejonesey on 2011-11-22
no your wern't hacked, more than likeley a new peice of hardware or software or bad config file...

to switch off your internal mouse...
[http://www.mikejonesey.co.uk/articles/linux-switch-touchpad-on-and-off.html](http://www.mikejonesey.co.uk/articles/linux-switch-touchpad-on-and-off.html)

---

### Post by TheNewbieGeek on 2011-11-22
> **mikejonesey said:**
> no your wern't hacked, more than likeley a new peice of hardware or software or bad config file...

to switch off your internal mouse...
[http://www.mikejonesey.co.uk/articles/linux-switch-touchpad-on-and-off.html](http://www.mikejonesey.co.uk/articles/linux-switch-touchpad-on-and-off.html)

Thanks for answering. How would a config file get bad?

---

### Post by HermanAB on 2011-11-22
Howdy,

The keyboard, screen and mouse are managed by Xorg.  The configuration files for Xorg are in /etc/X11 and there are also files in your home directory that can override these settings - since each user may want to have things configured slightly differently.  Therefore there are multiple places where a configuration file can be changed causing weird issues.

However, the most likely explanation is that you have a timing issue during startup, that sometimes leaves the keyboard dysfunctional.  It may happen again.

---

### Post by Telengard C64 on 2011-11-23
> **TheNewbieGeek said:**
> The keyboard woudn't work at the login screen.

Is this a USB keyboard? If so, try unplugging and replugging the keyboard.

---

### Post by Ms. Daisy on 2011-11-23
To learn a little more about being "hacked", I recommend the Basic Security Wiki 
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Your username implies that you're a new user, which is the intended audience for the Wiki.

---

