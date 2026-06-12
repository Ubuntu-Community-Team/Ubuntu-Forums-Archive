---
title: "Apache Virtual Hosts"
date: 2008-12-04
forum: Server Platforms
---

### Post by Drezard on 2008-12-04
Trying to get Virtual Hosts working in Apache2. Apache works perfectly when I use a default installation and such (It displays It works).

Now modifying the configuration a little bit. I want set up apache so when I type:
- [www.mydomain.com:80](www.mydomain.com:80) it pops up with /var/www/80/
- [www.mydomain.com:8080](www.mydomain.com:8080) it pops up with /var/www/8080/

Now, first off I modified the ports.conf to look like this:
> 
Listen <ipaddress>:80
Listen <ipaddress>:8080

(Replaced <ipaddress> with my actual IP address)

I then modified my /etc/apache2/sites-enabled/ by deleting 000-default and then creating a new file in there called mydomain.com. In mydomain.com, I put this:

> 
NameVirtualHost <ipaddress>:80
NameVirtualHost <ipaddress>:8080

<VirtualHost <ipaddress>:80>
    ServerName [www.mydomain.com:80](www.mydomain.com:80)
    DocumentRoot /var/www/80/
</VirtualHost>

<VirtualHost <ipaddress>:8080>
    ServerName [www.mydomain.com:8080](www.mydomain.com:8080)
    DocumentRoot /var/www/8080/
</VirtualHost>


And Ive created both directories (/var/www/80/ and /var/www/8080/). Then I restarted apache using '/etc/init.d/apache2 restart'. Worked perfectly.

So done all that and now when I goto [www.mydomain.com:80](www.mydomain.com:80), it works perfectly (goes to the /80/) but when I goto [www.mydomain.com:8080](www.mydomain.com:8080), it says: 
> 
Not Found

The requested URL / was not found on this server.


What have I done wrong?

Daniel

---

### Post by MJN on 2008-12-04
Is there a file in /var/www/8080/ ? (Specifically, one that matches one of the DirectoryIndex files)
 
If there is, what happens when you ask for that specific file, e.g. [http://www.mydomain.com:8080/index.htm](http://www.mydomain.com:8080/index.htm) ?
 
Mathew

---

