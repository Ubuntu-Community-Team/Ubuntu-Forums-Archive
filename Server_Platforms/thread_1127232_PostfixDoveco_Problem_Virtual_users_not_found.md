---
title: "Postfix/Doveco Problem: Virtual users not found"
date: 2009-04-16
forum: Server Platforms
---

### Post by th3_b0b on 2009-04-16
Hi!

I'm trying to configure postfix and dovecot to use virtual users.
I followed [this]("http://http://wiki.dovecot.org/HowTo/SimpleVirtualInstall") HOWTO and read (I think) every singe article on that wiki, but I'm stuck with this problem:

Postfix rejects all mail to the virtual domain stating:
```
postfix/pipe[11884]: 5B2A1D4097A: to=<test@my.domain.here>, relay=dovecot, delay=0.1, delays=0.09/0/0/0.01, dsn=5.1.1, status=bounced (user unknown) 
``` 

My configurations are as follows:
( Ubuntu 8.04 Server )

### dovecot -n ###
```
# 1.0.10: /etc/dovecot/dovecot.conf
log_timestamp: %Y-%m-%d %H:%M:%S
protocols: imaps
ssl_cert_file: /etc/ssl/dovecot.pem
ssl_key_file: /etc/ssl/dovecot.pem
login_dir: /var/run/dovecot/login
login_executable: /usr/lib/dovecot/imap-login
mail_privileged_group: mail
mail_location: maildir:~/Maildir
auth default:
  passdb:
    driver: passwd-file
    args: /etc/dovecot/vmail.passwd
  passdb:
    driver: pam
  userdb:
    driver: passwd-file
    args: /etc/dovecot/vmail.passwd
  userdb:
    driver: passwd
  socket:
    type: listen
    client:
      path: /var/spool/postfix/private/auth
      mode: 432
      user: postfix
      group: postfix
    master:
      path: /var/run/dovecot/auth-master
      mode: 438
      user: vmail
      group: vmail
```

### /etc/dovecot/vmail.passwd ###
```
test:{PLAIN}testfoobar:1002:1002::/home/vmail/test::
```

### postconf -n ###
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
local_recipient_maps =
mailbox_command = /usr/lib/dovecot/deliver
mailbox_size_limit = 0
mydestination = hXXXXXXXX.stratoserver.net, localhost
myhostname = hXXXXXXXX.stratoserver.net
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_auth_destination, permit_sasl_authenticated, permit_mynetworks, reject
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/ssl/postfix.pem
smtpd_tls_key_file = $smtpd_tls_cert_file
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_maps = hash:/etc/postfix/virtual_adresses
virtual_mailbox_domains = my.domain.com
virtual_transport = dovecot
```

### /etc/postfix/virtual_adresses ###
```
test@exposition-in.eu test
```

### /etc/postfix/master.cf (Stripped off all comments) ###
```
smtp      inet  n       -       -       -       -       smtpd
  -o smtpd_tls_security_level=may
  -o smtpd_sasl_auth_enable=yes
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
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
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
dovecot   unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail:vmail argv=/usr/lib/dovecot/deliver -f ${sender} -d ${recipient}
```

Hope that is enough info...
Bye!
Bob

---

### Post by randomstuff on 2009-04-17
Maybe this guide can help you?

[http://www.postfix.org/VIRTUAL_README.html#virtual_mailbox]("http://www.postfix.org/VIRTUAL_README.html#virtual_mailbox")

Personally I am using [virtual alias]("http://www.postfix.org/VIRTUAL_README.html#virtual_aliases") instead so I wouldnt know how to fix your problem.

---

