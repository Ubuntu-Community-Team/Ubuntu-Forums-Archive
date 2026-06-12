---
title: "postfix receiving time-stamp problem (beginner)"
date: 2010-09-08
forum: Server Platforms
---

### Post by nu_gen68 on 2010-09-08
I set up a mail server following flurdy's tutorial. But I have some small problems. Sometimes I receive some e-mails using Thunderbird that have the correct date, but the time is incorrect, usually a couple hours in the past.

This is when I receive e-mail from outside my e-mail server. 

I've checked the mail.log and it shows that I received the mail on time, it's just that the time-stamp on the e-mail is incorrect. I set up header_checks to prevent past and future dates from hitting the top or bottom of my inbox, but is there any way I can set it so the time-stamp is changed to the time it arrived to postfix versus the time on the sender's computer. It is a nuisance to look for random unread mails popping up here and there.

Please help.

My postfix main.cf
```

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
# Requirements for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service unix:private/policy, check_policy_service inet:127.0.0.1:10023, permit

# Require proper HELO at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

readme_directory = no

# virtual domains
local_recipient_maps =
mydestination =  $myhostname, localhost.$mydomain, localhost, $mydomain

# Header/Subject line checks
header_checks = regexp:/etc/postfix/maps/header_checks
# MIME file extension checks
#mime_header_checks = regexp:/etc/postfix/maps/mime_header_checks

message_size_limit = 40960000
recipient_bcc_maps = hash:/etc/postfix/recipient_bcc
sender_bcc_maps = hash:/etc/postfix/sender_bcc
myhostname = **********
mydestination = **********, localhost, 127.0.0.1
relayhost = 
mynetworks = 127.0.0.0/8 **********/24 127.0.0.1/32
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
content_filter = amavis:[127.0.0.1]:10024

```

---

### Post by kidders on 2010-09-09
Hi there,

It's not something I've ever tried to do, but I imagine you could use procmail to doctor the headers on incoming messages.

That wouldn't really *fix* anything though ... it'd just hide the problem. Receiving mail with incorrect timestamps is relatively unusual (unless of course it's spam). It'd be worth checking that all your clocks are right, and configured for the correct time zone. Can you pin the mis-timestamped messages down to a particular origin?

---

