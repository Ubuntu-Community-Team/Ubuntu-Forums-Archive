---
title: "Phpmyadmin + fail2ban"
date: 2015-05-13
forum: Server Platforms
---

### Post by rhandy2 on 2015-05-13
I would like to block failed attemp logins in phpmyadmin with failed2ban

phpmyadmin is running on [http://mydomain.tld/phpmyadmin](http://mydomain.tld/phpmyadmin)

Using cookie method to login.

But I can´t see any log of failed login in /var/log/apache2/domain.log

How i can do it????

---

### Post by Habitual on 2015-05-14
Have a look at [http://serverfault.com/questions/434651/setting-up-fail2ban-to-ban-failed-phpmyadmin-login-attempts](http://serverfault.com/questions/434651/setting-up-fail2ban-to-ban-failed-phpmyadmin-login-attempts)

---

### Post by rhandy2 on 2015-05-16
I see [http://serverfault.com/questions/434...login-attempts]("http://serverfault.com/questions/434651/setting-up-fail2ban-to-ban-failed-phpmyadmin-login-attempts")

But What I put in fail2ban.php

is just

> <?php
[FONT=Consolas]$_REQUEST['pma_{username|password'];
[/FONT]?>

---

### Post by Habitual on 2015-05-18
Tip: If you secure your phpmyadmin directory with either an .conf exclusion or using an .htaccess or .htpasswd file, then
having fail2ban watch this for phpmyadmin intrusions becomes unnecessary.

See also [http://stackoverflow.com/questions/4400154/htaccess-deny-all-allow-only-one-ip](http://stackoverflow.com/questions/4400154/htaccess-deny-all-allow-only-one-ip) and
[http://stackoverflow.com/questions/2631269/how-to-secure-phpmyadmin](http://stackoverflow.com/questions/2631269/how-to-secure-phpmyadmin)
But a 
deny from all
allow from <trusted_ip0>
allow from <trusted_ip1>

---

