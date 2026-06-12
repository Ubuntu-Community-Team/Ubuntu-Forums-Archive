---
title: "Need help with Email Server..."
date: 2007-09-04
forum: Server Platforms
---

### Post by creolbuay on 2007-09-04
Hi all.
Been a while. I tried setting up an email server using Courier and Postfix.

I used the basic config settings as outlined on the sites for either software packages even searched online but no help..

I can connect to the server fine, I can setup account on all email client software (outlook, outlook express, thunderbird). However, I cannot send or receive emails. I am currently running on a dynamic ip address which I'v tried before ad it worked but I had to rebuild the server due to an upgrade gone bad and now it wont work.

I am running on Ubuntu 7.04

---

### Post by creolbuay on 2007-09-04
/etc/postfix/main.cnf

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
#myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
#delay_warning_time = 4h
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
myhostname = mail.domain.com
mydomain = domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
recipient_delimiter = +
mydestination = mail.domain.com localhost.domain.com domain.com localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
```

---

### Post by KCPokes on 2007-09-04
Do you have DNS set up for your mail server?  At least set in your host file such that it presents a valid name when typing `hostname`?  The issues I've seen in the past with mail servers are typically around DNS, as far as receiving goes.  In regards to sending, you'll need to ensure you have it set up with a proper relay, such as your ISP's SMTP server.

---

### Post by creolbuay on 2007-09-04
telnet mail.domain.com 25

```
Trying 76.29.127.204...
Connected to mail.domain.com.
Escape character is '^]'.
220 mail.domain.com ESMTP Postfix (Ubuntu)
ehlo mail.domain.com
250-mail.domain.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
quit
221 2.0.0 Bye
Connection closed by foreign host.
```

---

### Post by creolbuay on 2007-09-04
tail -f /var/log/mail.log

```
Sep  4 22:26:09 server postfix/smtp[16262]: 2149BB042D5: to=<my_email@domain.com>, relay=mx01.domain.com[***.**.**.***]:25, delay=0.8, delays=0.41/0.02/0.21/0.16, dsn=5.7.1, status=bounced (host mx01.domain.com[***.**.**.***] said: 554 5.7.1 Service unavailable; Client host [**.**.***.***] blocked using zen.spamhaus.org; http://www.spamhaus.org/query/bl?ip=**.**.***.*** (in reply to RCPT TO command))
Sep  4 22:26:09 server postfix/cleanup[16261]: DF61DB042D9: message-id=<20070905032609.DF61DB042D9@mail.fiwebelize.com>
Sep  4 22:26:09 server postfix/qmgr[15893]: DF61DB042D9: from=<>, size=2828, nrcpt=1 (queue active)
Sep  4 22:26:09 server postfix/bounce[16265]: 2149BB042D5: sender non-delivery notification: DF61DB042D9
Sep  4 22:26:09 server postfix/qmgr[15893]: 2149BB042D5: removed
Sep  4 22:26:09 server postfix/local[16266]: DF61DB042D9: to=<my_email@mydomain.com>, relay=local, delay=0.06, delays=0.02/0.01/0/0.03, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Sep  4 22:26:09 server postfix/qmgr[15893]: DF61DB042D9: removed
Sep  4 22:26:35 server imapd: Connection, ip=[::ffff:127.0.0.1]
Sep  4 22:27:12 server postfix/smtpd[16257]: connect from c-**.**.***.***.hsd1.il.comcast.net[**.**.***.***]
Sep  4 22:27:26 server postfix/smtpd[16257]: disconnect from c-**.**.***.***.hsd1.il.comcast.net[**.**.***.***]
Sep  4 22:29:47 server postfix/smtpd[16272]: cannot load Certificate Authority data
Sep  4 22:29:47 server postfix/smtpd[16272]: warning: TLS library problem: 16272:error:02001002:system library:fopen:No such file or directory:bss_file.c:122:fopen('/etc/ssl/certs/cacert.pem','r'):
Sep  4 22:29:47 server postfix/smtpd[16272]: warning: TLS library problem: 16272:error:2006D080:BIO routines:BIO_new_file:no such file:bss_file.c:125:
Sep  4 22:29:47 server postfix/smtpd[16272]: warning: TLS library problem: 16272:error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib:by_file.c:274:
Sep  4 22:29:47 server postfix/smtpd[16272]: connect from bay0-omc3-s13.bay0.hotmail.com[**.**.***.***]
Sep  4 22:29:47 server postfix/smtpd[16272]: E134CB042D5: client=bay0-omc3-s13.bay0.hotmail.com[**.**.***.***]
Sep  4 22:29:48 server postfix/cleanup[16275]: E134CB042D5: message-id=<BAY117-DAV168B46F8BD034C3860D3909BCB0@phx.gbl>
Sep  4 22:29:48 server postfix/cleanup[16275]: E134CB042D5: message-id=<000001c7ef6d$04857f80$640aa8c0@fiwebeli57c878>
Sep  4 22:29:48 server postfix/qmgr[15893]: E134CB042D5: from=<my_email@hotmail.com>, size=2822, nrcpt=1 (queue active)
Sep  4 22:29:48 server postfix/local[16277]: E134CB042D5: to=<my_email@mydomain.com>, relay=local, delay=0.27, delays=0.23/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Sep  4 22:29:48 server postfix/qmgr[15893]: E134CB042D5: removed
Sep  4 22:29:48 server postfix/smtpd[16272]: disconnect from bay0-omc3-s13.bay0.hotmail.com[**.**.***.***]
```

---

### Post by creolbuay on 2007-09-04
Ay help you guys can offer would be much appreciated. If you need more info from me just ask.

---

### Post by creolbuay on 2007-09-05
I have the dns mapping and stuff done through the servers of my friend as he does that type of stuff. Here is what i got from him:

$TTL 3600
@       IN      SOA ns1.domain.net. hostmaster.domain.net. (
                2007060701
                3600
                120
                1209600
                3600 )


@         IN      MX      100     mail.domain.com.
@         IN      NS              ns1.domain.net.
@         IN      NS              ns1.domain.net.
@         IN      A               my external IP
www    IN      A               my external IP
wiki      IN      A              my external IP
pics      IN      A               my external IP
forum   IN      A               my external IP
ftp      IN      A             my external IP
mail    IN      A               my external IP
irc      IN      A               my external IP

---

### Post by creolbuay on 2007-09-05
OK. After hours with Comcast I found out that they do not allow imap mail servers.

Any suggestions on where to go next?

---

### Post by creolbuay on 2007-09-05
Just ran tail -f /var/log/mail.log again and got:

Sep  5 18:05:49 pelican postfix/smtpd[25690]: connect from unknown[208.47.211.203]
Sep  5 18:05:49 pelican postfix/smtpd[25690]: NOQUEUE: reject: RCPT from unknown[208.47.211.203]: 554 5.7.1 <receiver@their_domain.com>: Relay access denied; from=<me@my_domain.com> to=<receiver@their_domain.com> proto=ESMTP helo=<BELIKIN>
Sep  5 18:05:51 pelican postfix/smtpd[25690]: disconnect from unknown[208.47.211.203]

---

### Post by creolbuay on 2007-09-05
So to bypass the comcast issue I did the following:

touch /etc/postfix/smtp_relayhost_auth

to which I added:

[smtp.comcast.net] username:password

executed postmap /etc/postfix/smtp_relayhost_auth

then in /etcp/postfix/main.cf I added:

relayhost = [smtp.comcast.net]
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/smtp_relayhost_auth
smtp_sasl_security_options = noanonymous

reloaded postfix and wala! :guitar:

---

