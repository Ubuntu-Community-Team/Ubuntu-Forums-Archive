---
title: "Postfix - no Smtp-Auth"
date: 2008-05-20
forum: Server Platforms
---

### Post by klcom on 2008-05-20
Hi,

I am configured a postfix without Smtp-Auth but i can't send mails on internet, but it work correct on the lan.

For exemple i don't understand this:
- Telnet localhost work -

[INDENT]root@muga:/etc/postfix# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 muga.cxg.local ESMTP Postfix (Ubuntu)
mail from:xxxxx@domain.com
250 2.1.0 Ok
rcpt to:external@gmail.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
hola hoa
.
250 2.0.0 Ok: queued as 904C83485E4
quit
221 2.0.0 Bye
Connection closed by foreign host.[/INDENT]

Telnet 192.9.200.27 IP Of the server DO'T  WORK !!!
----------------------------------------------------------
OR Since other machines or thunderbird.

root@muga:/etc/postfix# telnet 192.9.200.27 25
Trying 192.9.200.27...
Connected to 192.9.200.27.
Escape character is '^]'.
220 muga.cxg.local ESMTP Postfix (Ubuntu)
mail from:xxxx@domain.com
250 2.1.0 Ok
rcpt to:egrassot@gmail.com
**554 5.7.1 <external@gmail.com>: Relay access denied**

Any sugestion?? i need send mail from other server without any authentification.

I can filter the ip of this server beacouse it can send mails without smpt-auth (i have other postfix configured with Smpt-auth)

Thanks for all.

---

### Post by pdwerryhouse on 2008-05-20
Check that you have set inet_interfaces. Either:

inet_interfaces = all

or 

inet_interfaces = 192.9.200.27, 127.0.0.1

Cheers,

Paul.

---

### Post by klcom on 2008-05-20
this is my main.cf.............................

root@muga:/etc/postfix# vi main.cf
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

#myhostname = muga.cxg.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = domain.com, muga.cxg.local, localhost.cxg.local, , localhost
relayhost = 87.236.241.xxx
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =

---

### Post by MJN on 2008-05-20
If you want to allow a machine to relay mail without authenticating (although I must ask why not just get it to authenticate?) then you must add its IP address to your trusted networks list, i.e.
 
**mynetworks = 127.0.0.0/8, [::ffff:127.0.0.0]/104, [::1]/128, <address of the trusted machine>**
 
Mathew

---

### Post by klcom on 2008-05-20
Thank you very much!!

For your information that is for SAP, for send mails to providers, and not load the Lotus Domino Server, but SAP need a NO Autenticated-SMTP.

Thanks!:guitar:

---

