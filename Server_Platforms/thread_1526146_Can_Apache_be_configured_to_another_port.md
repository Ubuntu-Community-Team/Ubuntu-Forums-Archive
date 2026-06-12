---
title: "Can Apache be configured to another port?"
date: 2010-07-07
forum: Server Platforms
---

### Post by redfox1160 on 2010-07-07
I have an ISP that blocks ports 80 and 8080, and I was wondering if I could use another port to host a website. What port could I use (if any), and would it cause any problems? Thanks!

---

### Post by arrrghhh on 2010-07-07
You can pick any port, it's just there are several established ports.  Every port up to 1024 is "reserved" so-to-speak, so I would pick something above 1024.  

[http://ubuntuforums.org/showthread.php?t=525847](http://ubuntuforums.org/showthread.php?t=525847) - Second post has the answer.  Just be sure to copy your ports.conf to ports.conf.bak or something like that to back up the original in case you bungle something.  Also, be sure to restart apache after the change.

---

### Post by stlsaint on 2010-07-07
Yes you can set the apache.conf for whatever port you specify. Then make sure that you setup port forwarding to that port. Then who ever you got your domain through...IE: godaddy.com....you need to setup a port redirect from 80 to whatever port you configured.

---

### Post by redfox1160 on 2010-07-07
Are there any ports that you would recommend? Would a higher port be better? Any suggestions would be appreciated. Also, would this effect my connection in any way?

---

### Post by Iowan on 2010-07-07
I had a router/firewall that used port 80 for it's own mini-webserver, and port 81 for configuration.

---

### Post by arrrghhh on 2010-07-07
> **redfox1160 said:**
> Are there any ports that you would recommend? Would a higher port be better? Any suggestions would be appreciated. Also, would this effect my connection in any way?

As I said earlier, you can use any port.  The ones below 1024 are "reserved", but no body says you can't use them.  ISPs are less likely to block stuff above 1024 as well.  Won't effect the connection speed... but to go to your website it won't be possible to just type in the address.  It'll be [www.webaddress.com:9000](www.webaddress.com:9000) - assuming your website is on port 9000.

> **stlsaint said:**
> Yes you can set the apache.conf for whatever port you specify. Then make sure that you setup port forwarding to that port. Then who ever you got your domain through...IE: godaddy.com....you need to setup a port redirect from 80 to whatever port you configured.

Please don't give contradicting mis-information.  The file is /etc/apache2/ports.conf... You CANNOT set the port # in the apache.conf.  Why would you post that you edit the apache.conf?

---

