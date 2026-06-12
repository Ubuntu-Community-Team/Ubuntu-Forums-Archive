---
title: "Relay access denied when sending through postfix"
date: 2007-05-12
forum: Server Platforms
---

### Post by KenSentMe on 2007-05-12
I've installed a postfix-courier mailserver following this tutorial: [http://workaround.org/articles/ispmail-sarge/](http://workaround.org/articles/ispmail-sarge/) .

Everything seems to work fine, only sending mails from clients from outside of the server network doesn't work. When i try to send an email to my smtp server and using the correct username and password for authentication i get the error 'relay access denied'.

This is what my main.cf looks like:

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

# TLS parameters
smtpd_tls_cert_file=/etc/postfix/smtpd.cert
smtpd_tls_key_file=/etc/postfix/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = MYDOMAIN.COM
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/mail/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smptd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated

content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
```

Sending mail from the remote clients only works when i add their ip address to mynetworks, but this is only a workaround of the problem and i want to be able to send mail from any place and not only predefined places. Does anyone have a clue on how to solve this?

---

### Post by MJN on 2007-05-12
Can you post your logs?

The 'permit_sasl_authenticated' directive should allow your clients to relay, hence it sounds like they're not authenticating...

Mathew

---

### Post by KenSentMe on 2007-05-13
This is the log part when a user tries to send a mail through postfix:

```

May 13 10:57:11 localhost postfix/smtpd[22244]: connect from kensentme.xs4all.nl[82.92.80.8]
May 13 10:57:11 localhost postfix/smtpd[22244]: NOQUEUE: reject: RCPT from kensentme.xs4all.nl[82.92.80.8]: 554 <jeroen.vandenieuwenhof@gmail.com>: Relay access denied; from=<jeroen@vandenieuwenhof.nl> to=<jeroen.vandenieuwenhof@gmail.com> proto=ESMTP helo=<[10.0.0.152]>
May 13 10:57:11 localhost postfix/smtpd[22244]: disconnect from kensentme.xs4all.nl[82.92.80.8]

```

---

### Post by MJN on 2007-05-13
Yeah, your client isn't authenticating. Compare with one that does:

```
May 12 13:51:20 localhost postfix/smtpd[6439]: connect from 82-46-99-50.cable.ubr01.chap.blueyonder.co.uk[82.46.99.50]
May 12 13:51:20 localhost postfix/smtpd[6439]: setting up TLS connection from 82-46-99-50.cable.ubr01.chap.blueyonder.co.uk[82.46.99.50]
May 12 13:51:20 localhost postfix/smtpd[6439]: TLS connection established from 82-46-99-50.cable.ubr01.chap.blueyonder.co.uk[82.46.99.50]: SSLv3 with cipher RC4-MD5 (128/128 bits)
May 12 13:51:21 localhost postfix/smtpd[6439]: 53821799D0: client=82-46-99-50.cable.ubr01.chap.blueyonder.co.uk[82.46.99.50],sasl_method=LOGIN, sasl_username=frank
May 12 13:51:22 localhost postfix/cleanup[6445]: 53821799D0: message-id=<20070512125121.53821799D0@mail.newtonnet.co.uk>
May 12 13:51:22 localhost postfix/smtp[6446]: 53821799D0: to=<bill@example.com>, relay=smtp.blueyonder.co.uk[195.188.53.60], delay=1, status=sent (250 OK id=1Hmr4E-0005BS-Km)
```Try adding -v to the end of the *smtp ..... smtpd **-v** *line in /etc/postfix/master.cf, restart Postfix and resend - this will reveal the full SMTP dialogue and indicate exactly what is and isn't happening. Of course, also check your client settings to make sure it knows to authenticate (and must use TLS)!

Mathew

---

### Post by KenSentMe on 2007-05-13
Did you mean the line in master.cf, becuase i can't find smtp ... smtpd in main.cf ?

---

### Post by MJN on 2007-05-13
Sorry, yes, didn't proof read what I wrote!

(I'll edit the original)

---

### Post by KenSentMe on 2007-05-13
I've put the log in a pastebin, because it's pretty long. You can find it here: <link removed>

---

### Post by MJN on 2007-05-13
<edit: jumped the gun here - give me a few minutes to rewrite what I put>

---

### Post by KenSentMe on 2007-05-13
You mean it's a problem with Evolution? I have tried it with Thunderbird and the same thing happens.

---

### Post by MJN on 2007-05-13
Actually, checking the logs shows that your TLS is not working - no tunnel is being established hence the client is not authenticating (as it'd reveal it's username/password in the clear).

Double-check the tutorial I guess!

Mathew

---

### Post by KenSentMe on 2007-05-13
I've configured Evolution so that it needs a username and pass to send mail through the smtp server. I told evo to use TLS-encryption and DIGEST-MD5 and gave my username. That should be enough, right?

---

### Post by MJN on 2007-05-13
I'm thinking it's a TLS issue. I'm not familiar with the tutorial you followed so can't comment if it's right or wrong.

I'd recommend reading through the guide at [http://postfix.state-of-mind.de/patrick.koetter/smtpauth/postfix_tls_support.html](http://postfix.state-of-mind.de/patrick.koetter/smtpauth/postfix_tls_support.html) as it least explains the what's *and* why's.

Mathew

---

### Post by MJN on 2007-05-13
Quick thought: Have you tried telling the clients not to use TLS, but still authenticate? This will certainly prove if the authentication side is working. (note your password will be sent in the clear)

Mathew

---

### Post by KenSentMe on 2007-05-13
Okay, i found out that these two lines were missing in main.cf:

smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes

When i added these lines i got a bit further because my mail client asks for the password. But i can't get further then that. Evolution says the connection to the smtp server was lost. I noticed that when i try to restart saslauthd through /etc/init.d/saslauthd restart i get this:

Stopping SASL Authentication Daemon: (not running).
Starting SASL Authentication Daemon: (failed).

This is what my log says when sending a mail:

```

