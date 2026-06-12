---
title: "dovecot stops working"
date: 2008-11-03
forum: Server Platforms
---

### Post by bathmatt on 2008-11-03
I am using dovecot for pop/imap services in 8.10, as i did under 8.04.  However, ever since being installed about every hour it stops responding and i need to restart the server (/etc/init.d/dovecot restart).  There is little in the logs. in mail.err i start getting

Nov  3 07:13:23 mail dovecot: auth-worker(default): pam(matt,127.0.0.1): pam_authenticate() failed: Authentication failure


in mail.log i get


Nov  3 07:05:18 mail dovecot: auth-worker(default): pam(matt,127.0.0.1): pam_start() failed: Critical error - immediate abort



Now if i restart it everything is great for a while, then this happens again.  I have a clean conf file except for 
protocols = pop3 imap imaps

ideas?
Thanks
matt

---

### Post by chadoe on 2008-11-06
[http://ubuntuforums.org/showthread.php?p=6007534#post6007534]("http://ubuntuforums.org/showthread.php?p=6007534#post6007534")

---

### Post by bathmatt on 2008-11-06
Found that before posting, didn't work...  Same thing, set it to the default value of 30.  Right now, crontab to restart..

---

