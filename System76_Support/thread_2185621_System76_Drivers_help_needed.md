---
title: "System76 Drivers help needed"
date: 2013-11-03
forum: System76 Support
---

### Post by jszurdi on 2013-11-03
Hi all,

I bought a  gazp9 sys76 laptop. I have a Windows on it. And next to the windows I installed an Ubuntu 12.04.3 LTS  64 bit.
I tried to install system76 drivers from console, with:
sudo apt-add-repository ppa:system76-dev/stable
C
sudo apt-get install system76-driver
 ,but it didn't work.
Then I downloaded them from: [http://planet76.com/repositories/system76-driver_3.2.7_all.deb](http://planet76.com/repositories/system76-driver_3.2.7_all.deb).
But after installation when I try to run it I get:

Your system is unsupported.
This application is desgined for System76 computers running Ubuntu versions 6.06 through 12.10. It appears your system fails one or both of these requirements. 
If you are running one of these Ubuntu versions on a System76 computer, please contact support at [www.system76.com/support](www.system76.com/support)

Can anyone help with this?

Thanks!

---

### Post by javsalgar on 2013-11-03
Might the version available in planet76 be outdated?

---

### Post by jszurdi on 2013-11-03
Yes, according to:
[http://ubuntuforums.org/showthread.php?t=2159121](http://ubuntuforums.org/showthread.php?t=2159121)
But that is the official link from the site. Where do I find the newest version?

Plus:

$ sudo apt-get install system76-driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
system76-driver is already the newest version.

---

### Post by scoodlebop on 2013-11-03
System76 doesn't support old versions of Ubuntu. The earliest that would work is 13.04 -- the driver wouldn't have anything designed to get your system working on 12.04.

---

### Post by jszurdi on 2013-11-03
No comment...
Changed to 13.xx

Thanks for the answers!

---

### Post by houstonbofh on 2013-11-06
This thread may or may not help you.  [http://ubuntuforums.org/showthread.php?t=2165676](http://ubuntuforums.org/showthread.php?t=2165676)

I suspect that your new system is not recognized by the older driver pack that works with 12.04.

---

