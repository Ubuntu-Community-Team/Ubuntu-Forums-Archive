---
title: "Apache, ddclient config HELP :("
date: 2005-08-27
forum: Server Platforms
---

### Post by wildasIwanabe on 2005-08-27
Hi,

I've been trying to learn Linux over the past couple of days and I've manage to install Apache, PHP and MySql. It all appears to be working fine on 127.0.0.1.

I've been hosting a site "aaa.ath.cx" on my XP machine and thought I'd stop that and start hosting it from my Ubuntu server.

So I installed and configured ddclient and opened port 80 on my router and on the server.  But for some reason I cannot access "aaa.ath.cx" from the net.  All I get is an error message "operation timed out"

This is my configuration in ddclient.conf
pid=/var/run/ddclient.eth0.pid
protocol=dyndns2
use=linksys, fw=192.168.1.1, fw-login=admin, fw-password=xxx
server=members.dyndns.org
login=xxxxxxxx
password=xxxxxxx
aaa.ath.cx

Also, I tried tried to ping aaa.ath.cx and that worked.

Do I have to add ServerName aaa.ath.cx somewhere?  If so where?

---

### Post by wildasIwanabe on 2005-08-31
Never mind, I figured it out..... I had to open the NAT port on the router.

---

