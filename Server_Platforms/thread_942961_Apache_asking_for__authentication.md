---
title: "Apache asking for  authentication"
date: 2008-10-09
forum: Server Platforms
---

### Post by kcg_ on 2008-10-09
Hello,

I have recently installed ubuntu server. When I open a browser and point it to the local address of the machine everything is ok, but when i give it my outside IP the browser then says " authentication required"

Any idea why this is happening?

Thanks!

kcg_

---

### Post by hrod beraht on 2008-10-09
Is that your router asking for authentication? Have you opened the appropriate port in your router to allow outside traffic through and pointed that traffic to your server's IP address? If not, all requests just hit the router and stop.

For example, for an Apache http server, your router should open port 80 and point it to IP 192.168.1.xxx (or whatever static address you gave to your server).

Bob

---

### Post by kcg_ on 2008-10-09
that was it! when I setup the new server, I never set up the port with it. 

thanks!

kcg_

---

