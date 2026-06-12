---
title: "Apache2 Named Virtual Hosts Not working"
date: 2015-01-21
forum: Server Platforms
---

### Post by robp2175 on 2015-01-21
I have setup named virtual host dozens of times and never had this problem. On two brand new 12.04 boxes it is simply not working. I have gone to as simple a setup as possible and for some reason I am always sent to the default directory, not the one in my named host when I try to access it with the named fqdn. I have to believe there is a bug I am not aware of. Any assistance would be greatly appreciated. 
Here is my config file. Lke I said, very simple. And of course NameVirtualHost *:80 is in my config. 

```
<VirtualHost *:80>
ServerName guac.domain.com
DocumentRoot /var/www/guac
</VirtualHost>
```

---

### Post by newbie-user on 2015-01-21
Did you:
1. enable the site?  *a2ensite guac*
2. restart apache?  *service apache2 restart*
3. check permissions on /var/www/guac?  *chmod -R 644 /var/www/guac*
4. check the apache log files?

---

### Post by robp2175 on 2015-01-21
Thanks but that has all been done.

---

### Post by newbie-user on 2015-01-22
Have you made changes in other configuration files? Usually, if I want virtual hosts, all I do is create a new conf file in /etc/apache2/sites-available, enable it, restart apache, then point DNS to the server. Really simple, and probably what you did. Is this line uncommented in /etc/apache2/apache2.conf?```
# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf
```

---

### Post by SeijiSensei on 2015-01-22
All the configuration files must end with the .conf extension, or they will be ignored.  This behavior differs from Apache 2.2 on earlier Ubuntu versions.

---

