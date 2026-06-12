---
title: "time out issue when accessing websites via lan"
date: 2016-04-11
forum: Virtualisation
---

### Post by ghmercado on 2016-04-11
I setup LAMPP and virtual hosts on my Ubuntu 14.04 with lan ip 192.168.0.106.

I set up two websites with directories /srv/www/d6/public_html and /srv/www/d7/public_html. 

here is the contents of /etc/apache2/sites-available/d6.com.conf. The d7.com.conf is similar just edited for d7.
```
# domain: example.com
# public: /srv/www/d6/public_html/

<VirtualHost 192.168.0.106>
  # Admin email, Server Name (domain name), and any aliases
  ServerAdmin someemail@email.com
  ServerName  d6.local
  ServerAlias www.d6.local

  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.html index.php
  DocumentRoot /srv/www/d6/public_html/
  # Log file locations
  LogLevel warn
  ErrorLog  /srv/www/d6/log/error.log
  CustomLog /srv/www/d6/log/access.log combined
</VirtualHost>
```

when I access from the local machine both websites on d6 and d7 load fine.

when i access via my win7 PC on the same lan nothing loads then it times out. But when I enter 192.168.0.106 I get the site on d6 quickly and normally.

here is my ubuntu etc/hosts file:
```
127.0.0.1       localhost
127.0.0.1       d6.local
127.0.0.1       d7.local
192.168.0.106   d6.local
192.168.0.106   d7.local
```

I placed these on my win7 host file:
```
192.168.1.106   d6.local
192.168.1.106   d7.local
```

when I ping either i get:

```
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\whut>ping d7.local

Pinging d7.local [192.168.1.106] with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
```

why does it time out? 
any hints appreciated tia.

---

### Post by TheFu on 2016-04-11
If Windows cannot ping the ubuntu machine, that is the first issue to solve.  Does the router/firewall block pings?  

If you are using the same IP for multiple websites, you must use name-based apache resolution - that means the virtual hostname must be in the config files, not the IP.  [https://httpd.apache.org/docs/current/vhosts/name-based.html](https://httpd.apache.org/docs/current/vhosts/name-based.html)  Note the *:80?

By default, apache doesn't listen on the main interface, so you'll need to modify the apache.conf file (or where ever that setting is) to listen on whatever the interface name is - often eth0, but it could have other names.   We don't use apache much anymore, so I don't recall the exact location of that setting - look for "listen" in all the conf files.  [https://httpd.apache.org/docs/trunk/bind.html](https://httpd.apache.org/docs/trunk/bind.html) explains.

Anyway, hope this helps with exact solutions.

---

### Post by SeijiSensei on 2016-04-11
I don't know why the Windows host file does not work, but you clearly have a name resolution problem on the Windows side.  It may not handle multiple entries with the same IP address correctly.  Try this in Windows:
```
192.168.1.106   d6.local d7.local d6 d7
```
and deleting the second entry.  If neither of the .local names work correctly, does it work with just "ping d6" and "ping d7"?

---

### Post by ghmercado on 2016-04-11
you are absolutely right the issue was in my win host file.

the correct IP address is 192.168.0.106
the ip address i placed in the host file is 192.168.1.106

works ok now. i have my eagle eyed friend to thank for that.

---

