---
title: "IBM x3250 Install keeps failing"
date: 2009-07-18
forum: Server Platforms
---

### Post by mod_plod on 2009-07-18
Hi all. I have a rack (12) of x3250 servers all with 4gig of ram and each with a 1TB raid 0. my problem is that no matter what release of ubuntu I try ( in fact no mater what distro I try) the install keeps failing saying the disk is corrupt. I have down loaded the iso at least four times and burnt it on many PC's all at the slowest speed. and it passes the disk check every time. I have even replaced the drive on one just in case it was faulty, but with no joy. I have also tried to install it from a usb key and via the network all attempts fail.

My question is this...

is there some reason for this? does the x3250 require some special install options? or is there anyone who has managed to get 9.04 server to install on a x3250?

help please.... I do not want to have to install winblows (which will install) into my network. I have managed for two years without it and just got the company to start accepting ubuntu as a desktop OS too.

---

### Post by Vegan on 2009-07-18
Try using the disks as a JBOD as the RAID controller may not be supported in the kernel.

---

### Post by windependence on 2009-07-19
You will probably have better luck with 8.04 than the new version. I personally have not had good luck with 9.04 at all. 8.04 LTS is very solid and works with most hardware. 

Vegan, if the controller doesn't work with the OS, it isn't going to matter what configuration you try, and this machine does not support JOBD anyway.

Just curious mod_plod, why not virtualize all those rack servers. I could buy a car with the money you would have saved and get gas with the electricity savings ;-)  I'm assuming there is a reason you needed separate hardware.

Also, if you just can't get Ubuntu to work, for servers, you could try other distros like CentOS or OpenSuSE. I am almost certain FreeBSD with work with no problems and IMHO it's more stable than Linux. This is all assuming you aren't loadin GUIs on these servers.

-Tim

---

### Post by jerrrys on 2009-07-19
forget this post

---

