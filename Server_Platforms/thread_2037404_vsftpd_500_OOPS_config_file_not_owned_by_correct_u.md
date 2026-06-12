---
title: "vsftpd: 500 OOPS: config file not owned by correct user, or not a file"
date: 2012-08-04
forum: Server Platforms
---

### Post by Birdbrain2 on 2012-08-04
When using  the ```
vsftpd
``` command to check my config, I got  ```
500 OOPS: config file not owned by correct user, or not a  file
``` I tried on a brand new Ubuntu installation and a brand new vsftpd installation and got the same error. ls -l gives me ```
-rw-r--r-- 1 root root 5528 /etc/vsftpd.conf
```

---

### Post by gordintoronto on 2012-08-04
sudo chown -cR (username) /etc/vsftpd.conf

---

### Post by Birdbrain2 on 2012-08-05
Now I get: ```
500 OOPS: vsftpd: must be started as root (use run_as_launching_user option
```
Changing that option causes vsftpd to fail to properly bind to its port.

---

