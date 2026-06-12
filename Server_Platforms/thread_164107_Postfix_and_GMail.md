---
title: "Postfix and GMail"
date: 2006-04-22
forum: Server Platforms
---

### Post by elminster13 on 2006-04-22
Hi all,

I hope someone can help me? I have looked through the forums and can't find the answer to my problem.

I would like to use gmail to relay all my mail but am having difficulties understanding the certificate system.

I have followed the tutorial at [http://souptonuts.sourceforge.net/postfix_tutorial.html](http://souptonuts.sourceforge.net/postfix_tutorial.html) tna.

Heres my problem; when i try to send mail using sendmail -bv [email]elminster13@gmail.com[/email] i get this error in my logs:

---------------------------------------------------------------------------------------------------------------------------------
[COLOR="Silver"]Apr 22 10:58:44 localhost postfix/pickup[8043]: C83371C2C6: uid=0 from=<root>
Apr 22 10:58:44 localhost postfix/cleanup[8048]: C83371C2C6: message-id=<20060422095844.C83371C2C6@trantor.duaneville.com>
Apr 22 10:58:44 localhost postfix/qmgr[8044]: C83371C2C6: from=<root@duaneville.com>, size=298, nrcpt=1 (queue active)
Apr 22 10:58:45 localhost postfix/smtp[8050]: setting up TLS connection to smtp.gmail.com
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL_connect:before/connect initialization
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL_connect:SSLv2/v3 write client hello A
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL_connect:error in SSLv2/v3 read server hello A
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL_connect:error in SSLv3 read server hello A
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL_connect:error in SSLv3 read server hello A
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL_connect:SSLv3 read server hello A
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL_connect:error in SSLv3 read server certificate A
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL_connect:error in SSLv3 read server certificate A
Apr 22 10:58:45 localhost postfix/smtp[8050]: certificate verification depth=0 subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
Apr 22 10:58:45 localhost postfix/smtp[8050]: certificate verification failed for smtp.gmail.com: num=20:unable to get local issuer certificate
Apr 22 10:58:45 localhost postfix/smtp[8050]: verify return: 0
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL3 alert write:fatal:unknown CA
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL_connect:error in SSLv3 read server certificate B
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL_connect error to smtp.gmail.com: -1
Apr 22 10:58:45 localhost postfix/smtp[8050]: warning: TLS library problem: 8050:error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate
verify failed:s3_clnt.c:894:
Apr 22 10:58:45 localhost postfix/smtp[8050]: SSL session removed
Apr 22 10:58:45 localhost postfix/smtp[8050]: C83371C2C6: to=<elminster@gmail.com>, relay=smtp.gmail.com[72.14.205.109], delay=1, status=undeliverable (delivery via smtp.gmail.com[72.14.205.109]: Cannot start TLS: handshake failure)
Apr 22 10:58:45 localhost postfix/cleanup[8048]: 785591C2C1: message-id=<20060422095845.785591C2C1@trantor.duaneville.com>
Apr 22 10:58:45 localhost postfix/qmgr[8044]: C83371C2C6: removed
Apr 22 10:58:45 localhost postfix/qmgr[8044]: 785591C2C1: from=<>, size=1854, nrcpt=1 (queue active)
Apr 22 10:58:45 localhost postfix/local[8053]: 785591C2C1: to=<elminster@duaneville.com>, orig_to=<root@duaneville.com>, relay=local, delay=0, status=sent (delivered to command: procmail -a "$EXTENSION")
Apr 22 10:58:45 localhost postfix/qmgr[8044]: 785591C2C1: removed[/COLOR]
 ---------------------------------------------------------------------------------------------------------------------------------

Now I have created my certificates as per the tutorial, and here is my postfix configuration:

-----------------------------------------------------------------------------------------------------------------------------------
[COLOR="Silver"]alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
disable_dns_lookups = yes
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = localhost.localdomain, localhost.localdomain, localhost, duaneville.com, duaneville.co.uk
myhostname = trantor.duaneville.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = [smtp.gmail.com]
smtp_generic_maps = hash:/etc/postfix/generic
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_loglevel = 2
smtp_tls_per_site = hash:/etc/postfix/tls_per_site
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_sasl_application_name = smtpd
smtpd_sasl_auth_enable = no
smtpd_sasl_local_domain = $myhostname
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
smtpd_tls_key_file = /etc/postfix/FOO-key.pem
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
transport_maps = hash:/etc/postfix/transport[/COLOR]
---------------------------------------------------------------------------------------------------------------------------------
the setup i have is this, i have a webserver running on my linux pc, and i use dyndns.org to point my domain duaneville.com to my home pc. I would like to send mail from my home via gmail.

Any help that you can offer would be appreciated.

---

### Post by MJN on 2006-04-22
Might the following be of any use? ;)

[Gmail on Home Linux Box using Postfix and Fetchmail]("http://souptonuts.sourceforge.net/postfix_tutorial.html")

Incidentally, the error is down to Postfix not being able to verify Gmail's certificate hence it fails to establish a TLS session - this isn't down to **your** certificates though.

Mathew

---

### Post by elminster13 on 2006-04-23
Hi,

Thanks for the reply but thats the tutorial i followed. <see start of my post>, so the question is why can't i verify gmails certificate.

This is helpful becuase i have recreated my certificates a number of times, i can stop that now.

Any ideas?

---

### Post by MJN on 2006-04-23
Ah yes - sorry I missed that bit (and here's me thinking I'd stumbled across a pot of gold for you! ;))

I'm afraid I'll have to leave it to someone else as whilst I use TLS on my server this is only for incoming connections (using its own certificate) and so don't have experience of getting it to successfully check someone elses certs.

Have you done a Google search? Searching for 'postfix unable to get local issuer certificate' seems to throw up a fair bit..?

Mathew

---

### Post by elminster13 on 2006-04-23
I changed my tls_per_sire file to 

smtp.gmail.com         MAY

and that solved my problem, but clearly at the expense of security. does anyone know how to verify the certificate.

---

### Post by MJN on 2006-04-23
Do you have genuine concerns that smtp.gmail.com might be spoofed, particularly by a spoofed DNS entry somewhere along the way? If not, I wouldn't be overly concerned - your username and password are at least being encrypted (assuming a TLS session stills gets established, albeit with a non-verified certificate from gmail).

Mathew

---

### Post by elminster13 on 2006-04-26
Your right of course, for home use the question is now irrelevent. However there is still the question of why the certificate is being rejected and understanding the underlying process. But thats a reading need of mine.

---

### Post by MJN on 2006-04-26
I know what you mean - required or not sometimes it's nice to know why something doesn't work!

---

