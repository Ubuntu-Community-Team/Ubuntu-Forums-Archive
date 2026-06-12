---
title: "TLS library problem, postfix"
date: 2009-11-25
forum: Server Platforms
---

### Post by Zer0d on 2009-11-25
I am not able to send emails out to external domains through Evolution, haven't tested other programs but it looks sever related and not client.

I am able to receive mails from external hosts like gmail, hotmail and so on but I can't send to them.

I have followed these guides:
[https://help.ubuntu.com/9.10/serverguide/C/postfix.html](https://help.ubuntu.com/9.10/serverguide/C/postfix.html)
[http://www.howtoforge.com/forums/showthread.php?t=2](http://www.howtoforge.com/forums/showthread.php?t=2)
[https://help.ubuntu.com/9.10/serverguide/C/certificates-and-security.html#certificate-authority](https://help.ubuntu.com/9.10/serverguide/C/certificates-and-security.html#certificate-authority)

**main.cf**
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
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.jeant.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = /etc/postfix/local-host-names
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 3
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
mailbox_command = 
virtual_maps = hash:/etc/postfix/virtusertable

```

**mail.warn**
```

Nov 25 21:03:06 slashroot-server postfix/smtpd[13420]: warning: 85.165.149.130: address not listed for hostname dsldevice.lan
Nov 25 21:06:57 slashroot-server postfix/smtpd[13564]: warning: 85.165.149.130: address not listed for hostname dsldevice.lan

```

**local-host-names**
```

jeant.com
www.jeant.com
mail.jeant.com

```

**master.cf**
```

#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
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
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
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
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```

---

### Post by Zer0d on 2009-11-25
In Evolution I get this message when I choose TLS as encryption:
RCPT TO <mail@domain.com> failed: <mail@domain.com>: Relay access denied. I get same message if I choose no encryption.

If I choose SSL as encryption it keeps sending forever and then:
Could not connect to mail.jeant.com: Connection timed out

---

### Post by Zer0d on 2009-11-26
Nobody has tips or anything I could check out? The whole problem is about sending to server outside my network like gmail, google and so on.

---

### Post by jmes on 2011-11-18
> **Zer0d said:**
> Nobody has tips or anything I could check out? The whole problem is about sending to server outside my network like gmail, google and so on.
 
 
I know this message is 2 years old, you most likely have figured it out by now.
 
You have to use alternate sendmail port or setup sasl_passwd with postfix and use your ISP as a relay through port 25 using an email account from your ISP you create.
Most Internet Service Providers block sending to anyone on port 25 except them.
 
Add the following settings to /etc/postfix/main.cf:
```
 
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =

```
 
Create /etc/postfix/sasl_passwd as follows:
```
 
my.mail.relay.net username:password

```
 
Because the password is in cleartext make it root only:
```
 
chown root:root /etc/postfix/sasl_passwd && chmod 600 /etc/postfix/sasl_passwd

```
 
Create the hash file:
```
 
postmap /etc/postfix/sasl_passwd

```
 
Make the hash file world readable:
```
 
chmod 644 /etc/postfix/sasl_passwd

```
  
Reload the Postfix config:
```
 
/etc/init.d/postfix reload

```

---

