---
title: "Apache +mod_rewrite:"
date: 2007-03-30
forum: Server Platforms
---

### Post by gustavo21ar on 2007-03-30
hi guys,

I have installed lamp in my localhost (Ubuntu 6.10). I need to activate  mod_rewrite for project:


root@cirkuit:/var/www#  sudo a2enmod rewrite

Module rewrite installed; run /etc/init.d/apache2 force-reload to enable.

root@cirkuit:/var/www#   /etc/init.d/apache2 force-reload

 * Forcing reload of apache 2.0 web server...   Syntax error on line 1 of /etc/apache2/mods-enabled/rewrite.load:
**Cannot load /usr/lib/apache2/modules/mod_rewrite.so into server: /usr/lib/apache2/modules/mod_rewrite.so: undefined symbol: ap_get_server_banner [fail] **

----------------------------------------------------------------------------------------------------------------------

root@cirkuit:/home/delirius# sudo a2enmod
Which module would you like to enable?
Your choices are: actions asis auth_anon auth_dbm auth_digest auth_ldap cache cern_meta cgid cgi dav_fs dav deflate disk_cache expires ext_filter file_cache headers imap include info ldap mem_cache mime_magic php5 proxy_connect proxy_ftp proxy_http proxy rewrite speling ssl suexec unique_id userdir usertrack vhost_alias
Module name? rewrite         
Module rewrite installed; run /etc/init.d/apache2 force-reload to enable.

root@cirkuit::/home/delirius# sudo /etc/init.d/apache2 force-reload
 * Forcing reload of apache 2.0 web server...                                                             [fail]

---

