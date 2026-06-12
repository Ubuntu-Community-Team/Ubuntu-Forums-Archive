---
title: "reject email"
date: 2013-10-05
forum: Server Platforms
---

### Post by Bondar_Mircea on 2013-10-05
How to reject email with not have reverse dns?

my postfix conf. is:
```
smtpd_sasl_auth_enable  = yes
broken_sasl_auth_clients = yes
smtpd_sasl_type         = dovecot
smtpd_sasl_path         = private/auth
mailbox_transport       = dovecot
disable_vrfy_command    = yes
smtpd_delay_reject      = yes
smtpd_helo_required     = yes
smtpd_sender_restrictions =
                        permit_sasl_authenticated,
                        permit_mynetworks,
                        reject_non_fqdn_sender,
                        reject_unknown_sender_domain,
                        permit

smtpd_recipient_restrictions =
        permit_sasl_authenticated,
        permit_mynetworks,
        reject_non_fqdn_recipient,
        reject_unknown_recipient_domain,
        reject_unauth_destination,
        reject_unauth_pipelining,
        reject_unknown_reverse_client_hostname


```

---

### Post by SeijiSensei on 2013-10-05
Try
```
smtpd_client_restrictions = reject_unknown_reverse_client_hostname
```

That's a bit more permissive than "reject_unknown_client_hostname".  [Details here](http://www.postfix.org/postconf.5.html#reject_unknown_client_hostname).

---

### Post by Bondar_Mircea on 2013-10-07
Not working.Still receive message wich no have rdns. In postfix a have this config

---

### Post by lisati on 2013-10-07
> **Bondar_Mircea said:**
> Not working.Still receive message wich no have rdns. In postfix a have this config

Apologies in advance if this is "obvious" but did you remember to restart postfix after updating its config?

---

### Post by Bondar_Mircea on 2013-10-07
yes..i restarted postfix..

---

### Post by SeijiSensei on 2013-10-07
What do you see in mail.log?  When my server encounters senders with IPs that have no reverse resolution, I get an entry like this:

```
Oct  7 09:41:32 Pikachu postfix/smtpd[11738]: NOQUEUE: reject: CONNECT from unknown[66.35.68.70]: 450 4.7.1 Client host rejected: cannot find your hostname, [66.35.68.70]; proto=SMTP
```

---

