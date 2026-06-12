---
title: "phpmyadmin file size limit"
date: 2015-02-10
forum: Server Platforms
---

### Post by Puzzettone on 2015-02-10
Hi, I've just purchased a VPS with Ubuntu 14.04.1 LTS and Plesk 12 Web Admin Edition.

I have to import to phpmyadmin a large wordpress database (30MB). Unfortunately the max file size allowed by phpmyadmi is 2,048MiB. It's not possible to change this value via the Plesk panel. How can I change this value via SSH?

I've already tried [this]("http://kb.sp.parallels.com/en/120683") but without any effect.

Thank you

---

### Post by volkswagner on 2015-02-10
The file you'll want to edit is /etc/php5/apache2/php.ini

I generally include upload and post size like:
```
upload_max_filesize = 50M
post_max_size = 55M

```

---

