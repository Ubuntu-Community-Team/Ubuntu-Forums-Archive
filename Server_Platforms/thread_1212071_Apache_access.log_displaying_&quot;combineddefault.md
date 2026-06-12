---
title: "Apache access.log displaying &quot;combineddefault&quot;"
date: 2009-07-13
forum: Server Platforms
---

### Post by R.Bucky on 2009-07-13
As the post title suggests, my apache logs are only displaying "combineddefault." Can anyone shed some light? I did the Google search, but did not find anything

---

### Post by yakkeh on 2010-06-21
same problem here.
anyone?

---

### Post by dapperdanny77 on 2010-06-21
I understood your lofiles contain just "combineddefault" - right?

check your apache config 
look for similar line

LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined

this is the definition of the log format
further in your config you should find then something like that

CustomLog /var/log/apache2/access.log combined

which is the definition of your logfile for a vhost with type combined. Maybe your config is garbled ...

---

