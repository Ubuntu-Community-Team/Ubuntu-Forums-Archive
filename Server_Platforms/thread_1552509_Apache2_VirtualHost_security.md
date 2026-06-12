---
title: "Apache2 VirtualHost security"
date: 2010-08-13
forum: Server Platforms
---

### Post by rwslippey on 2010-08-13
I have a server setup at home with which I'd like to do a few things....

I've got 4 sites now, their may be more later on....

1 of which I don't want to allow external access (web access from the internet)  I want to block external access and only allow access from my LAN and my VPN (which is on the same server, and currently not functioning correctly right now... but thats a different story.

I'm not even sure how to go about this. I currecntly have the server configured via NameVirtualHost...

Any help is as always greatly apprciated.

Rob

---

### Post by Bachstelze on 2010-08-13
You need something like:

```
<Directory /root/of/lan/only/site>
        Order Allow,Deny
        Allow from 192.168.0.*
</Directory>

```

Of course, replace 192.168.0.* by the address pattern you use on your LAN.

---

