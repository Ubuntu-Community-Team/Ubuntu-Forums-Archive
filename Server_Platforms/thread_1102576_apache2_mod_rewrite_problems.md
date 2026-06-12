---
title: "apache2 mod_rewrite problems"
date: 2009-03-21
forum: Server Platforms
---

### Post by derlupo on 2009-03-21
Hey Guys,

i've tried for hours now, and searched the web but still cant find a solution. I hope you can help me.

I just can't get that mod_rewrite to do anything :(

I set RewriteLogLevel to 9 and get not a single message in my rewrite log.

mod_proxy, mod_proxy_http and mod_rewrite are loaded, at least phpinfo() is telling me so.


```
   
ProxyPreserveHost On
RewriteEngine On
RewriteLog "/var/log/apache2/rewrite.log"
RewriteLogLevel 9

# this is just a test to get ANY rewrite working once
# it should rewrite http://myserver.com/test to
# http://myserver.com/forum
RewriteRule ^/test(.*)$ /forum$1

# this is the actual rule i want to have in the end .. 
# it should pass any requests to http://myserver.com/jboss/* 
# to the local jboss running at http://localhost:8080
# kinda like a reverse proxy
RewriteRule ^/jboss/(.*)$ http://localhost:8080/$1 [P]

```

I played around with the rules and placed this snippet at several places in my VirtualHost config, and even in apache2.conf

I don't see a single line in the redirect.log and the error log keeps saying:
File does not exist: /var/www/vhosts/default/htdocs/jboss
File does not exist: /var/www/vhosts/default/htdocs/test


Any ideas what im doing wrong?

Thanks in advance,
lupo

---

### Post by derlupo on 2009-03-22
*bump*

Can anyone help me with this issue?
What could I check to find the error?

Sorry I'm quite new to that stuff :(

Thanks,
lupo

---

### Post by derlupo on 2009-03-28
Ok, I finally solved it.
I was editing the wrong VirtualHost entry :lolflag:

There was another one defined within conf.d and some cryptic filename.. 

At least now I know how my provider's default config is set up :)

---

