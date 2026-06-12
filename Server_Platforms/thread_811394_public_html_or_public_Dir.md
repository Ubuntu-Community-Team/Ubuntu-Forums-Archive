---
title: "public_html or public Dir"
date: 2008-05-29
forum: Server Platforms
---

### Post by morgandeath on 2008-05-29
Hi,

I am trying to get [http://localhost/morgan](http://localhost/morgan) to work.
in my home dir there is a dir named public so, I put an index.html files in there but, I cant access in the browser locally or  though my isp.


I tried mkdir public_html  and still does not work.


What can I do to set it up so each home user can have there own web page?


Thanks.


Morgan

---

### Post by K.Mandla on 2008-05-29
Moved to Server Platforms.

---

### Post by cdenley on 2008-05-29
[http://httpd.apache.org/docs/2.2/mod/mod_userdir.html](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html)

[http://localhost/~morgan](http://localhost/~morgan)

Of course, you need to have userdir enabled
```

sudo a2enmod userdir
sudo /etc/init.d/apache2 force-reload

```
and your public_html files must be readable by www-data
```

chmod -R a+r ~/public_html
chmod a+x ~/public_html

```

---

