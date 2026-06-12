---
title: "webmin remote access"
date: 2008-09-27
forum: Server Platforms
---

### Post by baudday on 2008-09-27
How can I access webmin remotely? For instance, I can got to my.ip:10000 on the local machine and access it easily. But I'm at college and it's annoying to have to VNC every time just to see webmin. I wanna access it through my browser on my machine here. I appreciate any help.

---

### Post by jamesrfla on 2008-09-27
You need to port forward port 443 and 10000 in your router. Do you have a dyndns yet or some kinda of web address? Let me know if this works.

---

### Post by baudday on 2008-09-28
I have a URL and I have a website on the server. So just forward the ports? How would I access it then?

---

### Post by jamesrfla on 2008-09-28
Yes, all you need to do is port forward port 443 (HTTPS) and port 10000 (webmin). If you have VNC working you shouldn't have any problems like having a static ip address for your server inside your network.

---

### Post by baudday on 2008-09-28
Okay thanks, that worked, however I did not have to open 443. Which was nice. I now access it with [http://myurl.com:10000](http://myurl.com:10000)

---

### Post by jamesrfla on 2008-09-28
I wasn't sure if you had to or not. Now I know so I can do it with my server.

---

