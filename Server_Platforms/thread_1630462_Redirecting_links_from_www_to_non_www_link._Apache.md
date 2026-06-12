---
title: "Redirecting links from www to non www link. Apache (Ubuntu)"
date: 2010-11-25
forum: Server Platforms
---

### Post by Kneen on 2010-11-25
I installed Apache in Ubuntu 10.04.
Created a virtual host in sites-available named 'mysite':
```

<VirtualHost *:80>

    ServerName myrealdomain.com:80

    DocumentRoot /home/iuser/www/htdocs/mysite

    ServerAdmin webmaster@example.com

    ErrorLog /var/log/apache2/mysite-error_log

    CustomLog /var/log/apache2/mysite-access_log commo

</VirtualHost>

```

Then waited for nameservers to propagate it.
It works, but only for myrealdomain.com. I want to redirect [www.myrealdomain.com](www.myrealdomain.com) to myrealdomain.com.
How can I do that? Thanks.

---

### Post by SeijiSensei on 2010-11-25
Add a ServerAlias directive:

```

ServerName    myrealdomain.com
ServerAlias   www.myrealdomain.com

```

Of course, you'll need to have an A or CNAME record in DNS to point the www hostname to your server.  Also the name shouldn't include the :80; I'm a bit surprised that works at all.

ServerAlias can have multiple entries if needed.

---

### Post by Kneen on 2010-11-25
Yes, I had set an A record in DNS for www version too.

Thanks, ServerAlias did the trick. I didn't knew about ServerAlias, and was fiddling with htaccess to redirect it. Later I knew I had to get apache to somehow listen to www version first before I can redirect to non www version using htaccess (to avoid duplicate content).

Initially, I didn't add the port number, but while checking out PHP configuration in phpinfo(), I cam across a setting in apache2handler configs. It says:
```

Hostname:Port	myrealdomain.com:80

```
So I thought it was a necessity to exclusively specify the port.

---

