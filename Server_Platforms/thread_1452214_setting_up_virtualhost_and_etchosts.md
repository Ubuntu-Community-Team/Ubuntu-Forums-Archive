---
title: "setting up virtualhost and /etc/hosts"
date: 2010-04-11
forum: Server Platforms
---

### Post by HyperFlexed on 2010-04-11
Hi, I've set up apache2, but I'm having trouble getting virtual hosts to work

my /etc/hosts

```
127.0.0.1	localhost
127.0.1.1	johnny-desktop

127.0.0.1	go

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

my /etc/apache2/httpd.conf

```
NameVirtualHost *

<VirtualHost *>
        DocumentRoot /var/www
        ServerName localhost
</VirtualHost>

<VirtualHost *>
        DocumentRoot /var/www/go/htdocs
        ServerName go
</VirtualHost>
```

When I visit **[http://localhost](http://localhost)** I get /var/www/
When I visit **[http://go](http://go)** I get /var/www/go/htdocs/

The problem is when I visit **[http://127.0.0.1](http://127.0.0.1)** I get the contents of /var/www/go/htdocs/. I want /var/www/ instead. Any idea? Let me know if you need more information.

---

### Post by Ryan Dwyer on 2010-04-11
Switch the VirtualHost containers so the go host comes before localhost.

If none of the hosts match, Apache serves the first host which is also known as the default host.

---

### Post by HyperFlexed on 2010-04-11
> **Ryan Dwyer said:**
> Switch the VirtualHost containers so the go host comes before localhost.

If none of the hosts match, Apache serves the first host which is also known as the default host.

by that logic, wouldn't I want localhost at the top? (so that if nothing matches, /var/www is served?)

EDIT: for some strange reason everything seems to be working now. Maybe I had a caching issue.

---

