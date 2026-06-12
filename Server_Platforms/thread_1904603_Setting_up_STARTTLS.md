---
title: "Setting up STARTTLS"
date: 2012-01-05
forum: Server Platforms
---

### Post by defaria on 2012-01-05
Ok I recently updated my server from 10.04 -> 11.04 and my Postfix/STARTTLS configuration broke. Can anybody post the simple steps required to generate a self-signed cert and configure it such that STARTTLS works and I can send email from my cell phone, etc? I'd be very grateful. I've tried many things and they all fail to work.

Thanks.

---

### Post by smtp on 2012-01-05
Hello,

This is covered here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)


Generate certificates to be used for TLS encryption and/or certificate Authentication: 
touch smtpd.key
chmod 600 smtpd.key
openssl genrsa 1024 > smtpd.key
openssl req -new -key smtpd.key -x509 -days 3650 -out smtpd.crt # has prompts
openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out cacert.pem -days 3650 # has prompts
sudo mv smtpd.key /etc/ssl/private/
sudo mv smtpd.crt /etc/ssl/certs/
sudo mv cakey.pem /etc/ssl/private/
sudo mv cacert.pem /etc/ssl/certs/

Configure Postfix to do TLS encryption for both incoming and outgoing mail: 
sudo postconf -e 'smtp_tls_security_level = may'
sudo postconf -e 'smtpd_tls_security_level = may'
sudo postconf -e 'smtpd_tls_auth_only = no'
sudo postconf -e 'smtp_tls_note_starttls_offer = yes'
sudo postconf -e 'smtpd_tls_key_file = /etc/ssl/private/smtpd.key'
sudo postconf -e 'smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt'
sudo postconf -e 'smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem'
sudo postconf -e 'smtpd_tls_loglevel = 1'
sudo postconf -e 'smtpd_tls_received_header = yes'
sudo postconf -e 'smtpd_tls_session_cache_timeout = 3600s'
sudo postconf -e 'tls_random_source = dev:/dev/urandom'
sudo postconf -e 'myhostname = server1.example.com' # remember to change this to yours

---

### Post by defaria on 2012-01-05
I think you need to restart postfix too...

It didn't seem to work however. When sending a message in Thunderbird I get "Sending of message failed. Please verify that your Mail And Newsgroups account settings are correct and try again". In /var/log/syslog I see:

```
Jan  5 09:50:35 defaria postfix/smtpd[29497]: initializing the server-side TLS engine
Jan  5 09:50:35 defaria postfix/smtpd[29498]: initializing the server-side TLS engine
Jan  5 09:50:35 defaria postfix/smtpd[29497]: connect from smtp30.eventful.com[216.240.187.30]
Jan  5 09:50:35 defaria postfix/smtpd[29497]: warning: SASL: Connect to private/dovecot-auth failed: No such file or directory
Jan  5 09:50:35 defaria postfix/smtpd[29497]: fatal: no SASL authentication mechanisms
Jan  5 09:50:35 defaria postfix/smtpd[29498]: connect from unknown[59.103.205.141]
Jan  5 09:50:35 defaria postfix/smtpd[29498]: warning: SASL: Connect to private/dovecot-auth failed: No such file or directory
Jan  5 09:50:35 defaria postfix/smtpd[29498]: fatal: no SASL authentication mechanisms
Jan  5 09:50:36 defaria postfix/master[29367]: warning: process /usr/lib/postfix/smtpd pid 29497 exit status 1
Jan  5 09:50:36 defaria postfix/master[29367]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jan  5 09:50:36 defaria postfix/master[29367]: warning: process /usr/lib/postfix/smtpd pid 29498 exit status 1

```

Worse yet, postfix is not even running:

```

Defaria:telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.

```

---

### Post by smtp on 2012-01-05
Well,

The fatal error listed is that one:
fatal: no SASL authentication mechanisms

It appears that your Postfix is configured to use  SMTP AUTH through Dovecot SASL, thus following document could be helpful: [http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL](http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL)

---

### Post by defaria on 2012-01-06
That's what I thought too however I tried that and it didn't work. Digging a slight bit deeper, I don't seem to have a /var/spool/postfix/private/auth socket file. I have others, but not this one.

OK got it. I needed to restart devcot. Then the socket file got created and I think I'm OK...

---

### Post by smtp on 2012-01-06
oki doki

---

