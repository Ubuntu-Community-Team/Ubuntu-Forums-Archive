---
title: "Custom 404 page"
date: 2008-06-28
forum: Server Platforms
---

### Post by mam00th on 2008-06-28
Hi, I'm using Ubuntu server edition 8.04 with the LAMP stack and I'm having a hard time creating a custom 404 page for my website.

I've created the .htaccess in my /var/www folder which contain the following :

```
ErrorDocument 404 /notfound.html
```

I still however can't manage to get my custom 404 page when typing an incorrect URL. FYI, yes my page is larger then 512 bytes.

Help me please. Thanks!

---

### Post by slakkie on 2008-06-28
Check your allowoverride directive: [http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride](http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride)

You must have FileInfo enabled, otherwise you cannot overwrite the directive in your .htaccess file

---

### Post by mam00th on 2008-06-28
And how would you do that, from what I see my httpd.conf file is pretty much empty so shouldn't AllowOverride be set to All by default?

---

### Post by slakkie on 2008-06-28
> **mam00th said:**
> And how would you do that, from what I see my httpd.conf file is pretty much empty so shouldn't AllowOverride be set to All by default?

No, apply the [Principle of least privilege.](http://en.wikipedia.org/wiki/Principle_of_least_privilege)

If you want to change it, lookup the something simlar to this in the files which are located in /etc/apache2/sites-enabled, most probably this will be located in 000-default. Pick your favorite editor and open the file as root.

sudo vi /etc/apache2/000-default

```

DocumentRoot /var/www
<Directory /var/www/>
    Options Indexes FollowSymLinks MultiViews
#    AllowOverride None
    AllowOverride FileInfo
    # snip
</Directory>

```

Save your changes and quit the file.
Run /usr/sbin/apache2ctl configtest, and resolve any issue reported (not needed in this case ;)).
Once the configtest passes reload the apache config via /etc/init.d/apache2.

---

### Post by windependence on 2008-06-28
> **mam00th said:**
> And how would you do that, from what I see my httpd.conf file is pretty much empty so shouldn't AllowOverride be set to All by default?

Just a note, AFAIK Apache2 doesn't use the httpd.conf file. The default config file is at /etc/apache2/apache2.conf.

Here is some good info on configuration even though it's written for 6.10:

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html)

-Tim

---

