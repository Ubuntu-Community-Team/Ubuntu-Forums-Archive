---
title: "Postfix - help smtps port 465"
date: 2013-02-19
forum: Server Platforms
---

### Post by babaton on 2013-02-19
Hello,

I've just setup my first postfix server on ubuntu 8.04. I have a web applications that'll be sending mail through it, the web app seems to only send using ssl or tls.

So, I've edited the master.cf file and postfix is open on 465. I can telnet into postfix and send ok from the box the app is running on.The web apps ip address is in the MyNetworks list in main.cf.

However when I run the app and try to send I get the following in maillog :

```
Feb 18 17:48:10 green postfix/smtpd[31483]: connect from unknown[192.168.1.80]
Feb 18 17:48:10 green postfix/smtpd[31483]: lost connection after UNKNOWN from unknown[192.168.1.80]
Feb 18 17:48:10 green postfix/smtpd[31483]: disconnect from unknown[192.168.1.80]
Feb 18 17:48:10 green postfix/smtpd[31483]: connect from unknown[192.168.1.80]
Feb 18 17:48:10 green postfix/smtpd[31483]: lost connection after UNKNOWN from unknown[192.168.1.80]
Feb 18 17:48:10 green postfix/smtpd[31483]: disconnect from unknown[192.168.1.80]
Feb 18 17:48:10 green postfix/smtpd[31483]: connect from unknown[192.168.1.80]
Feb 18 17:48:10 green postfix/smtpd[31483]: lost connection after UNKNOWN from unknown[192.168.1.80]

```
My guess is that the app isn't adhering to smtp and the connection is being dropped.

Are there any other log files where I can see the smtp exchange between the server and app?
I noticed that when I telnet in on port 465 I don't need to authenticate, I haven't setup and certificates either so perhaps I haven't setup smtps correctly in the first place. I'm surprised I can send at all tbh.

here's my main.cf :
```
See /usr/share/postfix/main.cf.dist for a commented, more complete version
Debian specific: Specifying a file name will cause the first
line of that file to be used as the name. The Debian default
is /etc/mailname.
myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
appending .domain is the MUA's job.

append_dot_mydomain = no
Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

readme_directory = no
TLS parameters

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
information on enabling SSL in the smtp client.

myhostname = green
mydomain = mail.hgluk.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = green, localhost.localdomain, localhost
mynetworks = 192.168.1.99,192.168.1.80
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +

and my master.cf :
Postfix master process configuration file. For details on the format
of the file, see the master(5) manual page (command: "man 5 master").
Do not forget to execute "postfix reload" after editing this file.
==========================================================================
service type private unpriv chroot wakeup maxproc command + args
(yes) (yes) (yes) (never) (100)
==========================================================================
smtp inet n - - - - smtpd
submission inet n - - - - smtpd
-o smtpd_tls_security_level=encrypt
-o smtpd_sasl_auth_enable=yes
-o smtpd_client_restrictions=permit_sasl_authenticated,reject
-o milter_macro_daemon_name=ORIGINATING

smtps inet n - - - - smtpd
-o smtpd_tls_wrappermode=yes
-o smtpd_sasl_auth_enable=yes
-o smtpd_client_restrictions=permit_sasl_authenticated,reject
-o milter_macro_daemon_name=ORIGINATING
628 inet n - - - - qmqpd

pickup fifo n - - 60 1 pickup
cleanup unix n - - - 0 cleanup
qmgr fifo n - n 300 1 qmgr
qmgr fifo n - - 300 1 oqmgr

tlsmgr unix - - - 1000? 1 tlsmgr
rewrite unix - - - - - trivial-rewrite
bounce unix - - - - 0 bounce
defer unix - - - - 0 bounce
trace unix - - - - 0 bounce
verify unix - - - - 1 verify
flush unix n - - 1000? 0 flush
proxymap unix - - n - - proxymap
proxywrite unix - - n - 1 proxymap
smtp unix - - - - - smtp
When relaying mail as backup MX, disable fallback_relay to avoid MX loops

relay unix - - - - - smtp
-o smtp_fallback_relay=
-o smtp_helo_timeout=5 -o smtp_connect_timeout=5

showq unix n - - - - showq
error unix - - - - - error
retry unix - - - - - error
discard unix - - - - - discard
local unix - n n - - local
virtual unix - n n - - virtual
lmtp unix - - - - - lmtp
anvil unix - - - - 1 anvil
scache unix - - - - 1 scache
====================================================================
Interfaces to non-Postfix software. Be sure to examine the manual
pages of the non-Postfix software to find out what options it wants.
Many of the following services use the Postfix pipe(8) delivery
agent. See the pipe(8) man page for information about ${recipient}
and other message envelope options.
====================================================================
maildrop. See the Postfix MAILDROP_README file for details.
Also specify in main.cf: maildrop_destination_recipient_limit=1

maildrop unix - n n - - pipe
flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
See the Postfix UUCP_README file for configuration details.

uucp unix - n n - - pipe
flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
Other external delivery methods.

ifmail unix - n n - - pipe
flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp unix - n n - - pipe
flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix - n n - 2 pipe
flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman unix - n n - - pipe
flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
${nexthop} ${user}
```

---

### Post by lisati on 2013-02-19
*Thread moved to **Server Platforms**.*

---

### Post by lisati on 2013-02-19
8.04 is an older version of Ubuntu, available support may be limited.

Is that an exact copy of your main.cf? The first few lines look as if they should be comments.

---

### Post by babaton on 2013-02-19
....it looks like I've managed to lose the hash tags when copy/pasting.....

Here's the main.cf....

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

myhostname = green
mydomain = mail.hgluk.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = green, localhost.localdomain, localhost
mynetworks = 192.168.1.99,192.168.1.80
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
```

---

