---
title: "update to Ubuntu 8.10 under VirtualBox"
date: 2008-11-04
forum: Virtualisation
---

### Post by ubuntuubuntu on 2008-11-04
Hi,
I've just updated from Ubuntu 8.04 to 8.10. I run it under VirtualBox. After the update, I get the message in the attached image. Can someone help me with this issue?

Thank you very much!

---

### Post by LeAstrale on 2008-11-04
You need to reinstall the Vbox drivers.

To get GUI search for "vesa xorg"

You basically need to change to the vesa driver until the vbox one is installed again.

---

### Post by ubuntuubuntu on 2008-11-04
Thank you, that message doesn't show up anymore, but now I have another problem. When I try to install Guest Additions, I get the message

"Unable to build the kernel module. See the log file /var/log/vboxadd-install.log for more details. "

In that log file, there is the following message:

/tmp/vbox.0/r0drv/linux/the-linux-kernel.h:55:27: error: asm/semaphore.h: No such file or directory

How do I solve this? Thanks again!

---

### Post by AdamsJourney on 2008-11-05
I got the same message.  I found that I was still running Vbox 1.6.4 and they are now up to 2.0.4.  I updated by downloading the 8.04 package here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) That resolved this issue for me.

---

