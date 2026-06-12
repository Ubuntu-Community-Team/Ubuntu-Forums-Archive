---
title: "Setting up https on Ubuntu Hardy Heron (Ubuntu 8.04 LTS Server)"
date: 2008-06-21
forum: Server Platforms
---

### Post by ItsGambit on 2008-06-21
Hello, 

  I installed and set up Ubuntu Hardy Heron (Ubuntu 8.04 LTS Server)from this guide[http://www.howtoforge.org/perfect-server-ubuntu8.04-lts-p5]("http://www.howtoforge.org/perfect-server-ubuntu8.04-lts-p5") (Sorry if not external links are allowed...) I got everything to work but my problem is: 

a) getting https to work because it looks like enabled it.. 

b) getting phpmyadmin to run under https.

btw I am new to the server side of linux... 

Thanks in advance,
ItsGambit

---

### Post by RealPSL on 2008-06-23
You can take a look at the Server Guide here that briefly explains how to enable ssl/https for apache2.

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html")

---

### Post by windependence on 2008-06-24
You need to make sure port 443 is open and forwarded to your server on your router. Also, Apache needs to listen on that port.

Go to wwwcanyouseeme.org and test 443 to see if it's open.

-Tim

---

