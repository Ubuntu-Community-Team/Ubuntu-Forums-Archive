---
title: "Webmin via Apache proxy"
date: 2011-03-30
forum: Server Platforms
---

### Post by tangerine0469 on 2011-03-30
Either I missed something or I eff'd something up...it's probably the latter...

I have installed webmin and can access it from my local network, when i try to configure it as a virtual server via Mod_proxy i have gotten a number of errors. i have searched both the forum and the web only to break through 1 brick wall only to hit another.

my current virtual host config is:

<VirtualHost *:80>
ServerAlias webmin.computercrasherz.com
ProxyPass / [http://localhost:10000/](http://localhost:10000/)
ProxyPassReverse / [http://localhost:10000/](http://localhost:10000/)
<Proxy *>
allow from all
</Proxy>
</VirtualHost>

and my proxy setting is:

<IfModule mod_proxy.c>

# If you want to use apache2 as a forward proxy, uncomment the
# 'ProxyRequests On' line and the <Proxy *> block below.
# WARNING: Be careful to restrict access inside the <Proxy *> block.
# Open proxy servers are dangerous both to your network and to the
# Internet at large.
#
# If you only want to use apache2 as a reverse proxy/gateway in
# front of some web application server, you DON'T need
# 'ProxyRequests On'.

#ProxyRequests On
#<Proxy *>
#        AddDefaultCharset off
#        Order deny,allow
#        Deny from all
#        #Allow from .example.com
#</Proxy>

# Enable/disable the handling of HTTP/1.1 "Via:" headers.
# ("Full" adds the server version; "Block" removes all outgoing Via: headers)
# Set to one of: Off | On | Full | Block
#ProxyVia Off

</IfModule>

and lastly the error messages i get in /var/log/apache2/error.log are:

[Wed Mar 30 10:55:03 2011] [error] (111)Connection refused: proxy: HTTP: attempt to connect to 127.0.0.1:10000 (localhost) failed
[Wed Mar 30 10:55:03 2011] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Wed Mar 30 10:55:05 2011] [error] proxy: HTTP: disabled connection for (localhost)

and a 503 Service Temporarily Unavailable on the browser trying to connect.

Any thought as to why this is happening?

Edit: i am running ubuntu server 10.10. i have it currently setup as a lamp/email server (both working).

---

### Post by kgeekworking on 2011-03-30
Webmin normally runs as https with a self generated cert. You will likely have to make some changes to the Webmin configuration to use regular http.

The Webmin website mentions that you have to make some changes to the webmin configuration in order to run with a proxy.

[http://www.webmin.com/apache.html](http://www.webmin.com/apache.html)

---

### Post by tangerine0469 on 2011-03-30
Its funny how when you finally break down and ask for help you figure out what you did wrong or missed... thank you for pointing me back to that page! 

what they didn't cover in that page is to edit the  "/etc/webmin/miniserv.conf" file. the line "ssl=1" should be changed to "ssl="

and in "/etc/apache2/mods-enabled/proxy.conf" file you need uncomment the proxy section like this:

<Proxy *>
        AddDefaultCharset off
        Order deny,allow
        Deny from all
        #Allow from .example.com
</Proxy>

then restart both webmin and apache and it works for me.
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/webmin restart

---

### Post by a2j on 2011-06-15
> **tangerine0469 said:**
> 

what they didn't cover in that page is to edit the  "/etc/webmin/miniserv.conf" file. the line "ssl=1" should be changed to "ssl="


and what about password sniffers, etc...?

disabling ssl fixes the issue, but at the cost of less/no security. 
does proxy mod makes it more secure? or how can it be done more secure?

---

