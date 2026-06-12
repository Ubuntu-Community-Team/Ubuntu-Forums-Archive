---
title: "SFTP Permission Help"
date: 2012-01-24
forum: Server Platforms
---

### Post by TFroehlich3 on 2012-01-24
Hey everyone!
  I have my SFTP server setup within my webserver. How do I change the permissions so I can write to the /var/www/ folder? I am using WebMin, if that would help me any. Can someone please help me! It will not let me SFTP files into that folder! It says I don't have the permission.

---

### Post by Lars Noodén on 2012-01-24
SFTP uses the same permissions as anything else in the filesystem.  

The example below shares the folder /var/www with the group "webmasters"

```

sudo addgroup webmasters

sudo gpasswd --add tfroehlich3  webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;


```

---

### Post by TFroehlich3 on 2012-01-24
> **Lars Noodén said:**
> SFTP uses the same permissions as anything else in the filesystem. 
 
The example below shares the folder /var/www with the group "webmasters"
 
```

sudo addgroup webmasters
 
sudo gpasswd --add tfroehlich3  webmasters
 
sudo chgrp -R webmasters /var/www
 
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
 
sudo find /var/www -type f -exec chmod g=rws  "{}" \;
 

```
 
Thank you I will try that when I get home from work!

---

### Post by TFroehlich3 on 2012-01-24
> **Lars Noodén said:**
> SFTP uses the same permissions as anything else in the filesystem.  

The example below shares the folder /var/www with the group "webmasters"

```

sudo addgroup webmasters

sudo gpasswd --add tfroehlich3  webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;


```


This worked perfectly! Thank you so much!

---

