---
title: "Postfix not relaying to external domains."
date: 2010-01-16
forum: Server Platforms
---

### Post by matthew1471 on 2010-01-16
Hi,

I'm having a problem with a new install of postfix... it won't relay mail to external domains. Internal mail is fine.

I'm using virtual_mailbox_domains so that I can have multiple domains, and I've set dovecot to use local files with encrypted passwords.

Here's my main.cf

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
delay_warning_time = 4h
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
local_recipient_maps = 
mailbox_size_limit = 0
mydestination = 
mydomain = polyvisual.co.uk
myhostname = mail.polyvisual.co.uk
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128,192.168.0.0/24
myorigin = polyvisual.co.uk
readme_directory = no
recipient_delimiter = +
relayhost = 
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
tls_random_source = dev:/dev/urandom
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = /etc/postfix/virtualdomains
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000

```

The mail.log file shows:

```

Jan 16 10:12:15 polyvisual postfix/smtpd[11338]: connect from 5ace2f81.bb.sky.com[90.206.47.129]
Jan 16 10:12:15 polyvisual postfix/smtpd[11338]: NOQUEUE: reject: RCPT from 5ace2f81.bb.sky.com[90.206.47.129]: 554 5.7.1 <xxxxxx.xxxxx@googlemail.com>: Relay access denied; from=<xxxxx@polyvisual.co.uk> to=<xxxxx.xxxxxx@googlemail.com> proto=ESMTP helo=<[192.168.0.3]>
Jan 16 10:12:17 polyvisual postfix/smtpd[11338]: disconnect from 5ace2f81.bb.sky.com[90.206.47.129]

```

Please can someone assist? :D

---

### Post by matthew1471 on 2010-01-16
oops, this is my main.cf

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
delay_warning_time = 4h
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
local_recipient_maps = 
mailbox_size_limit = 0
mydestination = 
mydomain = polyvisual.co.uk
myhostname = mail.polyvisual.co.uk
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128,192.168.0.0/24
myorigin = polyvisual.co.uk
readme_directory = no
recipient_delimiter = +
relayhost = 
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
tls_random_source = dev:/dev/urandom
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = /etc/postfix/virtualdomains
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
```

---

### Post by matthew1471 on 2010-01-16
Actually, I think I've fixed it.

I'd not setup dovecot conf correctly.

I'll confirm in a moment.

---

