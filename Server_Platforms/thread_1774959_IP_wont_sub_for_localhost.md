---
title: "IP wont sub for localhost"
date: 2011-06-04
forum: Server Platforms
---

### Post by scottlw on 2011-06-04
Hello,

I was wondering if any can help me out. I installed LAMP and everything seems to be working but everytime i try to use my IP address to view my site, Nothing would happen. It wont connect. I also heard something about SSL certs and stuff about that but i just need help getting my site up to the public from my computer. I'll even let someone remotely connect to help me out. I'm running Ubuntu 11.04 btw and apache is working.

thanks

---

### Post by wlraider70 on 2011-06-04
ssl certs are for httpS. the s is for secure.
If you are not doing secure you don't need that.

Its more likely your external IP and/or port forwarding.
Go to [http://canyouseeme.org/](http://canyouseeme.org/) check port 80.

---

### Post by joppuh123 on 2011-06-04
I would use wlraider70 its option

But you could also try to typ in your local IP and see if the site shows up and if you want to see the site externaly you need to forward port 80 on your router. If you typ in your router name + portforwarding in google you will find plenty of documentation

---

