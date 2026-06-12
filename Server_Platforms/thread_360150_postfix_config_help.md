---
title: "postfix config help"
date: 2007-02-12
forum: Server Platforms
---

### Post by bspratt on 2007-02-12
setup postfix & courier & fetchmail on Edgy. Fetchmail works fine. However I cannot send myself email from outside my LAN - The only bounce back I might see is "could not be delivered; will try again"; Possibly something wrong with the config file below ? Do I need a host type file for DNS issues?  Thanks - Bill  By the way, I have to SMTP thru my ISP...

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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = mydomain.com
mydestination = mydomain.com, ubuntu-server61, localhost.localdomain, localhost
relayhost = smtp-server.tampabay.rr.com
mynetworks = 127.0.0.0/8 192.168.10.0/24
mailbox_size_limit = 25600000
recipient_delimiter = +
home_mailbox = Maildir/

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_received_header = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =

---

### Post by kidders on 2007-02-12
Hi there,

Thanks for posting your main.cf ... it *seems* fairly reasonable. :-) You should find much more detail on the nature of your problem in your mail logs though. They're likely to tell you exactly what's going wrong.

If I were you, I would try something like this...

[LIST=1]
[*]Open a terminal window and type **tail -n 0 -f /var/log/mail.log**
[*]Try to send yourself a mail from an external IP again.
[*]Watch the terminal window for any interesting diagnostic output.
[/LIST]

It would be a great help if you could post the output.

---

### Post by bspratt on 2007-02-12
thanks for the quick reply - your log suggestion was just what I was hoping for. It may take me a while to get the MX changed again but I will post back the results - thanks!

---

### Post by dcstar on 2007-02-12
> **bspratt said:**
> thanks for the quick reply - your log suggestion was just what I was hoping for. It may take me a while to get the MX changed again but I will post back the results - thanks!

Incoming mail must be addressed to a valid Internet host - unless your Ubuntu box is configured to be that host then it isn't going to accept e-mail for it.

The easiest way to test is to Telnet into port 25 and manually send a message using the full Internet address "RCPT TO" name.

---

### Post by bspratt on 2007-02-13
Ok, here are log results:

Feb 13 05:06:07 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 05:06:07 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 05:06:07 ubuntu-server61 courierpop3login: LOGOUT, user=bspratt, ip=[::ffff:192.168.10.2], top=0, re
tr=0, rcvd=12, sent=39, time=0
Feb 13 05:36:07 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 05:36:07 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 05:36:07 ubuntu-server61 courierpop3login: LOGOUT, user=bspratt, ip=[::ffff:192.168.10.2], top=0, re
tr=0, rcvd=12, sent=39, time=0
Feb 13 06:06:07 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 06:06:07 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 06:06:07 ubuntu-server61 courierpop3login: LOGOUT, user=bspratt, ip=[::ffff:192.168.10.2], top=0, re
tr=0, rcvd=12, sent=39, time=0
Feb 13 06:36:07 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 06:36:07 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 06:36:07 ubuntu-server61 courierpop3login: LOGOUT, user=bspratt, ip=[::ffff:192.168.10.2], top=0, re
tr=0, rcvd=12, sent=39, time=0
Feb 13 06:54:36 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 06:54:36 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 06:54:36 ubuntu-server61 courierpop3login: LOGOUT, user=bspratt, ip=[::ffff:192.168.10.2], top=0, re
tr=0, rcvd=12, sent=39, time=0
Feb 13 06:54:38 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 06:54:38 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 06:54:38 ubuntu-server61 courierpop3login: LOGOUT, user=bspratt, ip=[::ffff:192.168.10.2], top=0, re
tr=0, rcvd=12, sent=39, time=0
Feb 13 04:36:07 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 04:36:07 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 04:36:07 ubuntu-server61 courierpop3login: LOGOUT, user=bspratt, ip=[::ffff:192.168.10.2], top=0, re
tr=0, rcvd=12, sent=39, time=0
Feb 13 05:06:07 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 05:06:07 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 05:06:07 ubuntu-server61 courierpop3login: LOGOUT, user=bspratt, ip=[::ffff:192.168.10.2], top=0, re
tr=0, rcvd=12, sent=39, time=0
Feb 13 05:36:07 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 05:36:07 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 05:36:07 ubuntu-server61 courierpop3login: LOGOUT, user=bspratt, ip=[::ffff:192.168.10.2], top=0, re
tr=0, rcvd=12, sent=39, time=0
Feb 13 06:06:07 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 06:06:07 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 07:03:44 ubuntu-server61 postfix/smtpd[13914]: connect from localhost[127.0.0.1]
Feb 13 07:03:44 ubuntu-server61 postfix/smtpd[13914]: 1A2BEEE220: client=localhost[127.0.0.1]
Feb 13 07:03:44 ubuntu-server61 postfix/cleanup[13918]: 1A2BEEE220: message-id=<344979.83431.qm@web30502.mail.mud.yahoo.com>
Feb 13 07:03:44 ubuntu-server61 postfix/qmgr[12128]: 1A2BEEE220: from=<bspratt@yahoo.com>, size=2905, nrcpt=1 (queue active)
Feb 13 07:03:44 ubuntu-server61 postfix/local[13919]: 1A2BEEE220: to=<bspratt@localhost>, relay=local, delay=0.1, delays=0.07/0.02/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)
Feb 13 07:03:44 ubuntu-server61 postfix/qmgr[12128]: 1A2BEEE220: removed
Feb 13 07:03:44 ubuntu-server61 postfix/smtpd[13914]: disconnect from localhost[127.0.0.1]
Feb 13 07:03:52 ubuntu-server61 courierpop3login: Connection, ip=[::ffff:192.168.10.2]
Feb 13 07:03:52 ubuntu-server61 courierpop3login: LOGIN, user=bspratt, ip=[::ffff:192.168.10.2]
Feb 13 07:03:52 ubuntu-server61 courierpop3login: LOGOUT, user=bspratt, ip=[::ffff:192.168.10.2], top=0, retr=2945, rcvd=34, sent=3154, time=0

From this, it appears all thats happening is my pop3 client is periodically checking? Then at 7:03 Fetchmail did its thing and retrieved 1 email. I still do not know why my email does not find the server - it could be the FQD name or perhaps DNS? It did pass one Telnet test but perhaps I need to do some more. Thanks - Bill

---

### Post by bspratt on 2007-02-13
yep. That was embarassing.  Once I unlocked port 25 on my firewall, the floodgates opened.  Now I just need to get greylist, clamav and spam assassin to do their thing! 
Bill

---

### Post by bspratt on 2007-02-13
Anyone know why when starting postgrey, I get the following?
root@ubuntu-server61:/etc/default# postgrey start
ERROR: --unix or --inet must be specified
probably something simple?

---

### Post by MJN on 2007-02-14
You should be starting it with the init script i.e. **/etc/init.d/postgrey start**
 
Attempting to start it directly is failing as there are numerous command options that need specifying.
 
Mathew

---

### Post by bspratt on 2007-02-14
Thanks! Finally I'm trying to get my scanner (Procmail) configured correctly so that I can use Spamassassin. Does anyone know how to configure the /etc/procmailrc correctly for this? When I tried with:
DROPPRIVS=yes
:0fw
| /software/spamassassin/bin/spamc -s 256000
it bounced saying can't create user output file; also error while writing to /home//MailDir - lock failure.  The double slash doesn't look correct - any idea where I need to correct this?
Thanks - Bill

---

