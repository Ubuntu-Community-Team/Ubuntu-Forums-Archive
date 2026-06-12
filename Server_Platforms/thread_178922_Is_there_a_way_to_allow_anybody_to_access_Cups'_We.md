---
title: "Is there a way to allow anybody to access Cups' Web interface?"
date: 2006-05-18
forum: Server Platforms
---

### Post by Quake on 2006-05-18
I'm only doing a small Home Network So I don't need all the security to just allow only a selected IPs to the Interface.

I followed the instructions on [http://www.howtoforge.com/forums/showthread.php?t=2208&page=2](http://www.howtoforge.com/forums/showthread.php?t=2208&page=2) and [http://www.howtoforge.com/samba_setup_ubuntu_5.10_p5?from=10&comments_per_page=10](http://www.howtoforge.com/samba_setup_ubuntu_5.10_p5?from=10&comments_per_page=10) but couldn't make it work.

So is there a way to just allow anybody to access the web interface?

I'll attach my cupsd.conf file 
*Btw: 192.168.1.130 is my computer's IP while the server's IP is 192.168.1.160*

---

### Post by elaup on 2006-10-14
You need to add cupsys to the shadow group.

IE:

$ sudo adduser cupsys shadow

Then restart cups

$ sudo /etc/init.d/cupsys restart

This should allow your normal login to administrate printers from the web interface.

Then
[http://localhost:631](http://localhost:631)
to access web administration

---

