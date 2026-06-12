---
title: "php and postfix"
date: 2009-10-21
forum: Server Platforms
---

### Post by jabrilm on 2009-10-21
Hello, I am using PHP and trying to send an email from within the PHP script using the mail() function. This is PHP 5.2.4 and Ubuntu Hardy Heron. I am just trying to send the email to myself to check whether this works. The PHP script does not generate any error and the return value for the mail() function is TRUE, but the email does not arrive.

I had sendmail installed originally but read that people have had better luck with postfix, so I installed that. Postfix seems to be working from what I can tell. I can do

telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 homemade ESMTP Postfix (Ubuntu)
ehlo localhost
250-homemade
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

But the email is still not received from the PHP script. The problem may be in the php.ini file. These are the relevant settings:

[mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

; For Win32 only.
;sendmail_from = [EMAIL="anyone@anyone.com"]anyone@anyone.com[/EMAIL]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t -i

Should I change sendmail_path to point elsewhere? I am not sure where the Postfix sendmail command is located. If I do ls -l on /usr/sbin/sendmail I see that this binary was installed prior to my Postfix installation. 

Thanks for any help you can give.

---

### Post by lykwydchykyn on 2009-10-21
Check /var/log/mail.log.  It should detail the transaction between postfix and your SMTP server.

Are you able to send mail from the console using the mailx command?

---

### Post by falconindy on 2009-10-21
> **jabrilm said:**
> Should I change sendmail_path to point elsewhere? I am not sure where the Postfix sendmail command is located. If I do ls -l on /usr/sbin/sendmail I see that this binary was installed prior to my Postfix installation. 
Postfix acts as a friendly front end to sendmail. Don't worry about the installation date on it.

You can also use 'mailq' to monitor sendmail to make sure that mail items are actually making it as far as into the queue.

---

### Post by jabrilm on 2009-10-22
This is what appears in /var/log/mail.log:

```
Oct 21 23:54:35 homemade postfix/pickup[5735]: 2A31EA70109: uid=33 from=<www-data>
Oct 21 23:54:35 homemade postfix/cleanup[7997]: 2A31EA70109: message-id=<20091022065435.2A31EA70109@homemade>
Oct 21 23:54:35 homemade postfix/qmgr[5736]: 2A31EA70109: from=<www-data@homemade>, size=499, nrcpt=1 (queue active)
Oct 21 23:54:35 homemade postfix/error[7999]: 2A31EA70109: to=<xxx@gmail.com>, relay=none, delay=0.04, delays=0.03/0/0/0.01, dsn=5.0.0, status=bounced (gmail.com)
Oct 21 23:54:35 homemade postfix/cleanup[7997]: 3217DA7010A: message-id=<20091022065435.3217DA7010A@homemade>
Oct 21 23:54:35 homemade postfix/qmgr[5736]: 3217DA7010A: from=<>, size=2095, nrcpt=1 (queue active)
Oct 21 23:54:35 homemade postfix/bounce[8000]: 2A31EA70109: sender non-delivery notification: 3217DA7010A
Oct 21 23:54:35 homemade postfix/qmgr[5736]: 2A31EA70109: removed
Oct 21 23:54:35 homemade postfix/local[8001]: 3217DA7010A: to=<www-data@homemade>, relay=local, delay=0.03, delays=0/0.02/0/0.01, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Oct 21 23:54:35 homemade postfix/qmgr[5736]: 3217DA7010A: removed
```

If I try mailx, I get the following automatic response in my local mailbox:

```
I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<xxx@gmail.com>: gmail.com

--ADF25A70109.1256194556/homemade
Content-Description: Delivery report
Content-Type: message/delivery-status

Reporting-MTA: dns; homemade
X-Postfix-Queue-ID: ADF25A70109
X-Postfix-Sender: rfc822; gabrielm@homemade
Arrival-Date: Wed, 21 Oct 2009 23:55:56 -0700 (PDT)

Final-Recipient: rfc822; [EMAIL="xxx@gmail.com"]xxx@gmail.com[/EMAIL]
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; gmail.com

--ADF25A70109.1256194556/homemade
Content-Description: Undelivered Message
Content-Type: message/rfc822

Received: by homemade (Postfix, from userid 1000)
        id ADF25A70109; Wed, 21 Oct 2009 23:55:56 -0700 (PDT)
To: [EMAIL="xxx@gmail.com"]xxx@gmail.com[/EMAIL]
Subject: just a mailx test
Message-Id: <20091022065556.ADF25A70109@homemade>
Date: Wed, 21 Oct 2009 23:55:56 -0700 (PDT)
From: gabrielm@homemade (GM)

hello, this is a mailx test
...

--ADF25A70109.1256194556/homemade--
```

If I type mailq after running the PHP script, I get the response "Mail queue is empty".

(I've replaced my gmail address throughout with xxx for spam avoidance)

I find that I can email gabrielm@localhost using mailx and the email arrives successfully in my local mailbox, but if I try to email gabrielm@localhost from within the PHP script, the email is not received.

---

