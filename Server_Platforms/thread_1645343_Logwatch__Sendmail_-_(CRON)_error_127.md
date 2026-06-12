---
title: "Logwatch / Sendmail - (CRON) error 127"
date: 2010-12-14
forum: Server Platforms
---

### Post by megaplast on 2010-12-14
Dear all!

I am using ubuntu server 10.10. Tried to create a cronjob for logwatch/sendmail, but without sucess. 
I followed the instructions : [http://ubuntuforums.org/showthread.php?t=1268015]("http://ubuntuforums.org/showthread.php?t=1268015")

When I type :
> sudo grep CRON /var/log/syslog

I get the result :

CRON[27611]: (CRON) error (grandchild #27612 failed with exit status 127)

Any ideas?

Thank you in advance.

---

### Post by windependence on 2010-12-14
If you can't find the problem, then you might consider that the
primary difference between a cron-run job and a hand-run job is that
cron uses a different set of environment variables than are available
to the hand-run job. Take a look at what envvars you set in your
interactive session, and see which are unset or set differently in
your cron session. Probably one or more of those variables are your
difficulty.

Other things to look for:
- current working directory differences
- user/group differences
- PATH differences (part of the envvar differences above)

One or more of these are likely causing your problem

-Tim

---

### Post by megaplast on 2010-12-15
Hello,

thanks for your reply.

Cron was setup to run like this :

> 30 10 * * * /home/ironman/logwatch-sendemail.bash


logwatch-sendemail.bash :

> #!/bin/bash

/usr/sbin/logwatch

sendEmail -v -f [email]sender@gmail.com[/email] -s smtp.gmail.com:587 -xu sender -xp SrvR03 -t [email]receiver@gmail.com[/email] -o tls=yes -u title goes here -m message goes here -a /tmp/logwatch

exit

When I start the command manually everything works fine.

Since I am a ubuntu beginner, any suggestion would be helpful to me. 
Thank you in advance.

---

### Post by megaplast on 2010-12-16
I added sudo and all working properly. Thank you for your help.

> #!/bin/bash

/usr/sbin/logwatch

[COLOR="Red"]sudo[/COLOR] sendEmail -v -f [email]sender@gmail.com[/email] -s smtp.gmail.com:587 -xu sender -xp SrvR03 -t [email]receiver@gmail.com[/email] -o tls=yes -u title goes here -m message goes here -a /tmp/logwatch

exit

---

### Post by fasaxc on 2011-03-12
I had the same problem, which came down to the fact that cron doesn't put /usr/sbin/ on the path by default.  The fix in my case was to change

```
sendmail ...
```

to

```
/usr/sbin/sendmail ...
```

There was no need for sudo (and using sudo without need is bad idea).

---

