---
title: "Squid - Traffic priority port-based"
date: 2006-10-10
forum: Server Platforms
---

### Post by salvo1 on 2006-10-10
hi guys,
I've ubuntu dapper on a PC that we're using as mailserver, fax server, webserver and, above all, proxy server (with squid).

All is used by webmin ([www.webmin.com)](www.webmin.com)).

Now, i want to assign different priorities to internet traffic. Here, in office, we've a really slow internet connection, 120 PCs connected

How can i assign different priorities to the traffic? Can i do it using different ports? For example:
1. Are there FTP trasferts (port 21)? They're at first place!
2. Else.. are there SMTP/POP3 Trasferts (port 25)? They're at 1st place!
3. Else, HTTP traffic (port 80)
4. Default

The best thing will be a dinamic assignation.. but I can do it also static:
1. Traffic FTP: 10kb/s
2. Traffic SMTP: 25kb/s
3. Traffico HTTP: 50kb/s

---

