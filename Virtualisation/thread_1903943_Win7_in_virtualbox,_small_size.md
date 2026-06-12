---
title: "Win7 in virtualbox, small size"
date: 2012-01-03
forum: Virtualisation
---

### Post by vincegata on 2012-01-03
I installed Win7 in virtualbox, but it does not run in full screen, only small size.

Is it possible to run it full screen?

Thank you!

---

### Post by howefield on 2012-01-03
Try installing guest additions if you haven't already.

From the VirtualBox menu, select Devices > Install Guest Additions.

---

### Post by vincegata on 2012-01-03
I get:


Failed to download the VirtualBox Guest Additions CD image from [http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso](http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso).

Error downloading [http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso](http://dlc.sun.com.edgesuite.net/virtualbox/4.1.2_Ubuntu/VBoxGuestAdditions_4.1.2_Ubuntu.iso) - server replied: Not Found


What is the other way to download those additions?

Thank you!

---

### Post by howefield on 2012-01-03
Generally should be automatic as the guest additions iso is part of the VirtualBox download.

Have a read here on how to manually mount the iso.. 

[http://www.virtualbox.org/manual/ch04.html#additions-windows](http://www.virtualbox.org/manual/ch04.html#additions-windows)

failing that download the appropriate version of the guest additions iso from here..

[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

---

### Post by vincegata on 2012-01-03
damn never works out of the box, damn the one who planted this bug.


Thank you for your help - now it works!

---

