---
title: "Confused about DNS"
date: 2008-06-02
forum: Server Platforms
---

### Post by KB1LQC on 2008-06-02
Ok so I just got my ubuntu LAMP server running to an extent.  I am confused about DNS.  I want to host my own website... and to get a [www.example.com](www.example.com) working can I host my own DNS with BIND?  or do I still need something from my ISP (Comcast)?




Bryce
KB1LQC

---

### Post by windependence on 2008-06-02
> **KB1LQC said:**
> Ok so I just got my ubuntu LAMP server running to an extent.  I am confused about DNS.  I want to host my own website... and to get a [www.example.com](www.example.com) working can I host my own DNS with BIND?  or do I still need something from my ISP (Comcast)?




Bryce
KB1LQC

You don't need to, and probably can't host your own public DNS server. You need to point your site 'A' record and cname to your server's IP address. Do you have a static IP address? If not, you will either have to get one or use a redirection service such as no-ip. I don't recommend the redirection because it won' work for all people trying to access your site. Many companies block redirected sites, and quite a few people surf from work.

First before you go through all that, check to make sure your port 80 is open. Go to [www.canyouseeme.org](www.canyouseeme.org) and check port 80. If it is blocked, Comcast probably is doing it and it will be difficult to host your own website. I am pretty sure they block it unless you have a business account.

-Tim

---

### Post by KB1LQC on 2008-06-03
OK thanks it makes much more sense to me now!

---

