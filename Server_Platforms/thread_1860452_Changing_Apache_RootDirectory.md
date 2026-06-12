---
title: "Changing Apache RootDirectory"
date: 2011-10-14
forum: Server Platforms
---

### Post by MysteryX on 2011-10-14
Hi, I have an Apache server set-up on Ubuntu and everything is working perfectly with several domains.

There are config files in /etc/apache2/sites-available for each additional domain and they are working properly.
> <VirtualHost *:80>
  ServerName [www.uchangefromwithin.com](www.uchangefromwithin.com)
  ServerAlias uchangefromwithin.com
  DocumentRoot /var/www/uchangefromwithin
</VirtualHost>

The main domain is currently configured in /etc/apache2/sites-available/default where I set
DocumentRoot /var/www/shamanicattraction

Now, I'm trying to configure the main domain the same way other domains are configured, so that the server root points to /var/www. This would allow me to access all hosted websites when using the server IP address.

So I edit default config to set
DocumentRoot /var/www
and I create a new config file with the same format as the other domains, enable it and reload apache config.

When I do that, however, [www.shamanicattraction.com](www.shamanicattraction.com) points to /var/www instead of /var/www/shamanicattraction

What am I missing? It must be something obvious but I can't see it. It's working for any other domain.

---

### Post by vasile002 on 2011-10-15
what does "apache2 -S" say?

check if the virtual host for the [shamanicattraction.com]("http://www.shamanicattraction.com/") is loaded

---

### Post by MysteryX on 2011-10-16
What do you mean by "apache2 -S" ?

/etc/init.d/apache2 -S
 * Usage: /etc/init.d/apache2 {start|stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean|status}

/etc/init.d/apache2 status
Apache is running (pid 15889).

cd /etc/apache2/sites-available
a2ensite shamanicattraction
Site shamanicattraction already enabled

---

### Post by MysteryX on 2011-10-19
Anyone has any other ideas?

---

