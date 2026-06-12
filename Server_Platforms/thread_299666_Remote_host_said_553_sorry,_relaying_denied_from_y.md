---
title: "Remote host said: 553 sorry, relaying denied from your location"
date: 2006-11-14
forum: Server Platforms
---

### Post by huggy77 on 2006-11-14
i recieve a ```
Remote host said: 553 sorry, relaying denied from your location
```  error when i sent email to an address hosted on my ubuntu box... 

my postconf is:

```

root@mars:/var/log# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
mailbox_size_limit = 0
mydestination = mars.aplocal.net, localhost, localhost.localdomain
myhostname = mars.aplocal.net
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_uid_maps = static:5000

```

thanks for the help in advance!

---

### Post by Child of Wonder on 2006-11-14
EDIT: Didn't read your entire post.  :)

Can you post the section of /var/log/mail.log that shows the mail being rejected?

---

### Post by MJN on 2006-11-14
What address are you trying to send to? <someone>@mars.aplocal.net?

Mathew

---

### Post by huggy77 on 2006-11-15
Guys - i am sorry about being so vague...


the address i was sending to is [email]chris@landmarkaerials.com[/email] - that is a virtual domain under my courier/postfix set up...  I can currently send email from one account to another if those accounts are located on my machine...    I also 

```

Nov 14 14:03:06 mars postfix/smtpd[6277]: connect from unknown[10.10.10.11]
Nov 14 14:03:06 mars postfix/smtpd[6277]: 49CF36543C9: client=unknown[10.10.10.11], sasl_method=LOGIN, sasl_username=chris@landmarkaerials.com
Nov 14 14:03:06 mars postfix/cleanup[6280]: 49CF36543C9: message-id=<C17F7D21.5F1%chris@landmarkaerials.com>
Nov 14 14:03:06 mars postfix/qmgr[4546]: 49CF36543C9: from=<chris@landmarkaerials.com>, size=637, nrcpt=1 (queue active)
Nov 14 14:03:07 mars postfix/smtp[6281]: 49CF36543C9: to=<chrisl@aerialphotosofnj.com>, relay=smtp.secureserver.net[64.202.166.12]:25, delay=1.2, delays=0.2/0.01/0.72/0.23, dsn=2.0.0, status=sent (250 ok 1163530995 qp 1971 by pre-smtp16-01.prod.mesa1.secureserver.net)
Nov 14 14:03:07 mars postfix/qmgr[4546]: 49CF36543C9: removed
Nov 14 14:03:10 mars postfix/smtpd[6277]: disconnect from unknown[10.10.10.11]
Nov 14 14:04:59 mars postfix/smtpd[6282]: connect from unknown[10.10.10.11]
Nov 14 14:04:59 mars postfix/smtpd[6282]: 149EF6543C9: client=unknown[10.10.10.11], sasl_method=LOGIN, sasl_username=chris@landmarkaerials.com
Nov 14 14:04:59 mars postfix/cleanup[6285]: 149EF6543C9: message-id=<C17F7D92.5F6%chris@landmarkaerials.com>
Nov 14 14:04:59 mars postfix/qmgr[4546]: 149EF6543C9: from=<chris@landmarkaerials.com>, size=1879, nrcpt=1 (queue active)
Nov 14 14:04:59 mars postfix/local[6286]: warning: required alias not found: mailer-daemon
Nov 14 14:04:59 mars postfix/local[6286]: 149EF6543C9: to=<MAILER-DAEMON@mars.aplocal.net>, relay=local, delay=0.21, delays=0.18/0.03/0/0, dsn=2.0.0, status=sent (discarded)
Nov 14 14:04:59 mars postfix/qmgr[4546]: 149EF6543C9: removed
Nov 14 14:05:01 mars postfix/smtpd[6282]: disconnect from unknown[10.10.10.11]
Nov 14 14:05:41 mars postfix/smtpd[6282]: connect from unknown[10.10.10.11]
Nov 14 14:05:41 mars postfix/smtpd[6282]: A76086543C9: client=unknown[10.10.10.11], sasl_method=LOGIN, sasl_username=map@aplocal.net
Nov 14 14:05:41 mars postfix/cleanup[6285]: A76086543C9: message-id=<C17F7DBD.5F7%map@aplocal.net>
Nov 14 14:05:41 mars postfix/qmgr[4546]: A76086543C9: from=<map@aplocal.net>, size=881, nrcpt=1 (queue active)
Nov 14 14:05:41 mars postfix/virtual[6287]: A76086543C9: to=<chris@landmarkaerials.com>, relay=virtual, delay=0.28, delays=0.2/0.01/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)
Nov 14 14:05:41 mars postfix/qmgr[4546]: A76086543C9: removed
Nov 14 14:05:46 mars postfix/smtpd[6282]: disconnect from unknown[10.10.10.11]

```

i really appreciate the help -

---

### Post by huggy77 on 2006-11-15
email bounce message is:
64.202.166.11 does not like recipient.
Remote host said: 553 sorry, relaying denied from your location [64.202.165.12] (#5.7.1)
Giving up on 64.202.166.11.

---

### Post by huggy77 on 2006-11-15
what logs should i be looking at btw?  mail.info?

---

### Post by MJN on 2006-11-15
mail.log will suffice (the other mail. files are subsets of this)

If you can post the relevent portion that should definitely help.

Mathew

---

### Post by Child of Wonder on 2006-11-16
Post the section of mail.log that gives the 553 error and all relevant sections dealing with where the mail was from, to, etc.

In fact, just do this:

grep "relaying denied" /var/log/mail.log

This will show you the message that's being rejected and it's designation (a bunch of letters and numbers).  Then grep for that.

grep 92DE0EEC1B /var/log/mail.log

Then post what those two greps return.

---

