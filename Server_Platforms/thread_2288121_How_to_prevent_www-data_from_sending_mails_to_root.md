---
title: "How to prevent www-data from sending mails to root@myhost"
date: 2015-07-24
forum: Server Platforms
---

### Post by ed_b2 on 2015-07-24
Hello,  in my /var/log/mail.log, I found that www-data and smmsp keeps sending mails to root@myhost.  Would anyone know how to stop this?  I saw [http://ubuntuforums.org/showthread.php?t=2005535](http://ubuntuforums.org/showthread.php?t=2005535) but the "solution" wouldn't work for me because I use ssmtp which doesn't use /etc/aliases.  Thank you very much in advance.

---

### Post by slickymaster on 2015-07-24
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by ed_b2 on 2015-07-24
It turned out that there was a key to a partial solution of my problem in the above thread.  In /var/spool/mail/www-data, there were copies of mails from www-data, which was just notices for the
failure of scripts from "rrdweather".  So I purged rrdweather.

However, according to the headers of /var/spool/mail/www-data I see :

From www-data@hostname
Return-Path: <www-data@hostname>
To: www-data@hostname

(Here "hostname" is what is in /etc/hostname).
How come do ssmtp send them to root@myhost (here "myhost" is the domain of my ISP,
defined in /etc/ssmtp/ssmtp.conf ) ?

---

