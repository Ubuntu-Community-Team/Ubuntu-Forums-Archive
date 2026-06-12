---
title: "mysql having problems"
date: 2007-04-10
forum: Server Platforms
---

### Post by bobjr777 on 2007-04-10
mysql is working fine but its not listening on port 3306. i want to use java with mysql and it wont connect. apache works fine
any sugestions

---

### Post by DoorGunner on 2007-04-10
you may need to go to the mysql site. It has been my experience that it is more specialized to mysql issues. 

just a suggestion:(

---

### Post by bobjr777 on 2007-04-10
i got it working by editing the my.conf file
but now i get
SQLException: Access denied for user 'root'@'192.168.0.2' (using password: YES)
SQLState: 28000
VendorError: 1045
im at 192.168.0.2 and my server 192.168.0.5
the pass i supplyed is correct



edit fixed by 
GRANT ALL PRIVILEGES ON test.* TO 'root'@'192.168.0.2' IDENTIFIED BY 'passward'

---

### Post by jaheds on 2007-04-11
It's probably the case that the user "root" is only allowed access from localhost, and you're being denied access because your authenticating from "192.168.0.5" instead of "localhost"

If you truly need access to mysql from a different host, see the MySQL docs on their web-site to see how to give certain users such access.  It's a really good idea not to give "root" such access.

If "192.168.0.5" is actually your MySQL machine, don't access it using the IP 192.168.0.5 (or the name that resolves to that);  instead use the IP 127.0.0.1 (or the name "localhost" which resolves to that)

Good luck.

---

