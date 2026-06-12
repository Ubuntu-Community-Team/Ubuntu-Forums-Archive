---
title: "SIMPLE configuration of apache proxy?"
date: 2017-01-15
forum: Server Platforms
---

### Post by billsfdva on 2017-01-15
I have been pulling my hair out all week going through howto after howto and cannot get apache to serve static files with mezzanine. I have tried wsgi, I have tried without.
Right now this is what I have, no other config changes done to the server, simply trying to get it to proxy a site on the net. All I get is the default page. Please explain what I am missing. Thanks!

#This is for virtual host sites on server2 @ 192.168.1.3
<VirtualHost *:80>
        ServerAdmin [email]webmaster@domain.com[/email]
        ServerName myserver
# You can have list of space separated aliases if you server2 hosts multiple domains
        ServerAlias myserver
# If you have multiple hosts (NameVirtualHosts on server 2, you will need to preserve
# hostname, or you will always land at the root of
# the second server… ie: what ever the default site is.
        ProxyPreserveHost on
# Need to allow location / if you want the proxy to
# work when no folder is written in the url.
         <location />
          allow from all
     </location>

# This is where all the magic happens.
# You can modify the following for specific folders only and any remote host
# you can also specify a different port if you like
        ProxyPass / [http://wired.com/](http://wired.com/)
        ProxyPassReverse / [http://wired.com/](http://wired.com/)

</VirtualHost>

---

