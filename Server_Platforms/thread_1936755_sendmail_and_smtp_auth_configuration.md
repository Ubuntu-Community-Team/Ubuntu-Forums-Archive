---
title: "sendmail and smtp auth configuration"
date: 2012-03-06
forum: Server Platforms
---

### Post by maclenin on 2012-03-06
Here's hoping this thread evolves into a **sendmail** "how-to"....

Essentially, I am trying to send a sample php mail() from localhost via smtp auth relay using sendmail.

**A.** First.

1. I installed both **sendmail** and **sasl2**.

2. I created **client_info** in /etc/mail/auth/, with the following contents:
```
AuthInfo:smtpauth.relay.net "U:root" "I:user@relay.net" "P:pwd"
```

3. I created the **client_info.db** file using:
```
makemap hash client_info < client_info
```

3.a. I set permissions:
```
chmod 600 client_info*
```

4. I added the following to the END of **sendmail.mc**...
```
define(`SMART_HOST',`smtpauth.relay.net')dnl
define(`confAUTH_MECHANISMS', `EXTERNAL GSSAPI DIGEST-MD5 CRAM-MD5 LOGIN PLAIN')dnl
FEATURE(`authinfo',`hash /etc/mail/auth/client_info')dnl
```

5 ...and created **sendmail.cf** using:
```
m4 sendmail.mc > sendmail.cf
```

6. I even added **Sendmail.conf** to /user/lib/sasl2/...just in case, with the following contents:
```
pwcheck_method: saslauthd
#mech_list: LOGIN PLAIN
```

7. I restarted BOTH **saslauthd** and **sendmail** using...
```
sudo service saslauthd restart
```
...and...
```
sudo service sendmail restart
```

**B.** Then.

8. I tried to send this email sample...
[PHP]<?php

ini_set("sendmail_from","test@test.com");

$to='test@test.com';
$subject='php mail!';
$message='hello';
$headers='From: test@test.com' . "\r\n" .
'Reply-To: test@test.com' . "\r\n" .
'X-Mailer: PHP/' . phpversion();

if (mail($to,$subject,$message,$headers))
echo "Mail sent!";
else echo "Mail NOT sent!";

?>[/PHP]

...with **Mail sent!** appearing in my browser (FF) window.

**C.** However.

9. I also found these log entries in /var/log/mail.log...

```
Mar  6 18:42:27 localhost sm-mta[7924]: starting daemon (8.14.4): SMTP+queueing@00:10:00
Mar  6 18:43:16 localhost sendmail[7999]: q26IhGmv007999: **[COLOR="DarkGreen"]from=www-data[/COLOR]**, size=183, class=0, nrcpts=1, msgid=<201203061843.q26IhGmv007999@localhost.localdomain>, relay=www-data@localhost
Mar  6 18:43:16 localhost sm-mta[8000]: q26IhGYN008000: **[COLOR="DarkGreen"]from=<www-data@localhost.localdomain>[/COLOR]**, size=416, class=0, nrcpts=1, msgid=<201203061843.q26IhGmv007999@localhost.localdomain>, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Mar  6 18:43:16 localhost sendmail[7999]: q26IhGmv007999: to=test@test.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30183, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (q26IhGYN008000 Message accepted for delivery)
Mar  6 18:43:17 localhost sm-mta[8002]: STARTTLS=client, relay=smtpauth.relay.net., version=TLSv1/SSLv3, **[COLOR="DarkOrange"]verify=FAIL[/COLOR]**, cipher=AES256-SHA, bits=256/256
Mar  6 18:43:17 localhost sm-mta[8002]: q26IhGYN008000: to=<test@test.com>, ctladdr=<www-data@localhost.localdomain> (33/33), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=120416, relay=smtpauth.relay.net. [207.69.189.203], dsn=5.1.1, **[COLOR="DarkOrange"]stat=User unknown[/COLOR]**
Mar  6 18:43:18 localhost sm-mta[8002]: q26IhGYN008000: q26IhIYN008002: **[COLOR="DarkOrange"]DSN: User unknown[/COLOR]**
Mar  6 18:43:18 localhost sm-mta[8002]: q26IhIYN008002: **[COLOR="DarkGreen"]to=<www-data@localhost.localdomain>[/COLOR]**, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent
```

...and no email from test[at]test.com in the test[at]test.com inbox.

NB0: I am wondering whether the (3) log entries marked in **[COLOR="DarkOrange"]BOLD DARK ORANGE[/COLOR]** might be of particular interest or relevance....
NB1: I find the "from=" address (www-data) in the log entries marked in **[COLOR="DarkGreen"]BOLD DARK GREEN[/COLOR]** curious, as well, given the sendmail_from... [PHP]ini_set("sendmail_from","test@test.com");[/PHP] ...address explicitly defined in the php mail() script....

Thanks for any wisdom!

---

