---
title: "Postfix squirrelmail issue"
date: 2012-08-30
forum: Server Platforms
---

### Post by Mikog on 2012-08-30
Hi everybody,

I am working on a issue that i cannot seem to resolve on my own.

When login in to squirrelmail and when i try to send an mail i get an error notification.
When i look into the syslog of the postfix server i see this:


postfix/smtpd[4360]: warning: numeric hostname: 192.168.1.220
postfix/smtpd[4360]: connect from unknown[192.168.1.220]
postfix/smtpd[4360]: lost connection after UNKNOWN from unknown[192.168.1.220]
postfix/smtpd[4360]: disconnect from unknown[192.168.1.220]


My squirrelmail(192.168.1.220) is on a different server from where postfix is installed on.

What i also did is installing squirrelmail on the same server as the postfix server and then every thing works perfectly. When squirrelmail and postfix/dovecot are on the same server i have no issues at all.

From the remote squirrelmail server i am able to open an telnet session on port 25 to the postfix server.

The squirrelmail and the postfix server are both in the same subnet.

Please advise.

---

### Post by Bachstelze on 2012-08-30
> **Mikog said:**
> 
My squirrelmail(192.168.1.220) is on a different server from where postfix is installed on.

This is asking for trouble, why not install postfix on that server and be done with it?

---

### Post by SeijiSensei on 2012-08-30
Isn't it possible to solve this problem simply by adding an entry to the server's /etc/hosts with the hostname of the machine at 192.168.1.220?

---

