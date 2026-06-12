---
title: "ERROR 1045 (28000): Access denied for user"
date: 2014-09-15
forum: Server Platforms
---

### Post by said5 on 2014-09-15
Recently when I was moving a database from justhost to godady I did the usual mysql dump from command line, then tried to import it on the new server, but
When i used to this code
[SIZE=4]```
**[COLOR=#ff0000]mysql -database.name -mydomain.com -p[/COLOR]**
``` then[/SIZE]
An error -ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
When i used to this code 
[SIZE=4]```
**[COLOR=#ff0000]mysql -udatabase.name -hmydomain.com -p[/COLOR]**
``` then[/SIZE]
ERROR 1130 (HY000): Host 'ip-50-62-60-187.ip.secureserver.net' is not allowed to connect to this MySQL server

How can i connect mysql with putty and import my 450 mb sql database ?? 

Thank you

---

