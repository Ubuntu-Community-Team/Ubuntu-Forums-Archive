---
title: "Apache executes files without extensions"
date: 2009-06-26
forum: Server Platforms
---

### Post by shaker108 on 2009-06-26
I just noticed that apache executes files even if you don't write the extension in the url. It happens on 8.04 and 09.04

[http://localhost/info](http://localhost/info) will execute [http://localhost/info.php](http://localhost/info.php)

I have not seen this happen on any other apache installs I have. Anyone know how to disable this?

---

### Post by wesamly on 2010-08-10
Hi, today I was working on a page that supposed to be directed through htaccess, and no matter I changed the rules, the output will be the same, until I decided to rename .htaccess, the surprise was that the page still outputs the same html.
Then I googled the problem, and found your post, it is old, but I thought the answer might help someone out there.

Actually, it is an Apache option called MultiViews, it makes apache execute a request like: example.com/category/ from example.com/category.php, that is if the file exist only.

To disable it, remove the option from apache cnfig file: /etc/apache2/sites-available/default
remove it from :

```
<Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
```

---

