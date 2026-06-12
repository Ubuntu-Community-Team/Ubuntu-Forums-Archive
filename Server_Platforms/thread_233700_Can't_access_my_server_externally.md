---
title: "Can't access my server externally"
date: 2006-08-10
forum: Server Platforms
---

### Post by cexar on 2006-08-10
Hi.
I have apache2 on my box, and i want to mount a
webserver for the compny employees.
We have a domain name, "www.latiendaweb.com" (just an
example) and i want to make my server
"www1.latiendaweb.com" i add in the sites-available
folder, in default file, a section called virtual
server athe endo of file, i forwarded my USR-8054
Router port 80 to my local server (its ok from my LAN,
but not externally).
The results? not working. i add too the server address
in a no-ip domain, but still not working
any idea?.
i paste some code  the rest of code is the default
code.
....
</VirtualHost>
<VirtualHost *>
ServerName www1.latiendaweb.com
DocumentRoot /var/www
DirectoryIndex index.html index.htm index.php
index.shtml
</VirtualHost>

if u can help me, i will be very thankfully
thanks.

---

