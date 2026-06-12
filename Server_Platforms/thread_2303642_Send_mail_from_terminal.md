---
title: "Send mail from terminal"
date: 2015-11-20
forum: Server Platforms
---

### Post by iacoposk8 on 2015-11-20
Hello everyone! I'm trying to send an anonymous email to a SMTP server that should not have authentication.

the file /etc/postfix/main.cf it is configured so
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mezzo-VirtualBox
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mezzotestlinux.com, mezzo-VirtualBox, localhost.localdomain, localhost
relayhost = pop3.btconnect.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = all

``` 

I modified the relayhost with different SMTP servers but more or less always with the same result

 and read /var/log/mail.log


```

Nov 20 09:14:08 mezzo-VirtualBox postfix/smtp[4577]: connect to pop3.btconnect.com[213.123.26.23]:25: Connection timed out
Nov 20 09:14:08 mezzo-VirtualBox postfix/smtp[4578]: connect to pop3.btconnect.com[213.123.26.23]:25: Connection timed out
Nov 20 09:14:08 mezzo-VirtualBox postfix/smtp[4577]: 0E02C4D304: to=<**************@gmail.com>, relay=none, delay=1463, delays=1432/0.12/30/0, dsn=4.4.1, status=deferred (connect to pop3.btconnect.com[213.123.26.23]:25: Connection timed out)
Nov 20 09:14:08 mezzo-VirtualBox postfix/smtp[4581]: connect to pop3.btconnect.com[213.123.26.23]:25: Connection timed out
Nov 20 09:14:08 mezzo-VirtualBox postfix/smtp[4579]: connect to pop3.btconnect.com[213.123.26.23]:25: Connection timed out
Nov 20 09:14:08 mezzo-VirtualBox postfix/smtp[4580]: connect to pop3.btconnect.com[213.123.26.23]:25: Connection timed out
Nov 20 09:14:08 mezzo-VirtualBox postfix/smtp[4578]: D9A644AB26: to=<**************@gmail.com>, relay=none, delay=1077, delays=1047/0.07/30/0, dsn=4.4.1, status=deferred (connect to pop3.btconnect.com[213.123.26.23]:25: Connection timed out)
Nov 20 09:14:08 mezzo-VirtualBox postfix/smtp[4579]: 9E4894A6E6: to=<**************@gmail.com>, relay=none, delay=547, delays=516/0.1/30/0, dsn=4.4.1, status=deferred (connect to pop3.btconnect.com[213.123.26.23]:25: Connection timed out)
Nov 20 09:14:09 mezzo-VirtualBox postfix/smtp[4581]: E07D44A826: to=<**************@gmail.com>, relay=none, delay=1087, delays=1057/0.1/30/0, dsn=4.4.1, status=deferred (connect to pop3.btconnect.com[213.123.26.23]:25: Connection timed out)
Nov 20 09:14:09 mezzo-VirtualBox postfix/smtp[4580]: 2E2A34A825: to=<**************@gmail.com>, relay=none, delay=1479, delays=1449/0.09/30/0, dsn=4.4.1, status=deferred (connect to pop3.btconnect.com[213.123.26.23]:25: Connection timed out)

```

I run the test writing
```

echo testing | mail -s Bla **************@gmail.com
```

---

### Post by Habitual on 2015-11-20
```
telnet pop3.btconnect.com 25
``` illustrates the issue.
Investigate that and you'll have your answer.

---

### Post by iacoposk8 on 2015-11-20
pop3.btconnect.com has problems
but i try this:
```

telnet out.alice.it 25
Trying 82.57.200.132...
Connected to out.aliceposta.it.
Escape character is '^]'.
220 smtp207.alice.it ESMTP Service ready
Connection closed by foreign host.

```

i change the file /etc/postfix/main.cf so
relayhost = out.alice.it

and from log i read
```

Nov 20 17:55:48 mezzo-System-Product-Name postfix/pickup[8823]: 519BB501135: uid=1000 from=<mezzo@mezzo-System-Product-Name>
Nov 20 17:55:48 mezzo-System-Product-Name postfix/cleanup[8874]: 519BB501135: message-id=<20151120165548.519BB501135@mezzo-System-Product-Name>
Nov 20 17:55:48 mezzo-System-Product-Name postfix/qmgr[8824]: 519BB501135: from=<mezzo@mezzo-System-Product-Name>, size=382, nrcpt=1 (queue active)
Nov 20 17:55:48 mezzo-System-Product-Name postfix/smtp[8876]: 519BB501135: to=<***************@gmail.com>, relay=out.alice.it[82.57.200.132]:25, delay=0.64, delays=0.09/0/0.48/0.07, dsn=5.0.0, status=bounced (host out.alice.it[82.57.200.132] said: 553 <mezzo@mezzo-System-Product-Name> Invalid mail address, must be fully qualified domain (in reply to MAIL FROM command))
Nov 20 17:55:49 mezzo-System-Product-Name postfix/cleanup[8874]: 14556501C59: message-id=<20151120165549.14556501C59@mezzo-System-Product-Name>
Nov 20 17:55:49 mezzo-System-Product-Name postfix/bounce[8877]: 519BB501135: sender non-delivery notification: 14556501C59
Nov 20 17:55:49 mezzo-System-Product-Name postfix/qmgr[8824]: 14556501C59: from=<>, size=2493, nrcpt=1 (queue active)
Nov 20 17:55:49 mezzo-System-Product-Name postfix/qmgr[8824]: 519BB501135: removed
Nov 20 17:55:49 mezzo-System-Product-Name postfix/local[8878]: 14556501C59: to=<mezzo@mezzo-System-Product-Name>, relay=local, delay=0.08, delays=0.03/0/0/0.05, dsn=2.0.0, status=sent (delivered to mailbox)
Nov 20 17:55:49 mezzo-System-Product-Name postfix/qmgr[8824]: 14556501C59: removed

