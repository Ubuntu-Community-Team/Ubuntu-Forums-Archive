---
title: "Postfix Fatal: pipe_command"
date: 2007-06-21
forum: Server Platforms
---

### Post by dmeyer on 2007-06-21
I have an Edgy server located in my DMZ that is intended to run Postfix+spamc+spamassassin+postgrey+amavis and forward all mail through my ISA server to Exchange 2007 for delivery.  I've set up postfix, spamassassin and spamd, but no mail is being forwarded to the next server.  

In /var/log/mail.err I get errors that look like:

[INDENT]Jun 20 23:36:12 localhost postfix/smtp[29919]: fatal: valid hostname or network address required in server description: <192.168.2.2>
Jun 20 23:36:12 localhost pipe[29924]: fatal: pipe_command: execvp : No such file or directory [/INDENT]


In /var/log/mail.log I get errors that look like:

[INDENT]Jun 21 14:30:49 localhost postfix/pipe[28654]: 5DDDE25C16D: to=< [email]rick@jakked.net[/email]>, relay=spamassassin, delay=0.06, delays=0.03/0/0/0.03, dsn=4.3.0, status=deferred (temporary failure. Command output: pipe: fatal: pipe_command: execvp : No such file or directory )[/INDENT]

My main.cf looks like:

[INDENT]# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default 
# is /etc/mailname.
myorigin = /etc/mailname #this was commented out

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no 

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl- cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for 
# information on enabling SSL in the smtp client.

# forward all mail through ISA server
transport_maps = hash:/etc/postfix/transport

myhostname = mail.jakked.net
# alias_maps = hash:/etc/aliases  # commented this
# alias_database = hash:/etc/aliases # commented this
myorigin = /etc/mailname
# mydestination = localhost, localhost.localdomain, localhost
# mynetworks = 127.0.0.0/8, 192.168.2.0/24, 192.168.1.0/24
relay_domains = [jakked.net]
# relayhost = [ 192.168.2.2]

mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
[/INDENT]

and my Master.cf looks like:

[INDENT]
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args 
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
    -o content_filter=spamassassin 
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_enforce_tls=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#smtps     inet  n       -       -       -       -       smtpd 
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup 
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr 
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce 
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp 
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
    -o fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5 
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local 
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache      unix    -    -    -    -    1    scache 
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants. 
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ==================================================================== 
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe 
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient) 
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe 
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension} 
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
spamassassin unix -    n    n    -    -    pipe 
    user=spamd argv= /usr/bin/spamc -f -e 
    /usr/sbin/sendmail -oi -f${sender} ${recipient}

[/INDENT]

I'm really not sure what the problem is at this point.  I know its closer to working that it was before, but still nothing is getting through.

I would really appreciate any help that you could give,

-Dustin

---

### Post by Mr. C. on 2007-06-21
You've shown your main.cf twice.

Please show "master.cf".

MrC

---

### Post by dmeyer on 2007-06-22
> **Mr. C. said:**
> You've shown your main.cf twice.

Please show "master.cf".

MrC

Done.  Thanks!

---

### Post by Mr. C. on 2007-06-22
Remove the space between the option and value from

```
argv= /usr/bin/spamc
```

and restart postfix.

MrC

---

