---
title: "Postfix Sender Dependent Relay help"
date: 2016-06-30
forum: Server Platforms
---

### Post by wildcatleeds on 2016-06-30
Hi there,
We're currently migrating from Novell Groupwise as our relay server to using postfix relaying to our parent organization's email system.  The scenario is as follows:

    All secure emails must be sent using FROM: [email]email.secure@trust.net[/email] and transport through send.trust.net
    All unsecure emails (not containing confidential, PID, etc) can come FROM anyone and transport through relay.trust.uk

TLS is working fine to send.trust.net and mail sent using FROM:  [email]email.secure@trust.net[/email] is flowing correctly through send.trust.uk.  But these are the results of my testing so the sender dependent doesn't seem to be configured properly:

    FROM [email]email.secure@trust.net[/email] TO [email]anyone@anywhere.anywhe[/email]re transports through send.trust.net (expected and correct, restricted to the relay_domains for recipients)
    FROM [email]anyone@trust.net[/email] TO [email]anyone@trust.net[/email] transports through send.trust.net (not correct.  should be relay.trust.uk)
    FROM [email]anyone@anywhere.anywhe[/email]re TO [email]anyone@anywhere.anywhe[/email]re transports through relay.trust.uk (expected and correct)

We have configured only two domains allowed to relay, new domain and old domain, and we have relay_domains for the domains which are allowed to relay to.  I suspect that something is overriding something else or we're missing a parameter in the main.cf.

Any assistance would be very appreciated.
Yours,
WC

Configuration files follow:

```
main.cf
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydomain = old.domain.uk
myhostname = RELAYSVR.old.domain.uk
myorigin = $myhostname
# DISABLE LOCAL MAIL DELIVERY BY SETTING TO EMPTY
mydestination =
local_recipient_maps =
local_transport = error: local main delivery disabled
# ALLOWS TO RELAY THROUGH THIS GATEWAY
mynetworks = 127.0.0.0/8 xxx.xxx.xxx.xxx/16 yyy.yyy.yyy.yyy zzz.zzz.zzz.zzz 192.168.0.0/16
# DOMAINS FOR WHICH THIS GATEWAY WILL ACCEPT EMAILS
relay_domains = $myhostname, hash:/etc/postfix/relay_domains
# Transport Map
transport_maps = hash:/etc/postfix/transport
# Relay Host Map
sender_dependent_relayhost_maps = hash:/etc/postfix/relayhost_map
# SASL
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
# TLS
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtp_sasl_tls_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/GlobalSign_DV_CA.pem
smtp_tls_loglevel = 2
# TLSv1 or better:
smtp_tls_protocols = !SSLv2, !SSLv3
smtp_tls_security_level = may
# GENERAL
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
compatibility_level = 2

relay_domains (only partial list):
trust.net     OK
old.domain.uk   OK
yahoo.com   OK
esteem.co.uk   OK
emc.com     OK
block.co.uk   OK
textmagic.com   OK
text.aql.com   OK
paging.vodafone.net   OK
clearwater.eu.com   OK

transport:
trust.net       smtp:[secure.trust.net]:587
*       smtp:[relay.trust.uk]

relayhost_map:
# Per-sender provider
@trust.net     [send.trust.net]:587
*       [relay.trust.uk]
```

---

### Post by wildcatleeds on 2016-07-12
Sorted!
Added sender_dependent_default_transport_maps to **main.cf**
**sender_dependent_default_transport_maps = hash:/etc/postfix/sender_transport**


**sender_transport:**
[email]email.secure@trust.net[/email]    smtp:[send.trust.net]:587


commented out the default transport map in **main.cf**:
**# transport_maps = hash:/etc/postfix/transport**


uncommented out the relayhost entry in main.cf:
**relayhost = [relay.trust.net]**



That seems to have done the trick.

Sorted!
Added sender_dependent_default_transport_maps to [B]main.cf
sender_dependent_default_transport_maps = hash:/etc/postfix/sender_transport[/B]

**sender_transport:**
email.secure @ trust.net smtp:[send.trust.net]:587

commented out the default transport map in **main.cf**:
**# transport_maps = hash:/etc/postfix/transport**

uncommented out the relayhost entry in main.cf:
**relayhost = [relay.trust.net]**

That seems to have done the trick.

---

