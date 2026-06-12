---
title: "Logrotate not running script"
date: 2009-01-14
forum: Server Platforms
---

### Post by ksudbury on 2009-01-14
I'm a little stuck here, my logrotate file looks sane, I can run the script by hand fine.. but if I run the logrotate by hand it does not work, it will rotate the files but it will not run the script after... here is my logrotate file:

/var/backup/mysql/*.sql {
  daily
  copy
  missingok
  rotate 30
  compress
  notifempty
  create 640 root adm
  sharedscripts
  prerotate
  /usr/local/sbin/backup_mysql.sh
  endscript
}

Any ideas why this would happen, or how I can debug why it wont run the script? 

Many Thanks

---

### Post by RealPSL on 2009-01-16
Have you tried running ```
sudo logrotate -d
``` so you can see what might be happening?

---

### Post by ksudbury on 2009-01-16
In fact there was actually nothing wrong! it just needed a file there to start with then it rotated it and created a new file after just fine!

---

