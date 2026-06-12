---
title: "Postfix smtp authentication"
date: 2006-08-29
forum: Server Platforms
---

### Post by mwerlberger on 2006-08-29
Hi!

I configured my postfix so that only authenticated users can send mail via the server. But looking at the logs after a day running i get this:

Aug 29 22:21:33 athena postfix/smtp[18690]: 64FB61CB20D: to=<...snip...>, relay=bsmtp.telekom.at[213.33.87.14], delay=1, status=sent (250 OK id=1GIA5U-0001rK-PQ)

Whereas i did never send a mail to the user that is listet in to=<>.

Should i be worried that my box is used to distribute spam??

in my /etc/postfix/main.cf i have:

```

ssmtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_password
smtp_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_application_name = smtpd
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,
        permit_mynetworks, reject_unauth_destination,
        check_relay_domains, reject_unauth_pipelining
# TODO smtpd_sender_restrictions = check_sender_access
smtpd_tls_auth_only = yes
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

Everything ok or should i be a little bit worried.

Rgds,
 Manuel

---

### Post by chrisfay on 2006-08-30
What do you have listed in 'mynetworks'?

---

### Post by mwerlberger on 2006-08-30
mynetworks = 127.0.0.0/8, 192.168.1.0/24

---

