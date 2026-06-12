---
title: "Choosing Ubuntu as my server operating system"
date: 2008-08-24
forum: Server Platforms
---

### Post by Monarchist on 2008-08-24
Hello everyone. :)

I am making the change from CentOS 64-bit to Ubuntu Server Edition 64-bit. I hope I am making the right choice in [my decision](http://www.webhostingtalk.com/showthread.php?p=5276700#post5276700).

My sites mostly consist of PHP and MySQL-powered websites that are growing rapidly. Currently my most popular website achieves about 5k unique visitors per day right now with over 100k page-views daily.

At the present time, I am in the process of upgrading my current server to a new one, with the following specifications:

Intel Quad Core Q9550 Processor [[?](http://www.afterdawn.com/hardware/product_details.cfm/5038/intel_core_2_quad_q9550)]
8GB DDR2-6400 RAM [[?](http://www.kingston.com/HyperX/products/khx_ddr2.asp)]
Dual Western Digital 76GB 10k RPM HDD (RAID 1)
100mbps Connection
Ubuntu Server Edition 64-bit

I hope you guys will help me administer my server. My current server is facing a DDoS attack and though it can handle it (it's pretty beastly as well), I just think it's time to upgrade and get away from CentOS. :D

---

### Post by Vadi on 2008-08-24
Not sure if that's a question or no, but these forums are usually quite helpful and supportive, so you can count on that.

---

### Post by k8bopibu on 2008-08-24
I don't think much of it is a question other than a slight one about a DDoS attack?... figured I would include some links that might help you with catching and preventing future DDoS attacks: 

[Cisco whitepaper](http://www.cisco.com/en/US/tech/tk59/technologies_white_paper09186a0080174a5b.shtml) 
[lots and lots of links about DDoS attacks](http://staff.washington.edu/dittrich/misc/ddos/)

Hoped I helped some... I don't even know if this was your question but owell.

~k8

---

### Post by Vadi on 2008-08-25
I think ubuntu's ufw tool can help you against those.

---

### Post by moonpup on 2008-08-25
Hi,

You haven't really stated why you want to switch operating systems? Is Centos not working out the way you expected or do you think switching to Ubuntu will help mitigate the DDos attack. If your reasoning is the latter, it won't help you.

---

### Post by Monarchist on 2008-08-27
> **moonpup said:**
> Hi,

You haven't really stated why you want to switch operating systems? Is Centos not working out the way you expected or do you think switching to Ubuntu will help mitigate the DDos attack. If your reasoning is the latter, it won't help you.
No. I said I switched from CentOS to Ubuntu Server Edition for the support community. :)

---

### Post by gtdaqua on 2008-08-27
> **Justice McCay said:**
> No. I said I switched from CentOS to Ubuntu Server Edition for the support community. :)

True enough. This forum is very active indeed.

---

### Post by windependence on 2008-08-28
I certainly can't argue with that point. One thing Ubuntu has is good community support.

If I was running someting on your scale however (and I do) I would look into FreeBSD. In terms of scalability, and rock solid reliablility, you really can't beat it. Not that there is anytihng wrong with Ubuntu or any Linux in general, but a quick check of netcraft.com will reveal that a very large part of the web hosts on FreeBSD. There must be a reason.

-Tim

---

