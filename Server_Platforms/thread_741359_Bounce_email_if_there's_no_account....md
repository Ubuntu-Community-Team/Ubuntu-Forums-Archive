---
title: "Bounce email if there's no account..."
date: 2008-03-31
forum: Server Platforms
---

### Post by 3D Peruna on 2008-03-31
System: Edgy w/ ISPConfig, multiple domains.

ISPConfig has a setting for a "catchall" email account. Currently, I have a user called "catchall" that receives all of this email, which is emptied periodically.

I've looked all over and can't figure out the way to bounce emails coming to the system if there isn't an address.  Example:

These all all valid accounts:
[INDENT]bob@domain.com
[email]sue@domain.com[/email]
[email]jane@domain.com[/email][/INDENT]

but if mail arrives to [email]foo@domain.com[/email], I want it to bounce back--and do nothing with it.

---

### Post by Mr. C. on 2008-04-01
Which mail server - Postfix or Sendmail?

You don't want to accept mail then bounce it - you want to reject mail for unlisted recipients.

---

### Post by FakeOutdoorsman on 2008-04-01
Bouncing back messages is a bad idea. Spammers always spoof the from address and when a mail server bounces spam back to the spoofed sender it gets sent to an innocent non-spammer.  It is better to reject mail at the SMTP level.  Most end users won't be able to tell the difference, but there is no spam backscatter.

[Postfix Backscatter Howto]("http://www.postfix.org/BACKSCATTER_README.html")
[Mail Server Best Practices]("http://wiki.mailscanner.info/doku.php?id=best_practices")
[Why you shouldn't bounce spam and viruses]("http://www.dontbouncespam.org/")

---

### Post by 3D Peruna on 2008-04-01
Postfix

---

### Post by Mr. C. on 2008-04-01
Show output of :

```
postconf -n 

```

---

### Post by 3D Peruna on 2008-04-01
[INDENT]alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_at_myorigin = no
append_dot_mydomain = no
biff = no
bounce_template_file = /etc/postfix/bounce.cf
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
local_destination_concurrency_limit = 4
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 30000000
message_size_limit = 10240000
mydestination = /etc/postfix/local-host-names
mydomain = domain.com [COLOR="Red"]-- CHANGED[/COLOR]
myhostname = domain.com [COLOR="Red"]-- CHANGED[/COLOR]
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450
[/INDENT]

---

### Post by Mr. C. on 2008-04-01
Your config suggests that postfix rejects email from unknown recipients.

Currently, you are soft rejecting:

```
unknown_local_recipient_reject_code = 450
```

and should make that a 550 as soon as you have things working correctly.

You are also only considering the loopback network as part of "mynetworks".  Do you have other clients on the LAN that will be using this system as a mail server ?  If so, add those your network address to mynetworks.  Eg:
```

mynetworks = 127.0.0.0/8, 192.168.0.0/24
```

Your log messages should show you rejects to unknown users in the form of:

> ...postfix/smtpd[554]: NOQUEUE: reject: RCPT from example.com[10.0.0.1]: 550 5.1.1 <bogus@sample.net>: Recipient address rejected: User unknown in local recipient table; from=<friend@example.com> to=<bogus@sample.net> proto=SMTP helo=<example.com>

---

