---
title: "mail logs"
date: 2009-04-15
forum: Server Platforms
---

### Post by tonkyman on 2009-04-15
I am running 8.04LT  as a LAMP server. I have a standard load of Ubuntu to which I've added Postfix, Courier, and Squirrel Mail. 

Anyway, I'm doing standard logging on my mail transactions but I would like to have a log that doesn't included user logins. I want my log to contain all the information that is normally included in /var/log/mail.log without the user login and logout messages. I have so many users that wading through all the login/logout messages clutters the screen and makes it hard to make sense of the file if you tailing it.

Is there a way to setup a log file that will capture only traffic and not the user login information???

Thanks for your help,
Tony

---

### Post by ostrm on 2009-04-15
You could write a script, that greps for the lines you are interested in. Could you post an example? Maybe an one-liner will do it.

The best solution, though, is to configure the syslogger to put the messages you are looking for into seperate files. 

Have a look at
```
man syslog.conf
```

---

### Post by tonkyman on 2009-04-15
These are the lines I want to filter out. they all say "pop3d" or "pop3d-ssl" in them but I want to keep all the other lines that say "postfix", "amavis" "postgrey", or anyting else.


Apr 15 06:54:50 bovo pop3d: Connection, ip=[::ffff:XXX.XXX.XXX.XXX]
Apr 15 06:54:50 bovo pop3d: LOGIN, user=april@mailserver.com, ip=[::ffff:XX.XXX.XXX.XXX], port=[1060]
Apr 15 06:54:51 bovo pop3d: LOGOUT, user=april@mailserver.com, ip=[::ffff:XXX.XXX.XXX.XXX], port=[1060], top=0, retr=0, rcvd=12, sent=39, time=1
Apr 15 06:54:52 bovo pop3d: Connection, ip=[::ffff:XXX.XXX.XXX.XXX]

Thanks,
Tony

---

### Post by ostrm on 2009-04-15
To filter these lines (and the ones with "pop3d-ssl") out, this should do the trick

```
egrep -v 'pop3d.* (LOGIN|LOGOUT|Connection)' [logfile]
```

cheers
  Tom

---

### Post by tonkyman on 2009-04-16
Thanks Tom, that worked well for what in needed to do right now. 

I'm going to explore the syslog.conf in the hope that I can get the system to generate a long that I can "tail" all day long.

If you come across a way to make it a log all it's own then I'm really interested.

Thank you so much for you help.

Tony

---

