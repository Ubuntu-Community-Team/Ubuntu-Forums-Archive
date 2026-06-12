---
title: "Forwarding a domain onto my ubunto apache server?"
date: 2013-04-13
forum: Server Platforms
---

### Post by adsnoob on 2013-04-13
Title really says it all. I looked around everywhere and I cant seem to find out how to do it. :/ I want to have my main domain setup and working then also have a subdomain (server.domain.net). So can anyone help me? Also I am using GoDaddy for my domain. If that helps :P

---

### Post by adsnoob on 2013-04-14
bump: Can anyone help me? :/

---

### Post by darkod on 2013-04-14
First, is the server at your home? If it is, did you check whether your ISP is blocking port 80? Many of them block port 80 for residential customers in which case you can't run a webserver at home, not at the default port.

Second, is apache set up and working? From another computer on the same network, if you browse to the IP of the server does it open the website?

Third, setting it up in GoDaddy is the smallest problem. Go into the DNS Manager and look in the A hosts section. Change the default @ host to your public IP address. If your public IP is not static, you need some dynamic servoce like dyndns or noip.
Then create another A host which you can call 'server' and point it to the IP also. That will make it available server.domain.com to be directed to your IP also.

---

### Post by adsnoob on 2013-04-14
> **darkod said:**
> First, is the server at your home? If it is, did you check whether your ISP is blocking port 80? Many of them block port 80 for residential customers in which case you can't run a webserver at home, not at the default port.

Second, is apache set up and working? From another computer on the same network, if you browse to the IP of the server does it open the website?

Third, setting it up in GoDaddy is the smallest problem. Go into the DNS Manager and look in the A hosts section. Change the default @ host to your public IP address. If your public IP is not static, you need some dynamic servoce like dyndns or noip.
Then create another A host which you can call 'server' and point it to the IP also. That will make it available server.domain.com to be directed to your IP also.


My server is being hosted from a VPN company, and yes I can access it from another computer using the actual IP. I will take a look into it.

EDIT:----------------------------------------------------

I still cannot connect. I think it has something to do with my Server itself. When I try to restart it it gives me something like

> * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using*IPADDRESS HERE* for ServerName
 . . . waiting apache2: Could not reliably determine the server's fully qualified domain name, using*IPADDRESS HERE* for ServerName
                                                                                                                                                                                [ OK ]

And I want the server.domain.com one to be forwarded to a sub folder because it is going to be displaying my servers information.

---

### Post by darkod on 2013-04-14
I guess you meant VPS server, because VPN is entirely a different thing. Ok then, a VPS provider wouldn't block service ports.

That message only says you didn't put a FQDN on your server when installing, but in theory it shouldn't stop websites working.

What you are trying to do has two parts:
1. The configuration of DNS in GoDaddy.
2. The configuration of apache2.

For 1: From any machine try to use nslookup (or in linux you might use dig) to see if the DNS is resolving correctly. When you try your domain and subdomain (host) it needs to return your public IP as result. That means the DNS is working fine. You can also test it with ping. Even if you get no reply if the VPS provider is blocking ping replies for security reasons, at least the ping command will tell you which IP it's relating to the domain, so you know if DNS is working fine if that's your IP showing. Try something like:
```
nslookup domain.com
nslookup server.domain.com
ping domain.com
ping server.domain.com
```

Regardless which page you want to open, the @ and server A host have to exist in the GoDaddy DNS and point to your IP.

For 2: This is where it decides which page to open. You configure in apache2 two websites with their own  domains/addresses like domain.com and something.domain.com and each has it's own document/root folder. That is how apache knows what to open according to the address you entered in the browser. The DNS in GoDaddy doesn't decide that, but it has to resolve the domain.com and something.domain.com to the correct IP where the corresponding web server is.

I don't know apache in details but there are plenty of tutorials including in the ubuntu documentation so I guess a basic setup of two websites shouldn't take you long.

---

### Post by adsnoob on 2013-04-14
Thank you :] I got it all working now!

---

