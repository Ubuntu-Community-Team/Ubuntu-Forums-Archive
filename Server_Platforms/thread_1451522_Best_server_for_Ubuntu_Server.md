---
title: "Best server for Ubuntu Server"
date: 2010-04-10
forum: Server Platforms
---

### Post by laristech on 2010-04-10
Is there a Dell or HP server that works best with Ubuntu Server. 

Looking for normal specs. Dual core x64 processor, 2 gigs min of ram, and raid 1. 

The main part I am worried about is the RAID 1 working with ubuntu server x64 9.10.

Has anyone has any issues with a Dell server?

Looking for Dell Desktop base server. Not a blade server. 

I have found this [http://webapps.ubuntu.com/certification/list/?category=Server](http://webapps.ubuntu.com/certification/list/?category=Server) but it only shows blade servers.

---

### Post by HermanAB on 2010-04-11
I haven't encountered a Dell that doesn't work with Linux.

---

### Post by ubun2warrior on 2010-04-11
I think you can go with Dell as they have some sort of tie up with Ubuntu and have also started shipping laptops & desktops pre loaded with ubuntu. So may be you will get better tech support with Dell.

---

### Post by CharlesA on 2010-04-11
Don't most "servers" from Dell use a dedicated RAID card? If so, then you'd only have to worry about finding the driver for it if it is not already included in the kernel.

Other then that, Linux (and Windows for that matter) will only see 1 drive if it's a hardware RAID.

---

### Post by inphektion on 2010-04-11
I have a dedicated raid card in all my dell servers and I have hardy heron installed out of the box on Dell 1650, Dell 1750, Dell 1950, Dell 2950 and the new Dell R600 and R700.
 
so no worries with those.  all worked on clean install.

---

### Post by fang0654 on 2010-04-11
One caveat - newer dells take a little bit of extra legwork to get working with Ubuntu 8.04 (you need to install via USB Flash, and won't be able to access the DVD drive, also you will need to install the NIC driver).  If you are using 9.10 you won't have any trouble.

---