May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 220 MYDOMAIN.COM ESMTP Postfix (Ubuntu)
May 13 12:02:30 localhost postfix/smtpd[23043]: < kensentme.xs4all.nl[82.92.80.8]: EHLO [10.0.0.152]
May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-MYDOMAIN.COM
May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-PIPELINING
May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-SIZE 10240000
May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-VRFY
May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-ETRN
May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-STARTTLS
May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-AUTH LOGIN PLAIN DIGEST-MD5 CRAM-MD5
May 13 12:02:30 localhost postfix/smtpd[23043]: match_list_match: kensentme.xs4all.nl: no match
May 13 12:02:30 localhost postfix/smtpd[23043]: match_list_match: 82.92.80.8: no match
May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-AUTH=LOGIN PLAIN DIGEST-MD5 CRAM-MD5
May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250 8BITMIME
May 13 12:02:30 localhost postfix/smtpd[23043]: < kensentme.xs4all.nl[82.92.80.8]: STARTTLS
May 13 12:02:30 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 220 Ready to start TLS
May 13 12:02:31 localhost postfix/smtpd[23043]: < kensentme.xs4all.nl[82.92.80.8]: EHLO [10.0.0.152]
May 13 12:02:31 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-MYDOMAIN.COM
May 13 12:02:31 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-PIPELINING
May 13 12:02:31 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-SIZE 10240000
May 13 12:02:31 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-VRFY
May 13 12:02:31 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-ETRN
May 13 12:02:31 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-AUTH LOGIN PLAIN DIGEST-MD5 CRAM-MD5
May 13 12:02:31 localhost postfix/smtpd[23043]: match_list_match: kensentme.xs4all.nl: no match
May 13 12:02:31 localhost postfix/smtpd[23043]: match_list_match: 82.92.80.8: no match
May 13 12:02:31 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250-AUTH=LOGIN PLAIN DIGEST-MD5 CRAM-MD5
May 13 12:02:31 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 250 8BITMIME
May 13 12:02:31 localhost postfix/smtpd[23043]: < kensentme.xs4all.nl[82.92.80.8]: AUTH CRAM-MD5
May 13 12:02:31 localhost postfix/smtpd[23043]: smtpd_sasl_authenticate: sasl_method CRAM-MD5
May 13 12:02:31 localhost postfix/smtpd[23043]: smtpd_sasl_authenticate: uncoded challenge: <code@MYDOMAIN.COM>
May 13 12:02:31 localhost postfix/smtpd[23043]: > kensentme.xs4all.nl[82.92.80.8]: 334 <ANOTHERCODE>
May 13 12:02:31 localhost postfix/smtpd[23043]: < kensentme.xs4all.nl[82.92.80.8]: <AGAIN, CODE>
May 13 12:02:31 localhost postfix/smtpd[23043]: smtpd_sasl_authenticate: decoded response: frank@frank.com <FOURTH CODE>
May 13 12:02:31 localhost postfix/master[22975]: warning: process /usr/lib/postfix/smtpd pid 23043 killed by signal 11
May 13 12:02:31 localhost postfix/master[22975]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

```

---

### Post by KenSentMe on 2007-05-13
> **MJN said:**
> Quick thought: Have you tried telling the clients not to use TLS, but still authenticate? This will certainly prove if the authentication side is working. (note your password will be sent in the clear)

Mathew

If i don't use TLS then i get somewhat the same error and the part of the log looks mostly the same. It ends killing the process by signal 11

---

### Post by MJN on 2007-05-13
We're better off leaving TLS out of things for the time being as it's just going to confuse the issue.

Given the authentication is failing (i.e. process kill by signal 11) then it's down to the tutorial I'm afraid... (or your implementation of it!) ;)

Mathew

---

### Post by KenSentMe on 2007-05-13
I'll have another look at the settings and will post my findings here. Thanks for your help!

---

### Post by MJN on 2007-05-13
Good luck! Please don't think I'm disowning you but when a mammoth HowTo is involved it's kind of difficult to trawl through it and test it on theory - you're better off just redoing the steps as presumably, with peer review, it must be 'correct'!

Mathew

---

### Post by KenSentMe on 2007-05-13
> **MJN said:**
> Good luck! Please don't think I'm disowning you but when a mammoth HowTo is involved it's kind of difficult to trawl through it and test it on theory - you're better off just redoing the steps as presumably, with peer review, it must be 'correct'!

Mathew

No, don't worry. I'm very glad that you are trying to help me and i know you can't give me all the answers right away. I will redo the tutorial and report back here if anything fails.

---

