---
title: "MySQL. syslog-ng, and php-syslog-ng help"
date: 2009-07-25
forum: Server Platforms
---

### Post by l3git.h4cker on 2009-07-25
So I am trying to set up a server that logs events from the pfsense firewall, and put the logs from syslog-ng to mysql, and organize/send them to an email.  
This logs traffic and events from remote computers on the same network.

Does anyone know of a good tutorial/site/instructions that would help me set up an email notification logger from syslog and mysql using php-syslog-ng?

---

### Post by wojox on 2009-07-25
[http://www.syslog.org/forum/syslog-and-syslogd/howto-for-using-php-syslog-ng-with-rsyslog/](http://www.syslog.org/forum/syslog-and-syslogd/howto-for-using-php-syslog-ng-with-rsyslog/)

---

### Post by eldar40k on 2009-07-27
Hi, for the general syslog-ng to mysql setup, check the official syslog-ng documentation available at: 
[http://www.balabit.com/support/documentation/](http://www.balabit.com/support/documentation/)

For e-mail alerts, see the syslog-ng mailing list archives, this topic has been discussed recently.
[http://marc.info/?l=syslog-ng&w=2](http://marc.info/?l=syslog-ng&w=2)

---

