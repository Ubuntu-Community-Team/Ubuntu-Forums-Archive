---
title: "Able to see files and folders of website"
date: 2011-01-16
forum: Server Platforms
---

### Post by osx on 2011-01-16
Have a question that seems I could have easily found the answer to by searching the 'net, but maybe I'm just not using the right search terms.

I'm playing around with Ubuntu Server 10.04.1 and wanted to experiment with setting up a website.

I have a dummy site running and noticed that by pointing my browser to the root of the site I was able to see the file and folder structure.

I'd like it to not do that and wanted to know the best way to disable it.

I don't have an index.html page in it (experimenting with PHP stuff right now). Is it best to just put in an index.html page or is it better to use some type of Apache directive or filesystem level permission setting?

Thanks.

---

### Post by mike.doherty on 2011-01-16
You should remove the Indexes directive from your Apache configuration. That's typically /etc/apache2/httpd.conf:
Change
```
  Options All Indexes FollowSymLinks MultiViews
```
to
```
  Options All FollowSymLinks MultiViews
```

---

### Post by osx on 2011-01-16
Thanks, mike.doherty.

---

