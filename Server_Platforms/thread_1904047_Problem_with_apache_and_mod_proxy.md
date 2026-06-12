---
title: "Problem with apache and mod_proxy"
date: 2012-01-03
forum: Server Platforms
---

### Post by gregor1410 on 2012-01-03
Hello.

I've a issue with mod_proxy in apache 2.3.16. Everything is looking to work correctly. I use server to ProxyPass data into 3 additional servers.

And in example if I pass data to server1 - all is OK. When I pass data to server2 it sometimes connect to server1. On debug apache log I've found someting like: connecting server1 , connected server2 . It looks like apache cache last connection and connect to last used server. Does anyone know how to repair this? Part of config:

<VirtualHost myhost:8080>
RewriteEngine On

RewriteRule /proxy/(.*) http://$1 [P]
ProxyRequests Off
ProxySourceAddress xxx.xxx.xxx.xxx
</VirtualHost>



And in example: if I put in browser:

[http://myhost/proxy/somehost.com](http://myhost/proxy/somehost.com) - I'm connecting to somehost.com

When I put to browser:

[http://myhost/proxy/otherhost.com](http://myhost/proxy/otherhost.com) - It sometimes connect me to otherhost.com and sometimes to somehost.com (used prevoriusly)

Please for help.

Regard's

Greg

---

