---
title: "[SOLVED] Borked wireless after upgrade"
date: 2008-11-03
forum: System76 Support
---

### Post by glacialfury on 2008-11-03
This joins the growing number of upgrade issues, I'm sure.  I ran the automatic update today; at many, many junctions it asked me if I wanted to keep an old version of various customized configs I had or replace them; I always chose to keep my old ones, figuring that would cause the least problems in the future.

When I finally did load into the new one, some things were missing.  First of all, I loaded it from "Ubuntu 8.04....." on the grub menu, since that was one of the things I didn't let it replace.  It still loaded 8.10 though, which strikes me as kind of funny.

Most notably, the wireless network icon in the system tray is gone.  I don't know how to connect to my network without it, it doesn't seem to be recognize the LAN cable when I plug that in, and I don't know how to summon up the network icon to try and find my wireless network.

Any clues?

---

### Post by thomasaaron on 2008-11-04
After I upgraded, the icon was missing too, which I thought was pretty weird, as I was connected to a a wired connection. I rebooted twice, and then it came back and hasn't disappeared since. Try rebooting.

---

### Post by glacialfury on 2008-11-07
Four reboots now and still no internet.

---

### Post by thomasaaron on 2008-11-07
Please try my instructions here:

[http://ubuntuforums.org/showthread.php?t=972051](http://ubuntuforums.org/showthread.php?t=972051)

Does your Internet work correctly from a live CD?

You may also want to try to re-install network manager...
sudo apt-get --reinstall install network-manager

Also, go to System > Preferences > Sessions > Start-up Programs and make sure Network Manager is there and checked.

---

### Post by glacialfury on 2008-11-09
That worked flawlessly, Aaron, thank you again.

---

