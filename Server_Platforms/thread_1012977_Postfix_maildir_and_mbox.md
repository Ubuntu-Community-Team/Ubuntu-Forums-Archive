---
title: "Postfix maildir and mbox"
date: 2008-12-16
forum: Server Platforms
---

### Post by ilababy on 2008-12-16
I have ubuntu 8.04 server with fetchmail, procmail, dovecot and postfix for mail server.
It's configured for maildir and is ok, but i want read (from client with evolution) also mail from cron.
This mail is in /var/spool/mail/"user" in mbox format.
How can read the mail in maildir and mbox format?
Thanks.

---

### Post by MJN on 2008-12-16
If you've set Postfix to store mail in your users' directories in maildir format then that's where your cron mail will be also.

Mathew

---

### Post by ilababy on 2008-12-18
Thanks, but the mail cron is in /var/spool/mail/"user" and not in users' directories.
I set procmail for mail directory. How must set postfix?

---

### Post by MJN on 2008-12-18
> **ilababy said:**
> I set procmail for mail directory.What do you mean by that? Post your config.

> How must set postfix?It depends on whether you've configured it to use procmail for final delivery. Post your config.

(Do you see a theme appearing here? Config (and logs) are everything to solving most problems! ;-))

Mathew

---

### Post by ilababy on 2008-12-18
.procmailrc

:0
* ^To:.*info@example\.it
/home/"user"/mail/

:0
* ^To:.*amministrazione@example\.it
/home/"user"/mail/


main.cf

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

myhostname = server
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = example.it, server, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = mail/

```

Thanks.

---

### Post by MJN on 2008-12-18
> **ilababy said:**
> .procmailrcSorry, I meant your global Procmail configuration (/etc/procmailrc)

If you don't have one then there's your problem. We can sort that out if need be.

> main.cf

[...]Okay, that's good. It's just looking like your Procmail that needs fixing (depending on the contents of your global procmailrc config).

Mathew

---

### Post by ilababy on 2008-12-19
I don't have /etc/procmailrc file.
This is the problem?
Can I copy ~.procmailrc file or must be different?
Thanks.

---

### Post by MJN on 2008-12-19
In your case you need a generic one. Try the following:

```
DROPPRIVS=YES
ORGMAIL=$HOME/mail/
DEFAULT=$ORGMAIL
```

You can then get rid your .procmailrc as the above will cover it.

Mathew

---

### Post by ilababy on 2008-12-20
It's all right.
Thank you very much.

---

