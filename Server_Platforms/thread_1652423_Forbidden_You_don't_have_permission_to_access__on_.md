---
title: "Forbidden You don't have permission to access / on this server."
date: 2010-12-24
forum: Server Platforms
---

### Post by EpicKris on 2010-12-24
This is what I'm attempting to achieve:
example1.com > site1
example2.com > site 2

I've created the sites as virtual hosts:
/etc/apache2/sites-available/example1
```
<VirtualHost *:80>
        ServerAdmin me@example1.com
        ServerName example1.com
        ServerAlias example1.com
        DocumentRoot /home/me/Sites/example1/www
        <Directory /home/kristian/Sites/example1/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>
```

The www folder has permissions 755, owner me and group me.
The index.html file has permissions 644, owner me and group me.

Visiting the sites shows:
http://example1.com/ & http://example1.com/index.html
```
Forbidden

You don't have permission to access / on this server.

Apache/2.2.14 (Ubuntu) Server at pluginstudios.co.uk Port 80
```

Without the virtual hosts the setup works fine.

Any suggestions please?

---

### Post by EpicKris on 2010-12-25
Could any help? I've read a lot about this topic, but not sure what to do exactly…

---

### Post by CharlesA on 2010-12-25
Are the user's home directories encrypted?

---

### Post by EpicKris on 2010-12-25
> **CharlesA said:**
> Are the user's home directories encrypted?

Yes! Thank you! How do I stop that?

---

### Post by CharlesA on 2010-12-25
You don't. You need to put the sites somewhere else. Normally they'd be in /var/www/somefolder

---

### Post by EpicKris on 2010-12-25
> **CharlesA said:**
> You don't. You need to put the sites somewhere else. Normally they'd be in /var/www/somefolder

It wont allow me to create any files or folders in the /var/www directory.

---

### Post by CharlesA on 2010-12-25
You need to have root permission to create files and folders there.

---

### Post by EpicKris on 2010-12-25
> **CharlesA said:**
> You need to have root permission to create files and folders there.

Okay, thank you for the help, I'm certain this will solve my problem completely.

---

### Post by Vegan on 2010-12-25
when you need root provileges, use the

sudo mkdir xxx

then your making a root owned folder

sudo chmod 777 xxx

---

### Post by EpicKris on 2010-12-25
Unfortunately I restarted my server and I need to type a password before services start but don't have access to the machine physically right now.

---

