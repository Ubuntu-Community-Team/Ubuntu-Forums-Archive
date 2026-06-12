---
title: "Apache saying URL / not found on server"
date: 2012-01-28
forum: Server Platforms
---

### Post by stijnnoot on 2012-01-28
Hello guys,

Recently I started setting up a small server from an old unused desktop at home.
I installed Apache and did all the steps to make my server visible from outside the home network.
So i configured apache to listen to port 8080, i forwarded this port on my router.
Then i made a domain at no-ip.com called xxx.sytes.net , i chose the port 80 redirect and set the port number to 8080.
Now when i'm trying to view my server on the same network using the IP address of the server 192.168.x.x , there is no problem , i can see everything how it shoud be.
But when I type in xxx.sytes.net in my browser on another network i get the following error:

**Not Found**

 The requested URL / was not found on this server.
  Apache/2.2.16 (Ubuntu) Server at 84.192.x.x Port 8080


Is there something I'm missing?
Thanks in advance!

---

### Post by volkswagner on 2012-01-28
What do you get if you enter your external ip directly?

```
http://84.192.x.x:8080
```

Try this from outside you LAN if you can to verify you are not having NAT issues.  If you can try from a cellular network or use a free proxy such as hidemyass.com.

---

### Post by bcousins on 2012-01-29
> **stijnnoot said:**
> 
 The requested URL / was not found on this server.
  Apache/2.2.16 (Ubuntu) Server at 84.192.x.x Port 8080


Is there something I'm missing?


Is there a file at "/"?

---

