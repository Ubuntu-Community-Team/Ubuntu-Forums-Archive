---
title: "Syslog problem"
date: 2010-08-04
forum: Server Platforms
---

### Post by MasterGamerJK on 2010-08-04
Hello,  I an trying (without much luck) to setup a ubuntu client to forward all syslog messages to a chosen server and then have the the server dump all of those logs directly into the local4 group. Can anyone shine some light on how to direct the logs to local4 instead of being added to all local relivent facilities?

---

### Post by ruffEdgz on 2010-08-04
Have you looked into the 'logger' command to do something like this:
```

logger -p local4.<something> MESSAGE HERE

```
Depending on how you are moving from the client to the server (I used syslog-ng for my server to grab information from the clients), I could see using the 'logger' command but I would separate the logs of the clients from the server logs so you can help debug problems depending on the client.

Just my 2 cents ;)

---

### Post by MasterGamerJK on 2010-08-04
I very much like 2 cents : ) 


ATM im just trying to throw all logs to the server from /etc/syslog.conf on the client side
"
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log
*.*                             @NAME_OF_LOG_SERVER
"
 and then i need to figure out how to tell the server to take all incoming logs from "FQDN_OF_CLIENT" and drop them in local4 so that splunk of webmin can organize them

Ive been using the logger command, its been very helpful. Thank you
Keep the replays comming...

---

### Post by ruffEdgz on 2010-08-04
If you need help with the "NAME_OF_LOG_SERVER" setup, I would look into the application called 'syslog-ng'
```

aptitude show syslog-ng

```
I feel its pretty simple to use and can help you take those client side logs and organize them onto the syslog server. I have mine setup to catch all the syslogs from clients and place them into this format
```

/srv/logs/HOSTS/$HOST/$YEAR/$MONTH/$DAY/$FACILITY.log

```
The variables you see are a part of the syslog-ng service.

[Here is a link that will help you understand it better if you are interested.]("http://sial.org/howto/logging/syslog-ng/")

---

