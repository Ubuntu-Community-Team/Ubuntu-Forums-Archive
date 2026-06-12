---
title: "Postfix mail loops back to myself"
date: 2009-05-11
forum: Server Platforms
---

### Post by adaniels on 2009-05-11
Hi readers,

I'm having an issue and hope there is a mighty brain that help me out. I'm re-configuring the postfix configuration. Unfortunately I'm getting the famous message "mail for betamail.mx.p-client.net loops back to myself". I've read the main reasons of this message in the posfix docs and on several forums and double checked the configuration to make sure I don't have those issues.

```

May 12 01:42:54 betamail postfix/smtp[25818]: C258A70805C: to=<arnold@adaniels.nl>, relay=none, delay=8.8, delays=8.7/0.01/0/0, dsn=5.4.6, status=bounced (mail for betamail.mx.p-client.net loops back to myself)

```

Part of the configuration on betamail.mx.p-client.net:
```

myhostname = betamail.mx.p-client.net
mydestination = 
inet_interfaces = $myhostname
content_filter = smtp-amavis

virtual_mailbox_base = /var/vmail
virtual_alias_domains =
virtual_alias_maps = mysql:/etc/postfix/mysql/forwardings.cf mysql:/etc/postfix/mysql/email2email.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql/domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql/mailboxes.cf

```

```

root@betamail:~# postalias -q "arnold@adaniels.nl" mysql:/etc/postfix/mysql/email2email.cf 
arnold@adaniels.nl
root@betamail:~# postmap -q "adaniels.nl" mysql:/etc/postfix/mysql/domains.cf 
adaniels.nl
root@betamail:~# postmap -q "arnold@adaniels.nl" mysql:/etc/postfix/mysql/mailboxes.cf 
arnold@adaniels.nl/
root@betamail:~# host adaniels.nl
adaniels.nl has address 82.94.236.135
adaniels.nl mail is handled by 1000 mailtrap.mx.p-client.net.
adaniels.nl mail is handled by 20 alien.mx.p-client.net.
adaniels.nl mail is handled by 10 betamail.mx.p-client.net.

```

The postmap and host results are as expected.

Can anybody tell me what I'm doing wrong here? It would be very much appreciated.

Thanks,
Arnold

---

### Post by adaniels on 2009-05-11
When the content_filter is disabled, the issue does not occur.

From master.cf:
```

smtp-amavis unix -      -       n       -       100      smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
    -o disable_dns_lookups=yes
    -o max_use=50

127.0.0.1:10025 inet n  -       n       -       -  smtpd
    -o content_filter=
    -o smtpd_restriction_classes=
    -o smtpd_delay_reject=no
    -o smtpd_client_restrictions=permit_mynetworks,reject
    -o smtpd_helo_restrictions=
    -o smtpd_sender_restrictions=
    -o smtpd_recipient_restrictions=permit_mynetworks,reject
    -o smtpd_data_restrictions=reject_unauth_pipelining
    -o smtpd_end_of_data_restrictions=
    -o mynetworks=127.0.0.1
    -o smtpd_error_sleep_time=0
    -o smtpd_soft_error_limit=1001
    -o smtpd_hard_error_limit=1000
    -o smtpd_client_connection_count_limit=0
    -o smtpd_client_connection_rate_limit=0 
    -o smtpd_milters=
    -o local_header_rewrite_clients=
    -o local_recipient_maps=
    -o relay_recipient_maps=
    -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

```

---

### Post by adaniels on 2009-05-11
I need to do "content_filter = smtp-amavis:[127.0.0.1]:10024" of-course. 

Thanks for reading this

---

