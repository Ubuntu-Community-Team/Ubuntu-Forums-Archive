---
title: "Bind DNS and Apache Question"
date: 2011-05-10
forum: Server Platforms
---

### Post by znima2006 on 2011-05-10
I was  wondering if anyone knows how to make a zone file for bind dns server  that points "example.com" and all (by all i mean any) sub-domains to  this 127.0.0.1 address.
 
and i wanted to set up a virtual host in apache to use /var/www/eample/index.php for 'example.com' and all of its sub-domains

thanks a lot

---

### Post by hawkmage on 2011-05-11
I am not sure why you want it to resolve to the loopback address but you may want to try adding the following two lines to the zone file:

@ IN A 127.0.0.1
* IN A 127.0.0.1

---

