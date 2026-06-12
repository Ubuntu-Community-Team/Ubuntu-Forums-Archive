---
title: "Mail Server not allowing externall devices to connect"
date: 2012-01-09
forum: Server Platforms
---

### Post by DanHorniblow on 2012-01-09
Hi, I have recently just bought a VPS and I have followed this tutorial to set it up.

[http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3]("http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3")

Everything is working fine apart from email. The webmail works fine, I can send and view my mailbox.

However when I try to connect to my mail server externally via Outlook or my phone ect. I cant connect to my SMTP server. So I can recive mail but not send.

Any ideas what I might have done wrong?

Cheers Dan

---

### Post by SlugSlug on 2012-01-09
can you post the output of 

tail -30 /var/log/mail.log


when you try to connect a device

---

### Post by SeijiSensei on 2012-01-09
Common implementations of both sendmail and Postfix typically bind the SMTP server to the localhost (127.0.0.1) interface making it invisible to external hosts.  I'd look at the configuration file for your SMTP server to make sure it's listening on the external IP address.

Next, perhaps you're running a firewall of some kind?  Does it have a rule to permit traffic to the external port 25?

I'm assuming that your VPS provider doesn't block port 25 traffic as residential providers commonly do.  Still it's worth checking with them to make sure.

---

### Post by DanHorniblow on 2012-01-10
Hi, sorry for the late reply people.

I have looked at the mail.log, and when I try to connect to postfix from a different ip rather than 127.0.0.1 or localhost nothing happens and there is no log entry either.

I have looked through the tutorial taht I followed a few times and I can't see that I have installed a firewall. I am quite new to ubuntu and I don't know what all the packages are.

Its almost as if postfix is not allowing external IP's to connect.

---

### Post by DanHorniblow on 2012-01-10
Here is part of /var/log/mail.log anyway if it helps.

Jan  8 06:30:01 danhosting pop3d: Connection, ip=[::ffff:127.0.0.1]
Jan  8 06:30:01 danhosting pop3d: Disconnected, ip=[::ffff:127.0.0.1]
Jan  8 06:30:01 danhosting imapd: Connection, ip=[::ffff:127.0.0.1]
Jan  8 06:30:01 danhosting imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
Jan  8 06:30:01 danhosting postfix/smtpd[12651]: connect from localhost.localdomain[127.0.0.1]
Jan  8 06:30:01 danhosting postfix/smtpd[12651]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Jan  8 06:30:01 danhosting postfix/smtpd[12651]: disconnect from localhost.localdomain[127.0.0.1]
Jan  8 06:35:02 danhosting pop3d: Connection, ip=[::ffff:127.0.0.1]
Jan  8 06:35:02 danhosting pop3d: Disconnected, ip=[::ffff:127.0.0.1]
Jan  8 06:35:02 danhosting imapd: Connection, ip=[::ffff:127.0.0.1]
Jan  8 06:35:02 danhosting imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
Jan  8 06:35:02 danhosting postfix/smtpd[12716]: connect from localhost.localdomain[127.0.0.1]
Jan  8 06:35:02 danhosting postfix/smtpd[12716]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Jan  8 06:35:02 danhosting postfix/smtpd[12716]: disconnect from localhost.localdomain[127.0.0.1]

---

### Post by SeijiSensei on 2012-01-10
I still think your server is [bound]("http://www.postfix.org/postconf.5.html#inet_interfaces") to the 127.0.0.1 interface.
> Common implementations of both sendmail and Postfix typically bind the SMTP server to the localhost (127.0.0.1) interface **making it invisible to external hosts**.  I'd look at the configuration file for your SMTP server to make sure it's listening on the external IP address.

For Postfix, you also need to check the [mynetworks parameter]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from") in the main.cf file to make sure all possible sending addresses are allowed.

---

### Post by elico on 2012-01-11
use 
> netstat -ntlp
to see postfix binded interface

---

### Post by DanHorniblow on 2012-01-11
Hi I ran that command and it gave me this:

root@danhosting:~# netstat -ntlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1634/apache2
tcp        0      0 0.0.0.0:8081            0.0.0.0:*               LISTEN      1634/apache2
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      1535/pure-ftpd (SER
tcp        0      0 46.32.229.150:53        0.0.0.0:*               LISTEN      729/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      729/named
tcp        0      0 0.0.0.0:22200           0.0.0.0:*               LISTEN      604/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      12208/master
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      729/named
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      1634/apache2
tcp        0      0 0.0.0.0:2083            0.0.0.0:*               LISTEN      1634/apache2
tcp        0      0 127.0.0.1:10024         0.0.0.0:*               LISTEN      902/amavisd (master
tcp        0      0 127.0.0.1:10025         0.0.0.0:*               LISTEN      12208/master
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      738/mysqld
tcp6       0      0 :::143                  :::*                    LISTEN      1322/couriertcpd
tcp6       0      0 :::21                   :::*                    LISTEN      1535/pure-ftpd (SER
tcp6       0      0 :::53                   :::*                    LISTEN      729/named
tcp6       0      0 :::22200                :::*                    LISTEN      604/sshd
tcp6       0      0 ::1:953                 :::*                    LISTEN      729/named
tcp6       0      0 :::993                  :::*                    LISTEN      1350/couriertcpd
tcp6       0      0 :::995                  :::*                    LISTEN      1400/couriertcpd
tcp6       0      0 :::110                  :::*                    LISTEN      1372/couriertcpd
root@danhosting:~#

Am a being stupid or is there no reference to postfix in there?

Thanks Dan

---

### Post by elico on 2012-01-11
well it's ok by the listening stuff but you must use sasl and other authentication stuff to make your server run.
sorry to tell you that i dont like ispconfig for server setup.
this is kind of simple to setup mail server.
this:
[http://workaround.org/ispmail/squeeze](http://workaround.org/ispmail/squeeze)

is one very good tutorial that will make you understand what you are doing instead of doing a step by step guide with nothing less to understand.

---

### Post by SeijiSensei on 2012-01-11
> **DanHorniblow said:**
> Am a being stupid or is there no reference to postfix in there?

The entry "tcp 0 0 0.0.0.0:25 0.0.0.0:* LISTEN 12208/master" refers to Postfix, I believe.

---

### Post by DanHorniblow on 2012-01-11
Hi, I have been researching my problem, and apparently its a common problem with ubuntu 11.10.

Its something to do with saslauthd and how the users authenticate against the SMTP server. I am not very familiar with lniux mail servers as the mail server I am using has replaced a windows hmailserver.

I find it strange tho that squirrelMail will work and not external connections.

When a external device attempts to authenticate with postfix:

```
SASL LOGIN authentication failed: no mechanism available
```

Is entered into /var/log/mail.log.

I have tried [this fix]("http://www.howtoforge.com/ubuntu-11.10-saslauthd-sasl-plain-authentication-failed-no-mechanism-available") and it doesn't seem to work for me.

Any suggestions?

Many Thanks Dan

---