```
it say delivered to mailbox


 
 
 but I do not get anything to my mailbox

---

### Post by Habitual on 2015-11-20
Try
```
mail -s Test mezzo < /dev/null
```
If mezzo is your local user name, or send a blank email to root using
```
mail -s Test root < /dev/null
```

Use the mail c-line utility to read them.
```
sudo mail -u mezzo
``` or 
```
sudo mail 
```

---

### Post by iacoposk8 on 2015-11-21
thanks for the help :)
```

[COLOR=#00ff00]mezzo@mezzo-System-Product-Name:[/COLOR]~$ mail -s Test mezzo < /dev/null
mail: Null message body; hope that's ok
[COLOR=#00ff00]mezzo@mezzo-System-Product-Name:[/COLOR]~$ mail -s Test root < /dev/null
mail: Null message body; hope that's ok
[COLOR=#00ff00]mezzo@mezzo-System-Product-Name:[/COLOR]~$ sudo mail -u mezzo
[sudo] password di mezzo: 
"/var/mail/mezzo": 2 messages 2 new
>N   1 Mail Delivery Syst ven nov 20 17:55  70/2535  Undelivered Mail Returned
 N   2 Mezzo              sab nov 21 09:54  12/511   Test
? ^CInterrupt
? 
Held 2 messages in /var/mail/mezzo
[COLOR=#00ff00]mezzo@mezzo-System-Product-Name:[/COLOR]~$ sudo mail
"/var/mail/root": 2 messages 2 new
>N   1 Anacron            sab nov 21 09:49  15/681   Anacron job 'cron.daily' 
 N   2 Mezzo              sab nov 21 09:54  12/508   Test
? 
Held 2 messages in /var/mail/root

```

---

### Post by Habitual on 2015-11-21
Well, this shows mail is working on the localhost.
Is there still an issue?

---

### Post by iacoposk8 on 2015-11-22
yes, the address to which I sent the mail has not arrived nothing

---

### Post by iacoposk8 on 2015-11-23
When launching this command
echo testing | mail -s Bla **************@gmail.com
I expect to find an email on **************@gmail.com
but in the inbox I see nothing

---

### Post by smtp on 2015-11-23
Relay server is rejecting messages:

relay=out.alice.it[82.57.200.132]:25, delay=0.64, delays=0.09/0/0.48/0.07, dsn=5.0.0, status=bounce

[SIZE=2][FONT=arial]And bounced message was delivered to your local mailbox (namely to to=<mezzo@mezzo-System-Product-Name>). Would you please specify what do you trying to achieve? I mean why you are trying to use relayhost?[/FONT][/SIZE]

---

### Post by iacoposk8 on 2015-11-23
Send an email from the terminal, if I can anonymously better

---

### Post by smtp on 2015-11-23
Okay and what do you mean by "anonymously"?
For sending messages from terminal you don't need relay host if your system has access to the Internet. If that is the case removing "relayhost = pop3.btconnect.com" form postfix configuration will help.

---

### Post by iacoposk8 on 2015-11-23
by e-mail does not exist, for example, type, [email]testtesttest@test.com[/email]
 I do not want to receive responses from a newsletter

---

### Post by smtp on 2015-11-24
It appears that you need a kind of NDR management. That link is a good introduction: [http://www.postfix.org/bounce.8.html](http://www.postfix.org/bounce.8.html)
NDR management can be done via few techniques - depend of your particular situation.

---

### Post by iacoposk8 on 2015-11-24
with postfix I could not, but with ssmtp yes.
 send email authenticated on aol.com.
 I do a newsletter, if sent 99999999 email, aol.com stops me or it marks me as a spammer?
 I can send email without authentication?

---

### Post by Habitual on 2015-11-24
> **iacoposk8 said:**
> with postfix I could not, but with ssmtp yes.
 send email authenticated on aol.com.
 I do a newsletter, if sent 99999999 email, aol.com stops me or it marks me as a spammer?
 I can send email without authentication?

That's the definition of spamming.

---

### Post by QIII on 2015-11-24
Yes, and I think we're done here.

Closed.

---

### Post by iacoposk8 on 2015-11-25
I would like to send many emails and I did it through ssmtp thanks to this topic:
[http://ubuntuforums.org/showthread.php?t=2303642&page=2](http://ubuntuforums.org/showthread.php?t=2303642&page=2)

 The topic has been closed because it was suspected spam, but I would like to send it to members of my site that are several and the server that is hosted times out.
 I had proposed to send it anonymously, without authentication on aol.com because I would not get 1,000 replies to the newsletter.
 So the questions are two:
 1) I can send the newsletter without logging me?
 2) whether it will or not, it will report as aol.com spammers, or will block my account if I send too much email? and how can I fix? for example by sending 100 emails and then doing break of 15 minutes?
Thanks

---

### Post by howefield on 2015-11-25
And threads merged.

Closing a thread doesn't mean start a new one on the same topic.

---

