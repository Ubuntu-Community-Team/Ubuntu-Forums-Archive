---
title: "Apache Indexes"
date: 2011-11-22
forum: Server Platforms
---

### Post by DanHorniblow on 2011-11-22
Hi, I have changed my 000-default file in sites-enabled to look like this:
```

        <Directory /var/www/>
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

The -Indexes part has disabled directory listing for all directories within /var/www/.

But i want one directory to be listed, is this possible?

---

### Post by Jonathan L on 2011-11-22
Hi Dan

> Hi, I have changed my 000-default file in sites-enabled to look like this:
```

        <Directory /var/www/>
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```The -Indexes part has disabled directory listing for all directories within /var/www/.

But i want one directory to be listed, is this possible?Add something like this:
```
<Directory /var/www/down/there/thisoneisokay/>
  Options +Indexes
</Directory>
```Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by DanHorniblow on 2011-11-22
> **Jonathan L said:**
> Hi Dan

Add something like this:
```
<Directory /var/www/down/there/thisoneisokay/>
  Options +Indexes
</Directory>
```Hope that's helpful.

Kind regards,
Jonathan.
Thanks that has worked. I thought I was going to have to start using .htaccess files or something, much easier solution :)

---

### Post by SeijiSensei on 2011-11-22
> **DanHorniblow said:**
> Thanks that has worked. I thought I was going to have to start using .htaccess files or something, much easier solution :)

That AllowOverride setting of "None" prohibits .htaccess files from changing the directory's settings.  This is the default in Ubuntu.

---

