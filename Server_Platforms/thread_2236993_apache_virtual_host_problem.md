---
title: "apache virtual host problem"
date: 2014-07-30
forum: Server Platforms
---

### Post by Axel_Jacobs on 2014-07-30
Hi, 


I am fairly new to this, so I probably missed something obvious.


I have a ubuntu 12.4 apache2 setup. I have two sites running, they are working fine. But when I try to set up a third one, the second site gets redirected to the third. If I set up a fourth it gets redirected to the last. My vhost config are all like:

```

<VirtualHost *:80>
ServerAdmin webmaster@localhost


DocumentRoot /var/www/generationalbator/public_html
ServerName [www.generationalbator.be](www.generationalbator.be)
Serveralias generationalbator.be
Serveralias [www.generationalbator.be](www.generationalbator.be)


ErrorLog /var/www/generationalbator/logs/error.log
Loglevel warn
CustomLog /var/www/generationalbator/logs/access.log combined


<Directory /var/www/generationalbator/public_html>
	AllowOverride All
	Order allow,deny
	allow from all
</Directory>


</VirtualHost>

```

Any ideas?

---

### Post by thnewguy on 2014-07-30
It is hard to say for sure without seeing all the configuration files, but chances are there is an overlap or typo in the SeverName or ServerAlias directives. Or you need to reload/restart the Apache service.

Also, you just need one ServerAlias command. For example:
```

ServerName example.org
Serveralias www.example.org

```
Then make sure your DocumentRoot and Directory directives both point to the proper directory on your server.

---

### Post by TheFu on 2014-07-31
Like theNewGuy says, each virtualhost needs their own **ServerName** setting. I think that is what is missing.
There are many ways to setup virtualhosts - I use the 1 config-file-per-vhost method, but I don't think apache cares if you put them all inside 1 config file - provided they are inside different VirtualHost stanzas.

Please mark this thread solved, if it is. Otherwise, provide logfile data so we can help.

---

