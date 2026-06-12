---
title: "syslogng installation for centralized logging"
date: 2010-01-29
forum: Server Platforms
---

### Post by mansonthomas on 2010-01-29
Hi,

  I need to centralize the logging of several machine on one machine with syslog-ng.

  I'm currently using fail2ban for security enhancement and logwatch for log reports, which are based on file log on each machine.

  So one question is : is it possible to keep local logging for fail2ban and logwatch (logwatch can be dropped, but not fail2ban).

  One other need is to move old logs to a ftp site for archiving, as in france we have to keep one year of logs.

  Another thing I've seen, is that logging goes to a MySQL database instead of the filesystem which allow to have some nice feature as web frontend, search capabilities...
  I think it would be great but, how is it compatible with the ftp save?

Does anybody have an experience on this? some advice?

Regards,
Thomas.

---

### Post by mansonthomas on 2010-02-01
up

---

### Post by mansonthomas on 2010-02-03
up

---

### Post by mansonthomas on 2010-02-07
No one uses syslog-ng ?

---

### Post by stlsaint on 2010-02-08
im sure fail2ban logs can still be done locally and that you can simply copy and move logs to an offsite location. Im not sure about syslogng as i dont use it nor do i use mysql for storing logs.

---

### Post by mansonthomas on 2010-02-09
Well I'll try on syslog-ng mailing list instead, I'll get more answer I guess ;)

---

### Post by jure1873 on 2010-02-10
I've got all my servers setup so they log locally and then also send all the messages to a centralized syslog server that stores them in files and in a mysql database. There is also phpsyslog-ng on that server for easy searching.

---

### Post by mansonthomas on 2010-02-10
Hi,

 Do you have some sample configuration file to show or maybe some tutorial you use to setup your installation ? 

Thanks,
Thomas.

---

