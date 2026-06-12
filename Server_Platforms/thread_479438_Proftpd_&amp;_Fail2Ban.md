---
title: "Proftpd &amp; Fail2Ban"
date: 2007-06-20
forum: Server Platforms
---

### Post by Aberrix on 2007-06-20
Does anyone have any insight on how to get fail2ban to read the proftpd logs as well and ban attacks on proftpd?

Thanks in advance.

---

### Post by dannyboy79 on 2007-06-20
> **Aberrix said:**
> Does anyone have any insight on how to get fail2ban to read the proftpd logs as well and ban attacks on proftpd?

Thanks in advance.

here's a thread that states that there is  a problem with the current fail2ban and then the solution is on the last page. this deals with a different FTP server program but should be the same.

[http://ubuntuforums.org/showthread.php?t=438260&highlight=fail2ban](http://ubuntuforums.org/showthread.php?t=438260&highlight=fail2ban)

---

### Post by Aberrix on 2007-06-20
well... since I am running 6.06LTS it appears I am at fail2ban v0.6.0-3...

looks like I need to figure out a way to upgrade that...

---

### Post by dannyboy79 on 2007-06-20
you could compile from source, right?

---

### Post by Aberrix on 2007-06-20
> **dannyboy79 said:**
> you could compile from source, right?

looks like it depends on a new version of python which 6.06 doesnt have...

---

### Post by freebeer on 2007-08-23
I took me a while to track it down, but it would appear that you need to replace failregex line with:

```

failregex = USER \S+: no such user found from \S* ?\[<HOST>\] to \S+\s*$

```

I just did this myself, so I can't confirm that it works until I get home and scour the logs.

Oh.. and it case you didn't notice, proftpd buts its log files in /etc/log/secure so you'll need to make that change, too.

---

### Post by Aberrix on 2007-09-06
doesn't quite look like that worked for me, here is what I have in my /etc/fail2ban.conf

```
[FTP]
# Option:  enabled
# Notes.:  enable monitoring for this section.
# Values:  [true | false]  Default:  true
#
enabled = true

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = 21

# Option:  logfile
# Notes.:  logfile to monitor.
# Values:  FILE  Default:  /var/log/auth.log
#
logfile = /var/log/prodtpd/proftpd.log

# Option:  timeregex
# Notes.:  regex to match timestamp in Apache logfile.
# Values:  [Wed Jan 05 15:08:01 2005]
# Default: \S{3} \S{3} \d{2} \d{2}:\d{2}:\d{2} \d{4}
#
#timeregex = \S{3} \S{3} \d{2} \d{2}:\d{2}:\d{2} \d{4}

# Option:  timepattern
# Notes.:  format used in "timeregex" fields definition. Note that '%' must be
#          escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule)
# Values:  TEXT  Default:  %%a %%b %%d %%H:%%M:%%S %%Y
#
timepattern = %%b %%d %%H:%%M:%%S

# Option:  failregex
# Notes.:  regex to match the password failure messages in the logfile.
# Values:  TEXT  Default:
#
failregex = USER \S+: no such user found from \S* ?\[<HOST>\] to \S+\s*$
```

but I get this error when fail2ban is running;
```
2007-09-06 09:04:05,703 ERROR: Unable to get stat on /var/log/prodtpd/proftpd.log
2007-09-06 09:04:05,762 ERROR: Unable to get stat on /var/log/prodtpd/proftpd.log
2007-09-06 09:04:06,770 ERROR: Unable to get stat on /var/log/prodtpd/proftpd.log
2007-09-06 09:04:07,770 ERROR: Unable to get stat on /var/log/prodtpd/proftpd.log
2007-09-06 09:04:08,770 ERROR: Unable to get stat on /var/log/prodtpd/proftpd.log
```

and lastly, here is what I am seeing in my proftpd logs;
```
Sep 01 10:25:13 castle.nullbox.net proftpd[16475] castle.nullbox.net (ns2.caton.es[::ffff:212.163.4.132]): FTP session opened.
Sep 01 10:25:13 castle.nullbox.net proftpd[16475] castle.nullbox.net (ns2.caton.es[::ffff:212.163.4.132]): no such user 'password'
Sep 01 10:25:13 castle.nullbox.net proftpd[16475] castle.nullbox.net (ns2.caton.es[::ffff:212.163.4.132]): USER password: no such user found from ns2.caton.es [::ffff:212.163.4.132] to ::ffff:192.168.0.250:21
Sep 01 10:25:13 castle.nullbox.net proftpd[16475] castle.nullbox.net (ns2.caton.es[::ffff:212.163.4.132]): mod_delay/0.5: delaying for 209 usecs
Sep 01 10:25:14 castle.nullbox.net proftpd[16475] castle.nullbox.net (ns2.caton.es[::ffff:212.163.4.132]): no such user 'password'
Sep 01 10:25:14 castle.nullbox.net proftpd[16475] castle.nullbox.net (ns2.caton.es[::ffff:212.163.4.132]): USER password: no such user found from ns2.caton.es [::ffff:212.163.4.132] to ::ffff:192.168.0.250:21
```

---

### Post by flyboy320 on 2007-11-28
> **Aberrix said:**
> well... since I am running 6.06LTS it appears I am at fail2ban v0.6.0-3...

looks like I need to figure out a way to upgrade that...
Were you able to get a version other than 0.6.0-3 working on 6.06?   I have the same issue and have not found a clean How-To for a version other than 0.6.0-3.

Thanks.

Alan

---

