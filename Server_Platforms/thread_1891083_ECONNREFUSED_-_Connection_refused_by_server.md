---
title: "ECONNREFUSED - Connection refused by server"
date: 2011-12-04
forum: Server Platforms
---

### Post by nrodes on 2011-12-04
I have recently setup a vsftpd server to serve web directories in /var/www/$USER. I've setup a few virtual users using PAM and db-util. 

The server worked until I changed vsftpd.conf as per the instructions at [http://blog.up-link.ro/how-to-set-up-vsftpd-virtual-users-berkeley-db-pam/]("http://blog.up-link.ro/how-to-set-up-vsftpd-virtual-users-berkeley-db-pam/")

Now I get the ECONNREFUSED error. It seems that this error originates in the vsftpd.conf file and not some anomaly in the user/pass database. If it was the latter, then I would get a "LOGIN INCORRECT" -esque error instead. Attached is a copy of my vsftpd.conf.

---

### Post by nrodes on 2011-12-05
Problem solved, thanks to
[http://fixunix.com/debian/129361-pam-userdb-auth-issue-pam_userdb-cant-open-database-vsftpd-sarge.html](http://fixunix.com/debian/129361-pam-userdb-auth-issue-pam_userdb-cant-open-database-vsftpd-sarge.html).

---

