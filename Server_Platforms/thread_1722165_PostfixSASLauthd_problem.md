---
title: "Postfix/SASLauthd problem"
date: 2011-04-05
forum: Server Platforms
---

### Post by TheGrave on 2011-04-05
Hello,

I have a pretty basic problem I think. Managed to setup a mail server as per this guide:

[http://flurdy.com/docs](http://flurdy.com/docs) 

Everything runs (almost) perfectly smooth (sending and receiving e-mail to and from external domains, spam/av filtering, greylisting, etc.) but I discovered that if I login from anywhere I can send an e-mail from an existing virtual mailbox user to another virtual mailbox user without any requirements for authentication. Here is the output:

```
220 mail.mydomain.com ESMTP Postfix
ehlo test
250-mail.mydomain.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH PLAIN CRAM-MD5 DIGEST-MD5 LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: [EMAIL="info@mydomain.com"]info@mydomain.com[/EMAIL]
250 2.1.0 Ok
rcpt to: _test_[EMAIL="s.stefanov@mydomain.com"]@mydomain.com[/EMAIL]
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
test
,.

.
250 2.0.0 Ok: queued as 3D940810A4
```Now, I've been testing this on port 25, maybe with Submission I'll get different results as the daemon runs with different parameters there but before I get to this part I want to fix the problem.

As far as I know this thing is controlled via main.cf with the smtpd_sasl_security_options = noanonymous option. Doesn't work with me for some reason. I'm attaching main.cf and master.cf for reference. Any idea how to tackle this issue?

---

### Post by falko on 2011-04-05
This might help: [http://www.howtoforge.com/forums/showpost.php?p=214430&postcount=4](http://www.howtoforge.com/forums/showpost.php?p=214430&postcount=4)

---

### Post by elico on 2011-04-06
if you want only reliable server to have the option to send you emails then use RBL such as 
[http://www.spamhaus.org/](http://www.spamhaus.org/)
or others.

very helpful!!

---

### Post by TheGrave on 2011-04-06
> **falko said:**
> This might help: [http://www.howtoforge.com/forums/showpost.php?p=214430&postcount=4](http://www.howtoforge.com/forums/showpost.php?p=214430&postcount=4)

Well, not really but thanks for pointing out:) SMTP-AUTH is enabled as you can see in my config but anonymous access is still allowed for local users.

> **elico said:**
> if you want only reliable server to have the option to send you emails then use RBL such as 
[http://www.spamhaus.org/](http://www.spamhaus.org/)
or others.

very helpful!!

I believe I'm already doing this with the following line in my.cf:

smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org 

Doesn't seem to work though as I can telnet from anywhere and send spam to myself:)

---

### Post by TheGrave on 2011-04-25
I managed to fix the issue myself. You need to add the following to the main.cf file:

# Prevent sending spam from local users without authentication
smtpd_sender_login_maps = mysql:/etc/postfix/mysql_sender_login_maps.cf

and create /etc/postfix/mysql_sender_login_maps.cf with the following content (matching the DB parameters as per the guide mentioned above):

user = dbuser
password = dbpass
hosts = 127.0.0.1
dbname = maildb
table = users
select_field = maildir
where_field = id

Now, another problem comes up (not related to this one for sure) - postfix started sending 2 copies of each forwarded e-mail to my external alias but that's something I'm just about to dig.

---

