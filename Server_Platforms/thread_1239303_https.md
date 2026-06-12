---
title: "https"
date: 2009-08-13
forum: Server Platforms
---

### Post by phillw on 2009-08-13
[SIZE=2][SOLVED] 

Hi, I've got Webmin all up and running - I can log on via [https://127.0.0.1:10000]("https://127.0.0.1:10000/") fine.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2] I have set my firewall (using Firestarter on Ubuntu 9.04) to allow port 10000 (which it correctly noted was Webmin), I have my router's firewall to accept port 10000.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2] But, I just get time-out when trying to connect to my WAN ip address using [https://xxx.xxx.xxx.xxx:10000]("https://xxx.xxx.xxx.xxx:10000/") - 
[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Webmin is set to accept all IP's (I will be tying this down once I have got logged on !), netstat -a shows udp listening on port 10000.
[/SIZE]


[SIZE=2]I can connect via http to my /var/www directory okay, and via https to my internal 192... address.[/SIZE]


[SIZE=2]Which bit have I forgotten to do ?[/SIZE]


[SIZE=2]Thanks,[/SIZE]


[SIZE=2]Phill.
[/SIZE]

---

### Post by wojox on 2009-08-13
I had that problem although I don't use webadmin or firestarter just my router firewall. I had to port forward 443 for https on the router.

---

### Post by phillw on 2009-08-13
Thanks, i checked and already have 443 set to forward.

Any other things i should check ?

Phill

---

### Post by Bachstelze on 2009-08-13
Are you trying to access Webmin from inside your LAN? Some routers forbid accessing the external IP from within the LAN, and there's no way around it. Try from outside your LAN.

---

### Post by phillw on 2009-08-15
The router was fine, however the setting up of the SSL bit was totally beyond me. However, a very nice person put this together - which, when i got my head round it, works perfectly :-)

[http://www.tc.umn.edu/~brams006/selfsign.html](http://www.tc.umn.edu/~brams006/selfsign.html)

Articles that well written should be easier to find !!!!!!

Thanks for the general pointers - I'm new to Mail Servers, Web Servers etc - It's a great learning curve !!

Thanks,

Phill.

---

