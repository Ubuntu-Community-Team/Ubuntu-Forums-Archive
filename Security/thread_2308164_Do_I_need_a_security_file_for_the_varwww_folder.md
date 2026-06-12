---
title: "Do I need a security file for the /var/www folder?"
date: 2015-12-31
forum: Security
---

### Post by Heeter on 2015-12-31
Hi All,

I am currently hosting a few domains off my LAMP Ubuntu 14.04, all is working fine.

The webfolders are located in /var/www/ subfolders. 

But I do not actually have anything in the root /var/www folder itself. Should I have something ( a redirecting file or .htaccess file) in the /var/www folder?

Currently, my apache config file looks like this:

```

<Directory />
        Options FollowSymLinks
        AllowOverride None
        Require all denied
</Directory>

<Directory /usr/share>
        AllowOverride None
        Require all granted
</Directory>

<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>

```

Regards

---

### Post by Habitual on 2016-01-01
Modern releases of apache2 disable the .htaccess file from being read.
It is also suggested that restrictions like these be placed in the .conf file.
This speeds up processing as it does not have to 'hit' the .htaccess file for every file read.

---

### Post by Heeter on 2016-01-01
Thanks for your response,

What would be an appropriate entry into my apache config file that would address this?

Also another thing I noticed is that when I type in the actual IP address of the webserver into a web browser, it lands in nowhere land. I addressed this issue by editing the htaccess file in one of the domain webfolders to do a redirect. Should this be addressed in the apache config file instead?

Regards, and thank you

---

### Post by Habitual on 2016-01-02
```
</VirtualHost>
<Directory "/var/www/html">
Restrictions_here
</Directory>
```

See also [https://httpd.apache.org/docs/2.2/sections.html](https://httpd.apache.org/docs/2.2/sections.html)

---

