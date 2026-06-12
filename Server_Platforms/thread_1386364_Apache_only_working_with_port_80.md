---
title: "Apache only working with port 80"
date: 2010-01-20
forum: Server Platforms
---

### Post by Beige on 2010-01-20
Having some trouble with Apache.

I have a virtual server setup on port 80 that works fine, however, if I change the port to, say, 8080 the browser then fails to connect.

I'm using webmin to configure everything, all the other settings seem to work as I would expect.


I get the error "Safari can’t open the page “[http://192.168.0.12:8080/”](http://192.168.0.12:8080/”) because Safari can’t connect to the server “192.168.0.12”." in safari, and i get something similar on the xubuntu machine in firefox connecting via localhost.


It's almost as though theres a firewall in the way, but I think it's more likely to be some config problem.

---

### Post by pirateghost on 2010-01-20
make sure that your /etc/apache2/ports.conf has 
Listen 80
Listen 8080

---

### Post by Beige on 2010-01-21
You know, I even looked at that file, but for some reason completely missed the port number, best not to play so late at night :P

---

