---
title: "httpd.conf not working after upgrade to 9.04"
date: 2010-05-07
forum: Server Platforms
---

### Post by MalcolmCowen on 2010-05-07
Any changes in the way httpd.conf works in 9.04?   

Yesterday I updated from 8.04 to 8.10 and then to 9.04.  All works fine, except for Apache Virtual sites.

I had several defined in my httpd.conf file, which I used for testing clients' websites.

Since the upgrade the virtual sites are not recognised, and all access is done at the original level /var/www.

Any changes in the way httpd.conf works?   
I checked the Apache docs, but found nothing.

Here's the httpd.conf I've been using: 

<Directory /var/www/clientname/htdocs/products>
AllowOverride All
</Directory>

NameVirtualHost *

<VirtualHost *>
  ServerName wiki.local
  ServerAlias *.wiki.local
  DocumentRoot /var/www/wiki/htdocs
</VirtualHost>  

<VirtualHost *>
  ServerName joomla.local
  ServerAlias *.joomla.local
  DocumentRoot /var/www/joomla/htdocs
</VirtualHost>  

<VirtualHost *>
  ServerName wordpress.local
  ServerAlias *.wordpress.local
  DocumentRoot /var/www/wordpress/htdocs
</VirtualHost>

---

### Post by DaF1oh1 on 2010-05-07
What version of Apache are you running?

---

### Post by TheFuturian on 2010-05-08
```
apt-cache policy apache2
```

---

### Post by MalcolmCowen on 2010-05-08
My versions info is
System  Linux Pearl 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686  
Build Date  Jan 6 2010 21:56:40  
**Server API  Apache 2.0 Handler**  

apache2handler
**Apache Version  Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch  **Apache API Version  20051115  
Server Administrator  webmaster@localhost  
Hostname:Port  127.0.1.1:80  
User/Group  mc(1000)/1000  
Max Requests  Per Child: 0 - Keep Alive: on - Max Per Connection: 100  
Timeouts  Connection: 300 - Keep-Alive: 15  
Virtual Server  Yes  
Server Root  /etc/apache2  
Loaded Modules  core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_dir mod_env mod_mime mod_negotiation mod_php5 mod_setenvif mod_status  

Directive Local Value Master Value 
engine 1 1 
last_modified 0 0 
xbithack 0 0 


Apache Environment
Variable Value 
HTTP_ACCEPT  */*  
HTTP_ACCEPT_LANGUAGE  en-gb  
HTTP_USER_AGENT  Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.1; Trident/4.0; .NET CLR 2.0.50727; .NET CLR 3.0.4506.2152; .NET CLR 3.5.30729; .NET CLR 1.1.4322)  
HTTP_ACCEPT_ENCODING  gzip, deflate  
HTTP_HOST  wiki.local  
HTTP_CONNECTION  Keep-Alive  
HTTP_COOKIE  wiki_Csw_UserID=2; wiki_Csw_UserName=Mc  
PATH  /usr/local/bin:/usr/bin:/bin  
SERVER_SIGNATURE  <address>Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch Server at wiki.local Port 80</address>  
SERVER_SOFTWARE  Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch  
SERVER_NAME  wiki.local  
SERVER_ADDR  192.168.0.3  
SERVER_PORT  80  
REMOTE_ADDR  192.168.0.4  
DOCUMENT_ROOT  /var/www  
SERVER_ADMIN  webmaster@localhost  
SCRIPT_FILENAME  /var/www/phpinfo.php  
REMOTE_PORT  4905  
GATEWAY_INTERFACE  CGI/1.1  
SERVER_PROTOCOL  HTTP/1.1  
REQUEST_METHOD  GET  
QUERY_STRING  no value  
REQUEST_URI  /phpinfo.php  
SCRIPT_NAME  /phpinfo.php

---

### Post by MalcolmCowen on 2010-05-08
I ran apt-cache:

mc@Pearl:~$ apt-cache policy apache2
apache2:
  Installed: (none)
  Candidate: 2.2.11-2ubuntu2.6
  Version table:
     2.2.11-2ubuntu2.6 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-security/main Packages
     2.2.11-2ubuntu2 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages
mc@Pearl:~$ 


Does that help?

---

