---
title: "Virtualhost Custom PHP.INI"
date: 2011-02-16
forum: Server Platforms
---

### Post by craigp on 2011-02-16
so from what i understand a custom php.ini for each virtualhost is difficult to implement or impossible. So i'm just trying to add it in my virtualhost declaration. 

in main php.ini phpinfo is denied. I want to allow it for one website (as well as a number of other functions)

i have added:

```
NameVirtualHost *:80
<VirtualHost *:80>
ServerName test.com
DocumentRoot /home/www/public_html/test.com

**php_value enable_functions phpinfo**
```

but it does nothing. apache restarts fine but it has no effect when i run phpinfo().

any ideas?

---

### Post by rudelgurke on 2011-02-16
Did you read [http://www.php.net/manual/en/ini.core.php#ini.disable-functions](http://www.php.net/manual/en/ini.core.php#ini.disable-functions) ?

Still if you want to use PHP with Vhosts, do it with Suexec and FastCGI to have a separation of your Vhosts. Also makes setting up permissions much easier.

---

### Post by craigp on 2011-02-17
okay so i cant use that in that configuration. Annoying that i found that in someone elses examples. 

Suexec and FastCGI sounds like the way i want to go but with 100 sites it would be a bit of work i think to enable that for all with minimal downtime to the users, since i haven't set it up like that before. 

is it possible to enable phpinfo in a .htaccess file or any other way since i just need that as well as some other functions like system() for just one site?

---

### Post by rudelgurke on 2011-02-18
Yes. See about Suhosin's function blacklist / whitelist functions. These can be set on runtime.

Still, highly recommend the FastCGI method, specially when running several Vhosts to prevent one Vhost's PHP scripts eating all resources.

---

