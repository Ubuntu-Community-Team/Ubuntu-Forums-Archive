---
title: "phpMyAdmin upload size is still 2048kb!"
date: 2016-06-24
forum: Server Platforms
---

### Post by Rusz_Tams on 2016-06-24
[SOLVED]
Hello! I did this:
```
sudo nano /etc/php/7.0/cli/php.ini
```

upload_max_filesize = 512M
post_max_size = 1024M
memory_limt = 2048

```
sudo service apache2 restart
```

Still 2048kb! Help me!

---

### Post by Habitual on 2016-06-24
terminal >
```
sudo find /etc -name php.ini -type f
```

---

### Post by Rusz_Tams on 2016-06-24
Thank you!
[SOLVED]

---

### Post by Habitual on 2016-06-26
You're welcome!

---

