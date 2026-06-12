---
title: "PHPMyAdmin"
date: 2007-05-31
forum: Server Platforms
---

### Post by ecochran on 2007-05-31
I have been trying to find best practices on securing PHPMyAdmin but haven't found anything that has been very helpful.  Everything points to htaccess files and the PHPMyAdmin authentication.  What I am looking for is a way to secure it from external access.  Can I place it on a different port other than the standard 80 so that I can block access through my firewall?  How would I do this?

Thanks,
Ethan

---

### Post by ruy_lopez on 2007-05-31
I take it you have a webserver listening on port 80, and just want to make sure no one can access phpmyadmin. So blocking ingress traffic on port 80 isn't an option.

You can edit the phpmyadmin file in /etc/apache2/sites-available/
```

<Directory "/path/to/phpmyadmin/root">
    ...
    Order deny, allow
    Deny from all
    Allow from 192.168.1.0/255.255.255.0
</Directory>
```

Replace 192.168.1.0/255.255.255.0 with your private network, and restart apache2.

---

