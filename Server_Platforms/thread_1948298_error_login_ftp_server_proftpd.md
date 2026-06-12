---
title: "error login ftp server proftpd"
date: 2012-03-28
forum: Server Platforms
---

### Post by nurulshofyah on 2012-03-28
I'm working on my final project to build ftp server using proFTPd in Ubuntu Server 11.10. I have configured ProFTPd and MySQL.
I can connected to FTP server, but I can't login to it. This error message appeared : 
[COLOR="Red"]421 Service not available, remote server has closed connection
Login failed 
No control connection for command: No such file or directory[/COLOR]

There is also an error message in /var/log/proftpd/proftpd.log: [COLOR="red"]mod_sql/4.3: unrecoverable backend error: (1045) Access denied for user 'proftpd'@'localhost' (usingpassword : YES)[/COLOR]

I checked /var/log/mysql.log, but there was nothing I found there. :confused:

If you have the way to solve this problem, please share it with me. Thank you ;)

---

