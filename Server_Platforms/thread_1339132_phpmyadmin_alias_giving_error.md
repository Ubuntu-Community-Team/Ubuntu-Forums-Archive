---
title: "phpmyadmin alias giving error"
date: 2009-11-27
forum: Server Platforms
---

### Post by tapas_mishra on 2009-11-27
I am getting the following error when I am restarting apache2
```

root@tapas-laptop:/var/www# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                                        [Fri Nov 27 17:15:21 2009] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 4 will probably never match because it overlaps an earlier Alias.
 ... waiting [Fri Nov 27 17:15:22 2009] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 4 will probably never match because it overlaps an earlier Alias.

```

while the log shows 
```

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```
and if I comment the line 4 as above said 
which in my /etc/phpmyadmin/apache.conf
is Alias /phpmyadmin /usr/share/phpmyadmin
then [http://localhost/phpmyadmin](http://localhost/phpmyadmin) link breaks and does not work what can be done for this why is this warning coming.Which file should I check

---

### Post by ubhi on 2009-11-27
open in apache config file & add following line

servername myserver

instead of 'myserver' enter your servername

---

