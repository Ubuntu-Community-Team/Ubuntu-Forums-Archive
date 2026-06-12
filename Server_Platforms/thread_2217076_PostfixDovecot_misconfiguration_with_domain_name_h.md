---
title: "Postfix/Dovecot misconfiguration with domain name header?"
date: 2014-04-15
forum: Server Platforms
---

### Post by dudumomo on 2014-04-15
Hi guys,

I'm using Postfix, Dovecot and Roundcube but I may have a configuration problem with Postfix and Dovecot because if I want to log to Roundcube I need to type the username directly and cannot set the domain name. And in this case, when I send mail, it says they come from [email]user@sub.domain.com[/email]. But I'd like to display [email]user@domain.com[/email] instead.
(I know I can use Roundcube identities to do that, but I think it's a wrong solution as the issue might come from Postfix and Dovecot).

Do you have some ideas how to fix it?

Here is my postfix:
```

biff = no

myhostname = mail.fredif.org
mydomain = freedif.org
myorigin = /etc/mailname
mydestination = mail.freedif.org, freedif.org, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

smtpd_tls_cert_file=/etc/ssl/certs/freedif.pem
smtpd_tls_key_file=/etc/ssl/private/freedif.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_tls_security_level=may
smtpd_tls_protocols = !SSLv2, !SSLv3

smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_authenticated_header = yes

mailbox_command = /usr/bin/procmail -Y -a $DOMAIN
home_mailbox = Maildir/
content_filter = smtp-amavis:[127.0.0.1]:10024

```

And here is my dovecot:
```
log_path = /var/log/dovecot
disable_plaintext_auth = no
mail_privileged_group = mail
mail_location = maildir:~/Maildir
userdb {
  driver = passwd
}

passdb {
  driver = pam
}

protocols = imap

#protocol imap {
#  mail_plugins = " autocreate"
#}
#plugin {
#  autocreate = Trash
#  autocreate2 = Sent
#  autosubscribe = Trash
#  autosubscribe2 = Sent
#  autocreate3 = Junk
#  autosubscribe3 = Junk
#}

service auth {
  unix_listener /var/spool/postfix/private/auth {
    mode = 0660
        user=postfix
        group=postfix
  }
 }

ssl=required
ssl_cert = </etc/ssl/certs/freedif.pem
ssl_key = </etc/ssl/private/freedif.key
```

Thanks for your help!

---

