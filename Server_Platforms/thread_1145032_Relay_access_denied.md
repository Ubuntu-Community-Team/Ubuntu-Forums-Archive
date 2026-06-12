---
title: "Relay access denied"
date: 2009-05-01
forum: Server Platforms
---

### Post by Dy1anW on 2009-05-01
I have a Postfix + CourierIMAP + MySQL + ClamAV + Postgrey + Amavis + Spamassin setup on my server.  I can access/retrieve/send mails using Squirrelmail on both my workstation and my server, that's no problem.

On my workstation, I'm using Thunderbird and can access/retrieve from my server on SSL; that's fine.  What I can't seem to do is send via relay (and end up getting the error message that makes up the title of this thread), unless I set all my smtpd_*_restrictions = permit, which isn't a fantastic thing to do.  Here's a few relevant snippets from my main.cf:

```
mynetworks = 192.168.0.0/16, 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```

I'm not sure about the IPv6 stuff (the main.cf file had that by default), but this *should* give all computers on 127.0.0.* and 192.168.*.* access to "mynetwork"

```

# SASL Authentication
smtp_sasl_auth_enable = yes
smtpd_sasl_type = cyrus
smtpd_sasl_path = smtpd
smtpd_sasl_authenticated_header = no
smtpd_sasl_exceptions_networks = $mynetworks
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps=hash:/etc/postfix/sasl_passwd
smtpd_sasl_local_domain = 
broken_sasl_auth_clients = no

```

In case that may be useful...  I'm actually wondering why some lines are smtp and others are smtpd.  Did I get this wrong?  Admittedly this was done in the wee hours of the morning, so I was probably 'out of it'.

```

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_invalid_hostname, permit
# Requirements for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

```

Considering they permit_mynetworks, shouldn't my_networks be permitted?!  Or did I do something that essentially contradicts?

---

### Post by Dy1anW on 2009-05-01
Okay, I've singled out the one line that's causing problems.  When:

smtpd_recipient_restrictions = permit, reject_unauth_destination

I can send out from my client just fine, but when I edit this to:

smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination

I'm suddenly unable to send mails again, and get stuck with the faimilar error code again.  This suggests that:

mynetworks = 192.168.0.0/16 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

is the cause of the problem, and I'm sure the solution is laughably easy, but I just can't figure it out right now.


Actually, even when I specify my workstation's IP (192.168.1.2) it still won't connect.

---

### Post by Dy1anW on 2009-05-01
And so it turns out the problem *was* pretty straight forward after all.  I was using the full server name for the outbound mail server, DNS resolved the host and thus my IP was from my ISP and not from my local domain, so it wouldn't have matched $mynetworks.  Plugging in the direct IP solved it... though I wonder why I didn't get the same problem with incoming mail even though the restrictions are similar... strange!


As a side note,the problem could've also been solved using a local DNS.

---

### Post by vnkatesh on 2009-11-25
Thank you!

---

