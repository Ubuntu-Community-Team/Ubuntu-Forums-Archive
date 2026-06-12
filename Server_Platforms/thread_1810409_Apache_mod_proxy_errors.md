---
title: "Apache mod_proxy errors"
date: 2011-07-23
forum: Server Platforms
---

### Post by Orlando84 on 2011-07-23
all. I've just being wondering how to implement small jabber server in office and to install web-based frontend as client. So I've decided to install ejabberd + jwchat on Ubuntu server. Installed ejabberd and connecting through XMPP in Pidgin works fine. But for jwchat I've configured such vhost:
```
<VirtualHost *:80> 
ServerAdmin webmaster@localhost 
ServerName chat.orl.ua 
DocumentRoot /var/www/chat         
RewriteEngine On         
RewriteRule http-bind/ http://jabber.localhost:5280/http-bind/ [P] 
AddDefaultCharset UTF-8 
ProxyRequests Off 
ProxyPass /http-bind/ http://localhost:5280/http-bind/ keepalive=on 
ProxyPass /http-poll/ http://localhost:5280/http-poll/ keepalive=on 
ProxyPassReverse /http-bind http://localhost:5280/http-bind/ 
<Directory /var/www/chat/>     
Options Indexes FollowSymLinks MultiViews     
AllowOverride All     
Order allow,deny     
allow from all 
</Directory>  
ErrorLog ${APACHE_LOG_DIR}/chat_error.log  # Possible values include: debug, info, notice, warn, error, crit, # alert, emerg. LogLevel warn  
CustomLog ${APACHE_LOG_DIR}/chat_access.log combined
```So, I've tried both methods as http-poll, and http-bind but the chat_error.log says
```
[Sun Jul 17 16:59:30 2011] [warn] proxy: No protocol handler was valid for the URL /http-poll/. If you are using a DSO version of mod_proxy, make sure the proxy submodules are included in the configuration using LoadModule.

```So something is broken, I've found this thread [the same case[solved]]("http://ubuntuforums.org/showthread.php?t=1479485&highlight=ejabberd"), so can anyone explain what else I need to configure?

---

