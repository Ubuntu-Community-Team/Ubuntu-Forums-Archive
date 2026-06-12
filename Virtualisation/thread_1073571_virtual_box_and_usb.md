---
title: "virtual box and usb?"
date: 2009-02-18
forum: Virtualisation
---

### Post by Benbow on 2009-02-18
I have installed virtualbox (twice) but I cannot get usb support and I need it (usb) to print. I am using ubuntu intrepid but need to use windows occasionally for some of my work. What procedure do I follow to get this?

---

### Post by baizon on 2009-02-18
Which version of VirtualBox are you using?
What is the Host system saying (is it mounted)? 

Check that:
[http://forums.virtualbox.org/viewtopic.php?t=14057]("http://forums.virtualbox.org/viewtopic.php?t=14057")
[http://forums.virtualbox.org/viewtopic.php?t=8669]("http://forums.virtualbox.org/viewtopic.php?t=8669")

---

### Post by Doug11 on 2009-02-18
> **Benbow said:**
> I have installed virtualbox (twice) but I cannot get usb support and I need it (usb) to print. I am using ubuntu intrepid but need to use windows occasionally for some of my work. What procedure do I follow to get this?
Before you start the OS in VB,,click on the Settings tab and you should be able to enable USB in there. I'm pretty sure it is disable on the initil setup and you have to manually enable it. I know I had to on my first setup because that was my major need for VB was USB, but once i checked enable,,it even pick up and named the devices I had plugged in.

---

### Post by Benbow on 2009-02-18
Sorry for the delay but I have been fiddling with the usb settings and I have found that by following your advice and going into settings immediately after VB starts up then click on usb there are filters available. It is then necessary to enable the usb controller and then click on the filter on the right hand side to enable the filter for the appliance in question, in my case the Canon MP 170.

This is a problem which concerns many people and I hope that this thread is of help to them.

Thanks for your help.

---

