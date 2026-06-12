---
title: "Nvidia 340.24 driver"
date: 2014-07-17
forum: System76 Support
---

### Post by kend6502 on 2014-07-17
I read an artical ([http://www.ubuntugeek.com/install-nvidia-340-24-drivers-in-ubuntu.html](http://www.ubuntugeek.com/install-nvidia-340-24-drivers-in-ubuntu.html)) stating how to install the latest 340.24 driver.  

1) Is this something System 76 approves?

2) What is System 76's official procedure on updating Nvidia drivers?

Thanks,
kend650
bonobo 5 (nvidia 560m)

---

### Post by Vladlenin5000 on 2014-07-18
I can't and I won't speak for System76 but I can briefly comment.

1) System76 systems requiring nvidia driver are usually delivered with the recommended proprietary driver installed by its own driver implementation. Considering this is the default then...
2) No policy on updating nvidia drivers.

You can test it an if not happy you can even reinstall as usual - standard procedure - and then add the System76 PPA and install the System76 driver package. The result is the same as in an OOTB system.

---

### Post by isantop on 2014-07-21
We automatically issue updates to the Nvidia driver for applicable systems by updating the system76-driver-nvidia package. This will keep you on the correct version for your system.

---

### Post by kend6502 on 2014-07-22
Thank you Ian that was the answer I was looking for!!

Now, how do I know when there is a system76-driver-nvidia package update?  Does that show up in the software updates, or do I have to download the system76 driver package periodically to see if there are updates there?

---

### Post by isantop on 2014-07-24
Any updates to packages that you install through apt-get or software center will show up in your regular system updates. As long as you keep your updates installed, you'll always have the latest tested Nvidia driver ready to go!

---

