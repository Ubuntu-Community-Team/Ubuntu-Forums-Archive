---
title: "Apache is becoming crazy, help!!!!!!!"
date: 2010-05-20
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-05-20
hi, professionals, today, the power was suddenly cut off in my house, then my home Ubuntu Server restarted after the power on, but when I use my laptop to view my wesite, the index.html suddenly became blank page, I did clear the firefox cache, doesn't work, still blank, and I changed browser, to seamonkey, the index.html still was blank, so, I am sure that the problem is coused by the server, and then, I put the index.html file to a subdirectory, which under the /var/www/home/index.html, and then I put the address < [http://myserveripaddress/home/index.html](http://myserveripaddress/home/index.html) > ,then,I can view my website the main page index.html.

any professionals please help, I am sure that the apache server caused the problem , any simple way?

best thanks and regards,

:guitar::guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by dudumomo on 2010-05-20
Check first if apache is really running. If not, launch it:
sudo /etc/init.d/apache2 start

You can try to restart it as well if this one is already running
sudo /etc/init.d/apache2 start

---

### Post by cdenley on 2010-05-20
```

ls -l /var/www/index.html
head /var/www/index.html
echo -e "GET /index.html HTTP/1.0\n"|nc -q 1 127.0.0.1 80

```

---

