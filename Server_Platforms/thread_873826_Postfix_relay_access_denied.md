---
title: "Postfix: relay access denied"
date: 2008-07-29
forum: Server Platforms
---

### Post by 448191 on 2008-07-29
I'm getting the infamous 'Relay Access Denied' error when trying to a 'foreign' domain. 

> **448191:/etc/postfix# postconf -n**
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps =
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
masquerade_domains = mail.x.nl
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
myhostname = mail.x.nl
mynetworks_style = host
myorigin = x.nl
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_delay_reject = no
smtpd_hard_error_limit = 12
smtpd_helo_required = no
smtpd_helo_restrictions =
smtpd_recipient_limit = 16
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = smtpd
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated
smtpd_soft_error_limit = 3
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

The mysql query log has this in it (changed domain names):

> 
                     12 Query       SELECT domain FROM domains WHERE domain='x.nl' and enabled = 1
                     11 Query       SELECT destination FROM aliases WHERE mail='other.nl' and enabled = 1
                     12 Query       SELECT domain FROM domains WHERE domain='x.nl' and enabled = 1

So apparently it is trying to if the destination address is locally defined, which it shouldn't do, I imagine...

How to fix? :(

---

### Post by 448191 on 2008-07-30
bump.

---

### Post by MJN on 2008-07-30
Is your client authenticating correctly? (given that is the only form of relay access you've permitted i.e. no trusted local network allowance)
 
Mathew

---

