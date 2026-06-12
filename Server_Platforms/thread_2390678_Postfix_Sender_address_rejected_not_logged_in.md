---
title: "Postfix: Sender address rejected: not logged in"
date: 2018-05-01
forum: Server Platforms
---

### Post by the-junkmailer on 2018-05-01
Hi all,

First off, I have checked the following other threads for advice:
[https://ubuntuforums.org/showthread.php?t=2111524](https://ubuntuforums.org/showthread.php?t=2111524) - this didn't fix my problem since I'm OK with only sending emails from localhost (I use a webmail client).
[https://ubuntuforums.org/showthread.php?t=1453331](https://ubuntuforums.org/showthread.php?t=1453331) - this doesn't fix my problem since it's a different issue.

Here's the error I get from in /var/log/mail.log. example.com is the URL I'm sending from (in reality, a VPS I control), and [EMAIL="example@gmail.com"]example@gmail.com[/EMAIL] is really a different gmail address.
```

/var/log/syslog:May  1 09:11:06 example postfix/smtpd[1973]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 553 5.7.1 <me@example.com>: Sender address rejected: not logged in; from=<me@example.com> to=<example@gmail.com> proto=ESMTP helo=<mail.example.com>

```

Here is the output of postconf -n:
```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
compatibility_level = 3
default_destination_concurrency_limit = 5
disable_vrfy_command = yes
dovecot_destination_recipient_limit = 1
header_size_limit = 4096000
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}"
mailbox_size_limit = 0
milter_connect_macros = j {daemon_name} v {if_name} _
milter_default_action = accept
milter_protocol = 6
mydestination = mail.example.com, localhost.example.com, , localhost
myhostname = example.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
non_smtpd_milters = $smtpd_milters
postscreen_access_list = permit_mynetworks
postscreen_dnsbl_action = enforce
postscreen_dnsbl_sites = zen.spamhaus.org, b.barracudacentral.org, bl.spamcop.net
postscreen_greet_action = enforce
readme_directory = no
recipient_delimiter = +
relay_destination_concurrency_limit = 1
relayhost = [smtp.sendgrid.net]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = static:example:abc123
smtp_sasl_security_options = noanonymous
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, reject_non_fqdn_helo_hostname, reject_invalid_helo_hostname, reject_unknown_helo_hostname, permit
smtpd_milters = local:/var/run/opendkim/opendkim.sock
smtpd_recipient_restrictions = reject_unknown_client_hostname, reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_invalid_hostname, reject_non_fqdn_sender
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_login_maps = $virtual_mailbox_maps
smtpd_sender_restrictions = reject_unknown_sender_domain, reject_sender_login_mismatch
smtpd_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtpd_tls_ask_ccert = yes
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/letsencrypt/live/example.com/fullchain.pem
smtpd_tls_ciphers = high
smtpd_tls_key_file = /etc/letsencrypt/live/example.com/privkey.pem
smtpd_tls_loglevel = 1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
unknown_address_reject_code = 550
unknown_client_reject_code = 550
unknown_hostname_reject_code = 550
virtual_alias_maps = hash:/etc/postfix/virtual
virtual_mailbox_domains = hash:/etc/postfix/virtual-mailbox-domains
virtual_mailbox_maps = hash:/etc/postfix/virtual-mailbox-users
virtual_transport = dovecot

```

I've done some work to narrow down the problem, and it seems to be a problem with "reject_sender_login_mismatch" - if I remove it, I can send emails fine. Oddly, this was working only two days ago, and I haven't done any updates since then, or rebooted the VPS, or done anything else that might cause the config to get reloaded. (I've rebooted the VPS since, just in case there was an issue, but it didn't fix anything.)

I've looked at the docs for this setting, and it seems to indicate this happens when "the client login name doesn't own the MAIL FROM address according to $smtpd_sender_login_maps. " Here's a copy of virtual-mailbox-users:

```

me@example.com         me@example.com
postbot@example.com      postbot@example.com
webmaster@example.com    webmaster@example.com

```

Any tips are appreciated.

---

### Post by SeijiSensei on 2018-05-01
Maybe it's those double commas in mydestination?

---

### Post by the-junkmailer on 2018-05-01
Unfortunately not - thanks for the suggestion though.

---

