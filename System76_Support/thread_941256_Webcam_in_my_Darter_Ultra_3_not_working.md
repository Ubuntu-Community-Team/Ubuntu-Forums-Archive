---
title: "Webcam in my Darter Ultra 3 not working"
date: 2008-10-07
forum: System76 Support
---

### Post by newdarteruser on 2008-10-07
I just got my daru3 today and when I use either skype to test my webcam or lucview, my computer freezes and I have to restart. 

If I use camorama, I get the error 'could not connect to video device /dev/video0. Please check connection'

I went to system76 drivers and installed them. 

EDIT: Cheese kinda works - I can see myself and take photos.

Any suggestions?

---

### Post by Modax42 on 2008-10-08
I am going to try to reinstall skype using the instructions of this thread [http://ubuntuforums.org/editpost.php?do=editpost&postid=5929342](http://ubuntuforums.org/editpost.php?do=editpost&postid=5929342)

---

### Post by thomasaaron on 2008-10-08
> If I use camorama, I get the error 'could not connect to video device /dev/video0. Please check connection'

Your webcam only works with applications that support the newer v4l2 protocol. Camorama does not support that yet. It works with the older v4l protocol.

> when I use either skype to test my webcam or lucview, my computer freezes and I have to restart. 

This is due to a bug in the Intel driver. Video with Skype works great with the previous generation graphics (X3100) but not with the X4500. When that bug is fixed, it will come down via an update.

In the meantime, Ekiga Softphone works.

---

