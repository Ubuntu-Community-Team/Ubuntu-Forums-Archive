---
title: "connection refused when attempting to...."
date: 2006-06-10
forum: Server Platforms
---

### Post by without_nick on 2006-06-10
I've recently tried to set up an Apache2 server on my Ubuntu, but I've met quite weird problem. I have a dynamic IP, so I registered for no-ip, the forwarded both port 80 and port 9999 to my pc (In the beginning I wanted only to have my server on 9999, but since I couldn't I did both) I wrote into apache2.conf, Listen 80 and Listen 9999, did the <VirtualHost> ... name, alias etc. It works perfectly on localhost, when 
[http://localhost:9999(:80](http://localhost:9999(:80)) and connects to apache. But when I try to connect to my server, from outside I get an error, "connection refused when attempting to contact mydomain.com" I, installed ssh, quite before I did Apache2, and ssh works perfectly both with domain, IP, and whatever. When I try to connect to apache using IP, www, without www (and all other combinations) it still doesn't work. I just can't connect from outside

Thanks for any help.

---

