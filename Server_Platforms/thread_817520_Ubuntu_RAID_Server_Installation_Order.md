---
title: "Ubuntu RAID Server Installation Order"
date: 2008-06-03
forum: Server Platforms
---

### Post by duiu on 2008-06-03
Sometime soon, I am going to create a print server and Samba fileserver using a RAID card and some SATA drives and Ubuntu Server (8.04). The computer I am going to install this on is currently running Windows 2000 and has an 80gb HDD. I am planning on using the 80gb drive as my install drive and then purchasing several 500 or 750gb drives for the RAID. Eventually I plan on setting this up so that it doesn't require a monitor and can be configured through SSH. 

Should I install Ubuntu on the 80gb hard drive, then install the RAID, or should install the RAID and then Ubuntu?

Also, should I install OpenSSH, Fileserver, and Print Server software right at the operating system install, or wait until I have configured stuff? If so what packages do I need to install.

And does anyone have any suggestions for SATA RAID cards with 4-5 ports that are relatively cheap?

Thanks,

duiu

---

### Post by windependence on 2008-06-04
Well there aren't any SATA RAID cards that work well with Linux that are cheap. Cheap != better. I have had great luck with 3 Ware cards.

I would load and configure your system first without installing any software during the install, and then when you get everything configured the way you want it, load and configure each application that you are going to use.

Installing the OS on a non-RAID volume is an excellent idea. that way if you have RAID problems you can still recover the system or even reload the OS without touching the data on the RAID volume.

Hope this helps.

-Tim

---

### Post by duiu on 2008-06-05
Thanks, but what are the packages I would need to install?

I assume samba-suite will cover all the samba stuff, but I don't know the names of the packages for SSH and print server.

---

