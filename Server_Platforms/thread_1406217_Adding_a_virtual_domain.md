---
title: "Adding a virtual domain"
date: 2010-02-13
forum: Server Platforms
---

### Post by Quenyar on 2010-02-13
I have had my server for years (LAMP Ubuntu Server) but now I have to add a second virtual domain to my Web server.  I followed the instructions here: 

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

but what I now get is that the main URL for the domain points to my server default page and not the root index file I specified.

HELP

I must be missing something somewhere. I can get to the content by entering the base URL plus the subdirectory off www that the domain root is located in.  Grrrrr.

Please also email answer to [email]hwm@goomba.com[/email]

Thanks

---

### Post by mbehamin on 2010-02-19
would you let us know what exactly configuration you add to your site-available directory !? and also try to look your log file with *tail -f /var/log/apache2/error.log *or *access.log  *to find what exactly happen when you requesting these website and then i can help you more

---

