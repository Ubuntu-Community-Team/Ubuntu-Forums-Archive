---
title: "Active webistes on Apache2 server"
date: 2011-01-23
forum: Server Platforms
---

### Post by MatsB on 2011-01-23
How can I see what websites are active on my Apache2 server and what url and/or port respectively site uses?

---

### Post by kgatan on 2011-01-23
You can see all active sites under the folder /etc/apache2/sites-enabled/

---

### Post by MatsB on 2011-01-23
> **kgatan said:**
> You can see all active sites under the folder /etc/apache2/sites-enabled/

Thanks, but that doesn't list all sites available in Apache2? It seems that I have sites in /var/www as well. Is there anymore places I should look for? I know Cacti is installed on this server but I can't seem to find the website in any directory.

Let me rephrase my question. Is there any easy way to list all available websites on a Ubuntu/Apache2 server instead of looking through all sorts of directories?

---

### Post by James78 on 2011-01-23
Enabled sites: /etc/apache2/sites-enabled
Available sites: /etc/apache2/sites-available ;)

You'll might have to look through the Virtualhosts and configurations to see anything useful. If you're looking for where to access a webapp you installed automatically, it'll probably be in /etc/apache2/conf.d instead. Just look through all the configurations in /etc/apache2 and you should fine what you're looking for eventually.
```
ls /etc/apache2/sites-available
```

---

### Post by volkswagner on 2011-01-23
kgatan is correct.  If your server is using virtual hosts to allow multiple websites.

As kgatan pointed out the configuration files are located in sites-enabled for active sites.  Sites that aren't enabled are under /etc/apache2/sites-available.

The administrator can put web directories anywhere on the system such as /var/www or /home/username, etc.

The configuration files will explicitly spell out the root directory for the site, there for should give you the info you need.

I'm sorry I don't know of any easy tool to check for all sites.  You could write a script to check the contents of all files under /etc/apache2/sites-enabled for the line "DocumentRoot" and/or "<Directory /*>".

What makes this difficult if your not using virtual hosts but using just sub directories.  You can have sites using a directory tree inside one domain, such as [www.domain.com/index.html](www.domain.com/index.html), [www.domain.com/blog](www.domain.com/blog), [www.domain.com/shopping](www.domain.com/shopping), [www.domain.com/blog/forum](www.domain.com/blog/forum), etc.  With the above setup, you could have numerous sites with one configuration file.  You may need a spyder engine, see how google does it....

With mixed environments and variables, it would be difficult to easily parse the numerous sites.

---

### Post by MatsB on 2011-01-23
Thx to both James78 and volkswagner.

You've made it a bit more clear how Apache2 handles its websites.

---

