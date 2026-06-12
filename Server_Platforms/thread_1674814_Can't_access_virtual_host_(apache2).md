---
title: "Can't access virtual host (apache2)"
date: 2011-01-24
forum: Server Platforms
---

### Post by Innuendo108 on 2011-01-24
I've just installed LAMP.

[http://localhost/](http://localhost/) page works fine.

I need to create some virtual hosts. Localhost page is situated in /var/www/. It's normal for me, and I wanted to created virtualhost (in /var/www/vhost1)

But it doesn't open in browser. Where is my mistake?

/etc/apache2/ports.conf
```

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

/etc/apache2/sites-available/vhost1
```

<VirtualHost *:80>

ServerAdmin admin@vhost1
ServerName vhost1
ServerAlias www.vhost1

DocumentRoot /var/www/vhost1

<Directory /var/www/vhost1/>
	Options -Indexes FollowSymLinks MultiViews
	AllowOverride All
	Order allow,deny
	allow from all
</Directory>

</VirtualHost>

```

Then I type in command line:
```

# a2ensite vhost1
# /etc/init.d/apache2 reload

```

Where is my mistake?

---

### Post by wongo888 on 2011-01-24
Add the appropriate entry in the Hosts file on your client machine? What error are you getting?

---

### Post by Innuendo108 on 2011-01-24
I haven't added anything to hosts files.

[UPDATE:]
I've just added 127.0.0.1 vhost1
to /etc/hosts
and nothing happened (nothing good I mean)
[/UPDATE]

What error - do you mean browser what tells me? "Not Found" - (browser tries to find this page on the net)

---

### Post by CharlesA on 2011-01-24
You need to have an entry in either the hosts file or in DNS pointing to that virtualhost's name. Else it will not find it locally and try to find it out on the internet.

---

### Post by Innuendo108 on 2011-01-24
But how to do it?

---

### Post by CharlesA on 2011-01-24
add something like this to the /etc/hosts file:

```
127.0.0.1 vhost1
127.0.0.1 vhost2
```

Then connect using [http://vhost1/](http://vhost1/)

---

### Post by Innuendo108 on 2011-01-24
Below I've posted that I had done this. But it didn't help

---

### Post by CharlesA on 2011-01-24
What error do you get?

---

