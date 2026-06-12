---
title: "Webmin Forgets - HELP -"
date: 2006-01-01
forum: Server Platforms
---

### Post by YaAqoB on 2006-01-01
Hello.
I'm trying to create a web server. First time at this so I thought I would give WebMin a  go.
This is all local and testing at the moment, not live on the web.
Using Apache2 & Webmin I have created 2  virtual servers (Haworthestate & invited)and if I go to [http://Ubuntu-Server](http://Ubuntu-Server) I get a directory listing, which I'm happy with as I don't have a website here.
If i go to [http://Ubuntu-server/haworthestate](http://Ubuntu-server/haworthestate) or /invited my webpages work fine.
Now if i stop the apache service and then start it again or restart my PC I start having issues.
If I go to [http://Ubuntu-Server](http://Ubuntu-Server) I no longer get a directory listing of the virtual servers I get the webpage of the next in line virtual server ie the invited webpage. If i go to [http://Ubuntu-Server/haworthestate](http://Ubuntu-Server/haworthestate) or /invited I get an error as follows:
The requested URL /haworthestate was not found on this server.

If i delete the virtual servers and then create them again they work fine untill the next reboot and apache restart.
Anyone have any ideas??

---

### Post by YaAqoB on 2006-01-02
Actually... If it was configured correctly should I be able to access it from [http://haworthestate/](http://haworthestate/)      ?? Or would I have to have the Ubuntu-Server there aswell?

Cheers

---

