---
title: "I want to put my personal website at home, help!"
date: 2010-04-27
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-04-27
hi, any professionals, I was so exciting that I just registered a legal domain name for my personal website, and also I have installed the Ubuntu Server 9.10 on my home computer. Can I use the home computer IP address (192.168.0.1), which assigned by my home ADSL network router to point my website domain name on the Ubuntu server(DNS), or I have to use the nameservers, which provided by the domain name registration company, and I have to set the IP address of nameservers of the domain name registration company into the Ubuntu server 9.10, which I just installed at home.

which nameserver I should use, my home dns server or the registration companys' nameservers? help!!!

best regards and thanks,
:guitar::guitar:

---

### Post by VernieR on 2010-04-27
You should use the registration company's nameserver. The record for your registered domain should point at your public IP address (the IP address your ISP hands out to you). If your public IP address is dynamic, you need some sort of dynamic DNS updating.

Your Ubuntu server can use the 192.168.0.1 IP adress, but you have to make sure your router forwards all traffic on port 80 to this IP address.

---

### Post by uberlinuxnerd on 2010-04-27
Use a dynamic DNS service to update your IP and in your domainname DNS create a CNAME record pointing to you Dynamic DNS name. 

When your IP changes the dynamic DNS will update and your site should remain accessibly.

:KS

---

### Post by Iker Etxebarria on 2010-04-27
You have 2 options:
1.-Buy to your ISP a static IP service. Once you have that static IP change it in your DNS records
2.-Use services like [www.no-ip.com](www.no-ip.com) or [www.dyndns.org](www.dyndns.org) and then, as uberlinuxnerd wrote, create a CNAME record in your domains DNS entry to redirect your domain to the domain created with these services.

---

### Post by Yann76 on 2010-04-27
I did this website a looong time ago.. explains basic stuff about how to setup a LAMP server:
[http://idebian.sytes.net/index.php](http://idebian.sytes.net/index.php)

Hope this help you.

---

