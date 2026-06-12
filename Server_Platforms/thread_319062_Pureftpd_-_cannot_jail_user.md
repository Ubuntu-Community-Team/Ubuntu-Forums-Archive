---
title: "Pureftpd - cannot jail user"
date: 2006-12-15
forum: Server Platforms
---

### Post by DoorGunner on 2006-12-15
Hi  I installed Pureftpd on my system using the instructions on this site. [http://www.ubuntuforums.org/showthread.php?t=213266&highlight=pure-ftpd](http://www.ubuntuforums.org/showthread.php?t=213266&highlight=pure-ftpd)

when I do a $sudo pure-pw show john

Login              : john
Password           : xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
UID                : 1009 (ftpuser)
GID                : 1009 (ftpgroup)
Directory          : /home/ftpusers/john/./
Full name          : 
Download bandwidth : 0 Kb (unlimited)
Upload   bandwidth : 0 Kb (unlimited)
Max files          : 0 (unlimited)
Max size           : 0 Mb (unlimited)
Ratio              : 0:0 (unlimited:unlimited)
Allowed local  IPs : 
Denied  local  IPs : 
Allowed client IPs : 
Denied  client IPs : 
Time restrictions  : 0000-0000 (unlimited)
Max sim sessions   : 0 (unlimited)

My problem is that even though the Directory line shows /home/ftpusers/john .... When I access Pureftp from a remote computer I can access every file in my root directory. How can I jail my ftp user "john" to just the Directory /home/ftpusers/john ???

---

### Post by chrisfay on 2006-12-15
Not sure about pureftpd, but on proftpd all you have to do is add the directive:

```
DefaultRoot ~
```

....into the /etc/proftpd.conf file.

This will lock all users to their home directory. Unless you have emotional ties to pureftpd, I recommend switching to proftpd for simplicity. Apt-get it and you're good to go. 

A second recomendation would be to switch away from ftp altogether. Use scp or sftp to benefit from the security of ssh so your login credentials aren't sent in the clear.....

---

### Post by DoorGunner on 2006-12-15
Took you suggestion and did that..... it was a lot simpler and the script worked great....

thank you

---

### Post by chrisfay on 2006-12-15
excellent!:D

---

