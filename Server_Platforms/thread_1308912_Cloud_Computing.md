---
title: "Cloud Computing"
date: 2009-11-01
forum: Server Platforms
---

### Post by darwinj on 2009-11-01
I live out in the middle of nowhere (Brazil interior). I have been reading a lot about cloud computing. I use an Ubuntu server in my wifes office (file server, print server, DHCP, and backup). We have 5 computers on our LAN. I am upgrading to 9.10 and am wondering if we need cloud computing. I am not sure what it is or if it would be something that would benefit our office. Could someone shed some light on what cloud computing is and how we could use it in our small LAN.
Thank you,
Darwin

---

### Post by Chayak on 2009-11-01
Cloud computing isn't really for small LANS.  It's just another term for virtual machines running on a group of computers that you can manage from a single point.  They have Private clouds for use within the business and Public for those hosting things like web servers.  There's benefits to running some virtualized systems on a business network but to take it to the level it could be considered a cloud in the enterprise sense requires a lot of hardware for management systems, iSCSI interfaces over a dedicated storage network that's normally fiber optic, a management network, and a network for the virtual machines to communicate on.  I've seen smaller setups merge the management and virtual machine networks but the storage network has always been separate.

---

### Post by laluz on 2009-11-01
> **darwinj said:**
> Could someone shed some light on what cloud computing is and how we could use it in our small LAN.
Thank you,
Darwin
The main point is that you pay as you go for the computing. Instead of installing hardware on your site, you would get a fast network channel to a cloud provider and just use its infrastructure there as much as you need at any time.
I guess you dont need cloud as you have your hardware already.

---

### Post by darwinj on 2009-11-10
Thank you. This is the best defenition on cloud computing that I have heard.
Darwin Powell

---

### Post by darwinj on 2009-11-10
Thank you. As always I get answers that make sense from this forum.
Darwin Powell

---

### Post by darwinj on 2009-11-10
Thank you. As always I get answers that make sense from this forum.
Darwin Powell

---

### Post by fjgaude on 2009-11-10
I would hold off upgrading to 9.10 until all the issues about it are resolved. Just my opinion.

---

