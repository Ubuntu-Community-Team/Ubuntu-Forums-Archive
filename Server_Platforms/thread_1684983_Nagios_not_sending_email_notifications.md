---
title: "Nagios not sending email notifications"
date: 2011-02-09
forum: Server Platforms
---

### Post by Chrus on 2011-02-09
Hey

Trying to get email notifications working for Nagios and I've hit a bit of a wall. I can send mail from the command line, so i know thats not a problem.

I've set my notify-service-by-email command to:
```
/usr/bin/printf "%b" "to:$CONTACTEMAIL$\n" "from:user@domain.com\n" "subject:** $NOTIFICATIONTYPE$ Service Alert: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **\n\n" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$\n" | /usr/sbin/sendmail -t

```

But thats not wokring.

The strange thing is, if I run that same command from command line (and replace $CONTACTEMAIL$ with a valid email), it will happily send. And if i replace | /urs/sbin/sendmail -t with >> /tmp/notifications, it will happily output the correct syntax for sendmail to a text file.

I'm pulling my hair out trying to figure out why its not working. And im sure its gonna be something simple.

Any advice would be appreciated.

Thanks.

---

### Post by Chrus on 2011-02-10
bump

---

### Post by Chrus on 2011-02-10
Never mind. All sorted. Nagios was timing out after 30 seconds. Just increased the timeout to 120 secs and it works now. Still takes about a min to send an email, which is way too long... but thats a whole other issue.

---

