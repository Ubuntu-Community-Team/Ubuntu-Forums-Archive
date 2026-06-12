---
title: "syntax error when test apache2 configuration"
date: 2012-07-22
forum: Server Platforms
---

### Post by associates on 2012-07-22
Hi,

I have just finished installing apache2-4.2 (latest stable version of apache) from scratch on my Ubuntu Server 12.04 32bit. After running the commands "./configure" and "make install" with no errors, my apache2 looked set to start. But then, I thought if I could just test its configuration before I started it by running the command
> /usr/local/apache2/bin/apachectl configtest

I got a syntax error with the message that says "on line 66 of /usr/local/apache2/conf/httpd.conf: cannot load /usr/local/apache2/modules/mod_authn_file.so into server: /usr/local/apache2/modules/mod_authn_file.so: cannot open shared object file: no such file or directory."

I wonder if anyone has encountered such an error when installing the latest stable version 2.4.2. What steps have I missed out?

Any help would be greatly appreciated. Thank you

---

