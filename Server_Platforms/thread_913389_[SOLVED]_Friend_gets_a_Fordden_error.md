---
title: "[SOLVED] Friend gets a Fordden error"
date: 2008-09-07
forum: Server Platforms
---

### Post by lowstand on 2008-09-07
High i am having an issue not sure what i done wrong or what i am running apache2 on my Ubuntu   i have my website up runing smooth   a friend needed a file so i dropped it in a  folder i made in mysite  directory an called it downloads  an just dropped the taz file in   he  get this  error  i try an hit it from the gateway address as as well i get the same reply  how do i fix  please  in the easiest terms possible i know i installed a ftp as well but have no clue where to find it eather lmao 
but would love to get this error fixed so he may download from me or anyone else as well thanks 


Fobidden
You don't have permission to access /downloads/ on this server.

Apache/2.2.8 (Ubuntu) mod_ssl/2.2.8 OpenSSL/0.9.8g Server at lowstand.dyndns.org Port 80

---

### Post by mbeach on 2008-09-07
Thats some sweet grammar there.  Take the time to proofread - makes search results more reliable for others.

I would suspect you need to issue the following command to get around that forbidden message:
```
sudo chown -R www-data:www-data /var/www/downloads
```

---

