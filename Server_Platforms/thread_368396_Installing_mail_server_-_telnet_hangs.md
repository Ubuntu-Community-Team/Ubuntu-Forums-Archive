---
title: "Installing mail server - telnet hangs"
date: 2007-02-23
forum: Server Platforms
---

### Post by Fíona on 2007-02-23
I am setting up a mail server using;

[INDENT][/INDENT][https://help.ubuntu.com/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/ubuntu/serverguide/C/email-services.html)

After configuring sasl the how to recommends testing the configuration using telnet.

Telnet hangs after giving escape character 

fiona@server:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

My postfix/main.cf look like this:

fiona@server:~$ cat /etc/postfix/main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = server.localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = server.localhost.localdomain, localhost.localhost.localdomain, localhost
relayhost = mail.home.nl
mynetworks = 127.0.0.0/8 192.168.1.0/24 192.168.1.100/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = nonanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = /dev:/dev/urandom

Is there anyone who can give me an idea as to why I can't test my setup so far?

---

### Post by Child of Wonder on 2007-02-23
Check /var/log/mail.log to see if SASL is failing to start or some other error.

---

### Post by Fíona on 2007-02-23
I have the following message in /var/log/mail.log

server postfix/tlsmgr[23966]: exiting to reopen external entropy source /dev:/dev/urandom

This message appears over and over again.

---

### Post by MJN on 2007-02-23
Remove the leading / from  tls_random_source i.e.  [B]tls_random_source = dev:/dev/urandom

[/B]Mathew

---

### Post by Fíona on 2007-02-23
Thanks for the tip Mathew.
I have removed the slash as you suggested. I had also added 
[INDENT][/INDENT]mailbox_command = procmail -a "$EXTENSION"
before your post.

Your suggestion has changed the situation
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.

In the logs I'm also getting this;

fiona@server:/$ tail -f /var/log/mail.log
Feb 23 20:40:05 server postfix/smtpd[5298]: warning: unknown SASL security options value "nonanonymous" in "nonanonymous"
Feb 23 20:40:05 server postfix/smtpd[5298]: warning: bad per-session SASL security properties
Feb 23 20:40:05 server postfix/smtpd[5298]: fatal: SASL per-connection initialization failed
Feb 23 20:40:06 server postfix/master[5063]: warning: process /usr/lib/postfix/smtpd pid 5298 exit status 1
Feb 23 20:40:06 server postfix/master[5063]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Feb 23 20:41:06 server postfix/smtpd[5325]: warning: unknown SASL security options value "nonanonymous" in "nonanonymous"
Feb 23 20:41:06 server postfix/smtpd[5325]: warning: bad per-session SASL security properties
Feb 23 20:41:06 server postfix/smtpd[5325]: fatal: SASL per-connection initialization failed
Feb 23 20:41:07 server postfix/master[5063]: warning: process /usr/lib/postfix/smtpd pid 5325 exit status 1
Feb 23 20:41:07 server postfix/master[5063]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

I wouldn't say that I understand what this means!

Little by little we're getting there!

---

### Post by MJN on 2007-02-23
Yet another typo I'm afraid!

** smtpd_sasl_security_options = no_n_anonymous** (remove the n)

Maybe it might be worth copy-and-pasting the HowTo as typos are so easy to introduce otherwise (as I'm sure you'd agree!)... However, this last one might be enough to get it moving.

Mathew

---

### Post by Fíona on 2007-02-23
Mathew, thanks for helping again. I'll check it out tomorrow, I"m going to bed!!

---

### Post by Fíona on 2007-02-23
Just had to have a look before going to bed.

It was indeed the typo!

Thanks a million.

---

