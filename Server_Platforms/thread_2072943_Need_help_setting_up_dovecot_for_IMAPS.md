---
title: "Need help setting up dovecot for IMAPS"
date: 2012-10-18
forum: Server Platforms
---

### Post by holoplex on 2012-10-18
Hi all,

I'm trying to setup dovecot following instructions [here]("https://help.ubuntu.com/12.04/serverguide/dovecot-server.html") and [here]("https://help.ubuntu.com/community/Dovecot"). I've got as far as testing the server is working using **telnet localhost imap2**, but when I setup dovecot to bind to a public facing interface (as shown in the commented out lines below) and restart dovecot, telnet comes back with connection refused.

**/etc/dovecot/dovecot.conf:**
```
protocols = imap imaps
#protocol imap {
#     listen = *:143
#     ssl_listen = *:993
#     login_greeting_capability = yes
#     imap_client_workarounds = tb-extra-mailbox-sep
#}
mail_location = maildir:~/Maildir
ssl = yes
ssl_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
ssl_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
ssl_disable = no

```

Could someone help me to correction the configuration. Thanks

---

