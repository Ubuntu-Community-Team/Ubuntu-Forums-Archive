---
title: "help adding mod_alias module to apache2"
date: 2007-01-06
forum: Server Platforms
---

### Post by socktan on 2007-01-06
Hello all,

It took me 5 hours, but I did it.  I setup a LAMP server to help me develop my web site locally.  

There's one thing left that I need some help with.  I'm running gallery2 to manage my photos online.  Locally, paths are quite working correctly so images files are not displaying.   I think I am missing the alias module for Apache2.  None of the links work for the albums.  I successfully enabled mod_rewrite through a2enmod.  mod_alias does not exist in the mods-available directory though.  That's where I need help.

I googled, searched through the ubuntu forums and played around with apt-get and I still haven't found a way to add mod_alias to the mods-available so that I can enable it.

Here's a list of modules running in apache2 now:

> 
core mod_access mod_auth mod_log_config mod_logio mod_env mod_setenvif prefork http_core mod_mime mod_status mod_autoindex mod_negotiation mod_dir mod_alias mod_so mod_cgi mod_include mod_php5 mod_rewrite mod_userdir


Thanks in advance,

-
Chris.

---

### Post by scoon on 2007-01-06
Hey there, 

A work around for that could be to use mod_rewrite which you should have the module for.  [http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html]("http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html")

-scoon

---

### Post by logankoester on 2007-02-17
I realize this is an old thread but I'd like to point out that before assuming a module is not installed based on the contents of mods-available you should check the output of ```
apache2ctl -l
```
These modules are compiled in. In my case (apache2 on 5.10) mod_alias was compiled into apache, so I didn't find it where I expected to in mods-available. Cheers

---

