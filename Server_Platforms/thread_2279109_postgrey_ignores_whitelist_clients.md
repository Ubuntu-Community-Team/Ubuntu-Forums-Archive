---
title: "postgrey ignores whitelist_clients"
date: 2015-05-21
forum: Server Platforms
---

### Post by Mona on 2015-05-21
I just installed "Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + Roundcube + Postgrey" following the instructions on [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/). Except for postgrey everything is working fine.

Postgrey graylists everybody discarding the given whitelists.

As far as I understood postgrey automatically "loads" the files
/etc/postgrey/whitelist_clients
/etc/postgrey/whitelist_recipients

but i also tried by adding "--whitelist-clients=/etc/postgrey/whitelist_clients" to /etc/default/postgrey.

Postgrey ignores the entries and still greylists everbody:

```
/etc/postgrey/whitelist_clients:
(...)
debian.org
(...)

```

```

telnet localdomain 25:
220 /etc/mailname ESMTP Postfix
helo debian.org
250 test.localdomain
MAIL FROM:test@debian.org
250 2.1.0 Ok
RCPT TO:test@example.org
450 4.2.0 <test@example.org>: Recipient address rejected: Greylisted, see http://post
grey.schweikert.ch/help/slums.de.html

```

```

tail -f /var/log/mail.log:
May 21 07:22:45 test postfix/smtpd[2759]: connect from unknown[93.91.234.150]
May 21 07:23:05 test postgrey[1492]: action=greylist, reason=new, client_name=unknown, client_address=93.91.234.150, sender=test@debian.org, recipient=test@example.org
May 21 07:23:05 test postfix/smtpd[2759]: NOQUEUE: reject: RCPT from unknown[93.91.234.150]: 450 4.2.0 <test@example.org>: Recipient address rejected: Greylisted, see http://postgrey.schweikert.ch/help/slums.de.html; from=<test@debian.org> to=<test@example.org> proto=SMTP helo=<debian.org>

```

```

/etc/postfix/main.cf
(...)
smtpd_recipient_restrictions = reject_unauth_pipelining,
 permit_mynetworks,
 permit_sasl_authenticated,
 reject_non_fqdn_recipient,
 reject_unknown_recipient_domain,
 reject_unauth_destination,
 reject_rbl_client sbl.spamhaus.org,
 check_policy_service inet:127.0.0.1:10023
 permit

```

---

