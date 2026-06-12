---
title: "can't get sub.localhost to work"
date: 2007-04-22
forum: Server Platforms
---

### Post by mephisto56 on 2007-04-22
I'm trying to work with a localhost subdomain but I don't get it to work on ubuntu. According to all I've read it should be pretty straightforward.

1. a file in sites-available, named it phorum.localhost

<VirtualHost *>
  ServerName phorum.localhost
  ServerAlias [www.phorum.localhost](www.phorum.localhost)
  DocumentRoot /var/www/apache2-default
</VirtualHost>

2. a2ensite phorum.localhost

3. restart apache using  sudo /etc/init.d/apache2 restart

Then when I open the browser and go to phorum.localhost I get a server not found error.

---

### Post by jtc on 2007-04-22
Looks like Apache is setup correctly, or at least in the right direction.

The problem is that your web browser has no idea what host phorum.localhost is and can therefore not connect to it. What you most likly want to do is to make an entry in your /etc/hosts

```
127.0.0.1          phorum.localhost
```

(Assuming you run your server at the same computer your trying to browse from.)

---

### Post by mephisto56 on 2007-04-22
That worked, thanks.

---

