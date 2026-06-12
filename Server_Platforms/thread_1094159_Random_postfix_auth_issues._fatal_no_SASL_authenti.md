---
title: "Random postfix auth issues. fatal: no SASL authentication mechanisms"
date: 2009-03-12
forum: Server Platforms
---

### Post by comet on 2009-03-12
Hey guys, there's a lot of info about this problem out there but nothing seems to meet my criteria. One day out of the blue, my postfix server starting spewing out this error message in the mail.log. It has been running fine for a couple months now. 


I'm currently using pgsql as a virtual user manager for my dovecot and postfix users. Although hardly ANY of my users are actually using the SMTP server. I usually convince them to use their ISP's SMTP. Here's the error:

```


Mar 11 15:00:37 vps117 postfix/smtpd[15936]: fatal: no SASL authentication mechanisms
Mar 11 15:00:38 vps117 postfix/master[11633]: warning: process /usr/lib/postfix/smtpd pid 15930 exit status 1
Mar 11 15:00:38 vps117 postfix/master[11633]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Mar 11 15:00:38 vps117 postfix/master[11633]: warning: process /usr/lib/postfix/smtpd pid 15935 exit status 1
Mar 11 15:00:38 vps117 postfix/master[11633]: warning: process /usr/lib/postfix/smtpd pid 15936 exit status 1
Mar 11 15:01:38 vps117 postfix/smtpd[17590]: warning: SASL: Connect to private/auth failed: Connection refused

```

This error message technically means that it can't find the the method of sasl-auth I'm using which is just regular old plain auth. However, upon restarting the postfix server the issue corrected itself.

This just happened out of the blue for no reason at all. I'm just looking for an answer on how to prevent this from happening in the future. Has anyone ever had this randomly happen to them?

here's the info from my postconf in relation to sasl:

```


broken_sasl_auth_clients = yes
cyrus_sasl_config_path =
lmtp_sasl_auth_cache_name =
lmtp_sasl_auth_cache_time = 90d
lmtp_sasl_auth_enable = no
lmtp_sasl_auth_soft_bounce = yes
lmtp_sasl_mechanism_filter =
lmtp_sasl_password_maps =
lmtp_sasl_path =
lmtp_sasl_security_options = noplaintext, noanonymous
lmtp_sasl_tls_security_options = $lmtp_sasl_security_options
lmtp_sasl_tls_verified_security_options = $lmtp_sasl_tls_security_options
lmtp_sasl_type = cyrus
proxy_write_maps = $smtp_sasl_auth_cache_name $lmtp_sasl_auth_cache_name
send_cyrus_sasl_authzid = no
smtp_sasl_auth_cache_name =
smtp_sasl_auth_cache_time = 90d
smtp_sasl_auth_enable = no
smtp_sasl_auth_soft_bounce = yes
smtp_sasl_mechanism_filter =
smtp_sasl_password_maps =
smtp_sasl_path =
smtp_sasl_security_options = noplaintext, noanonymous
smtp_sasl_tls_security_options = $smtp_sasl_security_options
smtp_sasl_tls_verified_security_options = $smtp_sasl_tls_security_options
smtp_sasl_type = cyrus
smtpd_recipient_restrictions = permit_mynetworks  permit_sasl_authenticated  reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = no
smtpd_sasl_exceptions_networks =
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_tls_security_options = $smtpd_sasl_security_options
smtpd_sasl_type = dovecot

```

I just don't know why restarting the server fixes the problem, and why the problem occurs in the first place. When the error starts happening, we start getting emails saying "Delivery Notification Status (Delay)".

I appreciate any further insight on the matter. Thanks so much for your time.

---

### Post by comet on 2009-03-12
hey again guys.. i'm shedding a little light here..

My company has their own in-house MS Exchange Server.. Unfortunately our internet provider doesn't allow us to relay mail from our Exchange Servers using their SMTP. Hence, I setup postfix on my own VPS with proper PTR's so that we could use it as a relay.

Upon looking at my log files, I noticed that the Exchange Server was the last connection attempt that was made to postfix before I started getting those errors.

My question is, why would MS Exchange cost Postfix and sasl to do this? Any insight on how to prevent this from happening again?

Thanks again....

---

### Post by comet on 2009-03-12
SOLVED!!!!

Upon looking deeper in my log files, I noticed this error right before I started getting the mechanisms warning...

postfix/qmgr[11636]: warning: backward time jump detected -- slewing clock

dovecot: Time just moved backwards by 18931 seconds. This might cause a lot of problems so I'll just kill myself now. [http://wiki.dovecot.org/TimeMovedBackwards](http://wiki.dovecot.org/TimeMovedBackwards)


HAHAH AMAZING.. I guess due to Daylight Savings, this caused a MAJOR issue. This is what sucks about using a VPS sometimes.. You can only control so many things, and time isn't one of them.

---

