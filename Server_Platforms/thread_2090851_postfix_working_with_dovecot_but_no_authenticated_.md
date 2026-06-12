---
title: "postfix working with dovecot but no authenticated smtp"
date: 2012-12-03
forum: Server Platforms
---

### Post by cqfast on 2012-12-03
I have been successfully running postfix + dovecot using Ubuntu 12.04 on a 64-bit AMD machine.  Until now, in order to use my postfix smtp to send external email, the user had to be on my trusted local network (or VPN'd to my trusted local network).

But now I wanted to enable authenticated SMTP so that a user did not need to be VPN'd in after all.  I followed the directions on help.ubuntu.com/12.04/serverguide/postfix.html but have apparently not yet correctly enabled/configured the smtp authentication, because there is not a "250-AUTH" line advertised:

```

telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 xxxx.xxxxxx.xxx ESMTP Postfix (Ubuntu)
ehlo localhost
250-xxxx.xxxxxx.xxx
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
quit
221 2.0.0 Bye
Connection closed by foreign host.

```

Postfix does appear to be compiled with the ability:
```

postconf -a
cyrus
dovecot

```

Postfix main.cf settings that I think are relevant:
```

smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}"
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes

```

dovecot.conf:
```

!include_try /usr/share/dovecot/protocols.d/*.protocol
auth default {
  mechanisms = plain login
  passdb pam {
  }
  userdb passwd {
  }
  user = root
  !include_try /etc/dovecot/auth.d/*.auth
}
dict {
}
!include conf.d/*.conf
!include_try local.conf

```

/etc/dovecot/auth.d/01-mail-stack-delivery.auth:
```

mechanisms = plain login
socket listen {
        client {
                path = /var/spool/postfix/private/dovecot-auth
                mode = 0660
                user = postfix
                group = postfix
        }
}

```

/etc/dovecot/conf.d/01-mail-stack-delivery.conf settings that I think are relevant:
```

disable_plaintext_auth = yes
ssl = yes
ssl_cert = </etc/ssl/certs/ssl-mail.pem
ssl_key = </etc/ssl/private/ssl-mail.key
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
auth_mechanisms = plain login
service auth {
  unix_listener /var/spool/postfix/private/dovecot-auth {
    mode = 0660
    user = postfix
    group = postfix
  }
}

```

I've read numerous help docs that seem to provide the same advice in slightly different variations (e.g. different names for the socket).  I'm a little concerned that I may have combined instructions that came from different approaches for configuring dovecot; I seem to have some redundant dovecot settings above.

Are there any tests or logs I should check, to determine the current state of my authenticated smtp?  The /var/log/mail.err does not currently indicate any errors.  Earlier, when I was experimenting with different options, I got some errors complaining:
  postfix/smtpd[18234]: fatal: no SASL authentication mechanisms
but am no longer getting these errors.  And my postfix setup is still successfully sending mail from my local trusted network.

What have I missed?

---

