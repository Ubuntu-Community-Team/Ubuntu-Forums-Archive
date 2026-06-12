---
title: "Location of MySQL Error Log Files"
date: 2009-11-13
forum: Server Platforms
---

### Post by MockY on 2009-11-13
According to multiple books, the default location for the error logs in Linux is in the data directory. In the case of Ubuntu, this location is /var/lib/mysql and the file should be called <host>.err.

This is indeed not correct, since the only mysql error file I can find is mysql.err which happens to be located in /var/log
So both incorrect file name and location according to the books.

Furthermore, by default, error logging is enabled when you install MySQL, but the error log file in /var/log is empty, even if I executed a DROP USER noneexistinguser; which resulted in an error.

I added log-error=/var/lib/mysql under [mysqld] in my.cnf and restarted the MySQL server, but yet there are no .err files created in that directory whenever I execute something faulty in MySQL, nor is something showing up in the mysql.err file.

Could someone be so kind and enlighten me.
Thanks.

---

### Post by bradphelan on 2010-01-06
I see the same problem. So I thought I'd bump the message.

---

### Post by bradphelan on 2010-01-06
Actually under ubuntu it goes to /var/log/syslog

---

