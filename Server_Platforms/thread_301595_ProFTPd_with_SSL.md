---
title: "ProFTPd with SSL"
date: 2006-11-17
forum: Server Platforms
---

### Post by Chillster on 2006-11-17
I installed proftpd using this guide [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) and it works great. 

However i wanted to get it working with ssl/tls. But it seems like the module i need isnt included "mod_tls" how can i fix this?

---

### Post by dataw0lf on 2006-11-17
From the link you provided, it seems to have instructions to install mod_tls.  Looks like it requires you to build it yourself.

---

### Post by dannyboy79 on 2006-11-17
yeah, i pointed this out here ([http://www.ubuntuforums.org/showthread.php?t=286147&highlight=proftpd)](http://www.ubuntuforums.org/showthread.php?t=286147&highlight=proftpd)). if you're using edgy, amybe there is some way to install the version that's in the dapper repo's or yes, you have to compile it yoruself. I have already compiled it. i have a .deb file from using checkinstall. I wonder if could somehow put it somewhere for people? i compiled it with pretty much everything except mod_sql and mod_sql_mysql which is why most people will not this deb that I have since I think  a lot folks do auth thru sql.

proftpd -vl
Compiled-in modules:
  mod_core.c
  mod_xfer.c
  mod_auth_unix.c
  mod_auth_file.c
  mod_auth.c
  mod_ls.c
  mod_log.c
  mod_site.c
  mod_delay.c
  mod_tls.c
  mod_ifsession.c
  mod_quotatab.c
  mod_quotatab_file.c
  mod_ratio.c
  mod_load.c
  mod_rewrite.c
  mod_readme.c
  mod_cap.c

---

### Post by Chillster on 2006-11-17
Yea im using edgy, is there anyway you could send me that .deb file? would really make it a hell of alot easier for me :)

---

### Post by dannyboy79 on 2006-11-21
> **Chillster said:**
> Yea im using edgy, is there anyway you could send me that .deb file? would really make it a hell of alot easier for me :)

i sent it to you and asked you a question since. Can you please answer me?? I need to know if you have gotten your ftp server to work with mod_tls or not??? I can't seem to get it to work. I get an error that states that mod_tls/blah couldn't use key in server.crt or something along those line??? I use frodons guide for creating the self signed keys or certificates, whatever you want to call them? Then after that, even if I comment out the mod_tls stuff in the proftpd.conf and restart xinetd (i run my server thru this instead of standalone) my server will not accept any connections no matter what. I have to actually shut my machine off and on again  and then finally the server will allow connections?? I wonder if I compiled it incorrectly. This is the first thing that I have built from source. This is what I used at configure time.

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --with-modules=mod_tls:mod_ifsession:mod_quo                       tatab:mod_quotatab_file:mod_ratio:mod_load:mod_rewrite:mod_readme


Can anyone help me with this???

---

