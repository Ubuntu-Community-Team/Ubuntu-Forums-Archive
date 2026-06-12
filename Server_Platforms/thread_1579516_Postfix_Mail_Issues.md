---
title: "Postfix Mail Issues"
date: 2010-09-21
forum: Server Platforms
---

### Post by CormoranTick on 2010-09-21
I'm running a postfix server that doesn't want to receive mail form the internet. It worked fantastic when I first set it up, but suddenly it stopped receiving emails from the any server other than itself. My /var/log/mail.log file displays the following over and over: (emails have been changed for security)

```
Sep 21 23:38:13 vserver1 postfix/smtpd[2895]: connect from mail-pz0-f53.google.com[209.85.210.53]
Sep 21 23:38:13 vserver1 postgrey[1201]: action=pass, reason=client whitelist, client_name=mail-pz0-f53.google.com, client_address=209.85.210.53, sender=internet.email@user.com, recipient=local.email@domain.com
Sep 21 23:38:13 vserver1 postfix/smtpd[2895]: 98F03280ADE: client=mail-pz0-f53.google.com[209.85.210.53]
Sep 21 23:42:58 vserver1 postfix/smtpd[2891]: timeout after DATA (0 bytes) from mail-pw0-f53.google.com[209.85.160.53]
Sep 21 23:42:58 vserver1 postfix/smtpd[2891]: disconnect from mail-pw0-f53.google.com[209.85.160.53]
```I have fiddled and tweaked every setting my firewalls have to offer, to no avail. Obviously a connection is being made and kept, but data can't seem to be transferred back and forth for whatever reason. I am at my wit's end with this problem. Anyone have any thoughts?

---

### Post by Vegan on 2010-09-22
Can you post you config file so we can see what is up?

---

### Post by CormoranTick on 2010-09-22
/etc/postfix/main.cf
```
# myhostname = /etc/mailname
myorigin = domain.com
smtpd_banner = $myhostname ESMTP $mail_name
relayhost = smtp.isp.net
inet_interfaces = all
mynetworks_style = host
# masquerade_domains = mail.domain.com www.domain.com
# masquerade_exceptions = root
local_recipient_maps =
mydestination =
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_data_restrictions = reject_unauth_pipelining

smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# transport_maps = mysql:/etc/postfix/mysql_transport.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf

content_filter = amavis:[127.0.0.1]:10024

biff = no
append_dot_mydomain = no
readme_directory = no
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +

#smtp_use_tls = no
smtp_tls_security_level = may
#smtpd_use_tls = no
smtpd_tls_security_level = may
#smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_cert_file=/etc/ssl/certs/mail.domain.com.crt
smtpd_tls_key_file=/etc/ssl/private/mail.domain.com.key
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
```

---

### Post by minhnghivn on 2010-09-22
I think the problem was due to the following lines:
> smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_data_restrictions = reject_unauth_pipelining
First of all, try commenting out all the above lines which restrict certain kind of senders, receivers (this will make your Postfix an open relay server, of course!)
If the problem is solved then, just uncomment the above lines one by one to figure out the exact line that caused your problem

---

### Post by CormoranTick on 2010-09-22
An interesting thought. Doesn't seem entirely likely though. If Postfix was rejecting the client it would actually reject it, not just let it time out. Also, the client connects and communicates fine until it tries to send the DATA section of the message; only then timing out. When I get the mail delivery error it doesn't report a rejection either, just a timeout.

I did however get a couple failure emails that reported this:
> Diagnostic-Code: X-Postfix; unknown mail transport error

So once again I'm still unsure as to what could be wrong. I'll give it a try though and see if if the client/sender/data restrictions are causing the issue. Thanks for the help.

---

### Post by CormoranTick on 2010-09-22
No dice on that idea. Just commented out all the restriction lines and it's still doing the same thing. Anyone else have some any ideas on things to try? Thanks.

---

### Post by perspectoff on 2010-09-22
Stupid idea, but try restarting your network:

 sudo /etc/init.d/networking restart

---

### Post by CormoranTick on 2010-09-22
Trust me, that was the first thing I tried. And I've tried it 100 times since then too. Rebooted the server, rebooted the firewall, rebooted the modem....

---

