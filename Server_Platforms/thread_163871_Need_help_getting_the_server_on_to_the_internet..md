---
title: "Need help getting the server on to the internet."
date: 2006-04-21
forum: Server Platforms
---

### Post by Nordoelum on 2006-04-21
Greetings,

I have just successfully configed an webserver that I can access through my private network. And that is going like a charm.

But when I try to access it through internet. It don't seam to connect. I am using no-ip.com and it is getting updated successfully with my ip. And I have confiugured the router to redirect to the server, when someone is accessing the outstanding ip adress. And the firewall is always disabled.

And I have noticed that ZPanel is detecting my apache server as not started. I find this very strange since I can access my serverf from my pm and it claiming I am using apache2 at the bottom of the fileviewer.

In the ports.conf I have:
```
Listen 80
```


Therefore I ask, is there anything else I need to do?

---

### Post by kthakore on 2006-04-22
If you have a permanent Ip address this usualy works in server when connecting to the net:

> Listen your_ip_address:80
if you are still haveing  problems open up network tools and run a port scan to find out what ports are running then choose a port number and do this

> 
Listen new_port
Listen you_ip_address:new_port


this will work but note to access from the net you have to type the port at the end of the url.

example:

> 
Listen 3455
Listen 127.0.0.1:3455


In the browers

> [http://127.0.0.1:3455/](http://127.0.0.1:3455/)

peace out and have fun

---

### Post by Nordoelum on 2006-04-22
Thank you :D

Will try it now..

---

