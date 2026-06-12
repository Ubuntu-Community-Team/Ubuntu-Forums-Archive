---
title: "Apache 2"
date: 2009-01-22
forum: Server Platforms
---

### Post by ajwak95 on 2009-01-22
Well, I messed up. In anger, I deleted all Apache files from /etc, thus, messing it up. Then upon reinstall, I get a message; 
ERROR: APACHE_PID_FILE needs to be defined in /etc/apache2/envvars
;

Any suggestions?

---

### Post by geforce123 on 2009-01-24
```
sudo apt-get remove --purge $(dpkg -l apache* | grep ii | awk '{print $2}') && sudo apt-get install apache2
```


[http://ubuntuforums.org/showthread.php?t=813725](http://ubuntuforums.org/showthread.php?t=813725)



Phil

---

