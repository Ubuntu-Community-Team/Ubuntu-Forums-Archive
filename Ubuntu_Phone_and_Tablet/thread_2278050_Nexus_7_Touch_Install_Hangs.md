---
title: "Nexus 7 Touch Install Hangs"
date: 2015-05-13
forum: Ubuntu Phone and Tablet
---

### Post by JedTheHead on 2015-05-13
Hello and thank you in advance!

I have a brand new Nexus 7 2013 Wifi and have been trying over and over to install Ubuntu Touch following the instructions here: [https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

All works well, but it never completes.   I run this command: $ ubuntu-device-flash touch --channel=devel --bootstrap

and the packages push to the device without error and then... nothing... 

It pushes several images / packages from ./cache/ubuntuimages/ and then just sits there - forever.  The Nexus is still sitting in the Ubuntu Touch Recovery screen... both will just sit there and never completes.  If I manually reboot the Nexus, it goes back into the Google / Android code.

Any ideas?

Thanks!!

---

### Post by lgd on 2015-05-13
You need vivid-proposed not vivid. This is over and out since a very long time with no updates.

---

### Post by Elfy on 2015-05-15
Last channel flash I did here was 

ubuntu-device-flash touch --channel=ubuntu-touch/devel-proposed

---

