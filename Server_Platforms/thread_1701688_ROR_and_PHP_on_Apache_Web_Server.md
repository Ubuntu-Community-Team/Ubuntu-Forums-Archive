---
title: "ROR and PHP on Apache Web Server"
date: 2011-03-06
forum: Server Platforms
---

### Post by Z.K. on 2011-03-06
I would like to add ROR to my web server, but I would still like to keep php.  I tried doing this a few days ago, but it made my PHP unusable so that it would ask me to download a file rather than displaying the php page.  I was wondering if anyone had a good tutorial on how to install ruby on rails without trashing my system again.

---

### Post by wongo888 on 2011-03-08
These fellows claim to be able to run RoR using Passenger and PHP at the same time.

[http://bit.ly/gs1WkX](http://bit.ly/gs1WkX)

I haven't tried it personally. Maybe you can try it and report back.

---

### Post by rubylaser on 2011-03-08
Passenger works great.  I have 10 Rails vhosts ,and 2 Wordpress vhosts with no problem.  Here's about all you need in a vhost file for each.

PHP site...
```
<VirtualHost *:80>
    ServerName fqdn.hostname.com
    DocumentRoot /var/www/wordpress/
</VirtualHost>

```

Rails app...
```
<VirtualHost *:80>
    ServerName fqdn.hostname.com
    DocumentRoot /var/www/website/public/
</VirtualHost>
```

Setting up Passenger is dead simple on Ubuntu, and they have on their website.
[http://www.modrails.com/install.html]("http://www.modrails.com/install.html")

---

### Post by Z.K. on 2011-03-10
> **wongo888 said:**
> These fellows claim to be able to run RoR using Passenger and PHP at the same time.

[http://bit.ly/gs1WkX](http://bit.ly/gs1WkX)

I haven't tried it personally. Maybe you can try it and report back.

Thanks, this might be what I am looking for.

---

