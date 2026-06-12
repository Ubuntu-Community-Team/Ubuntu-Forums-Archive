---
title: "Postfix SMTPD Error - Relay Access Denied"
date: 2014-11-08
forum: Server Platforms
---

### Post by thevjm on 2014-11-08
I have installed and configured a mail server on an Amazon EC2 instance following this [guide](http://arstechnica.com/information-t...domain-part-1/). I can login into my account from thunderbird, but I can't send or recieve mail. Here is the output from the error log:

```
Nov  9 01:50:40 postfix/smtpd[2792]: connect from mail-wg0-f42.google.com[74.125.82.42]
Nov  9 01:50:41 postfix/smtpd[2792]: Trusted TLS connection established from mail-wg0-f42.google.com[74.125.82.42]: TLSv1 with cipher ECDHE-RSA-AES128-SHA (128/128 bits)
Nov  9 01:50:41 postfix/smtpd[2792]: NOQUEUE: reject: RCPT from mail-wg0-f42.google.com[74.125.82.42]: 554 5.7.1 <user@mailserver.com>: Relay access denied; from=<user@gmail.com> to=<user@mailserver.com> proto=ESMTP helo=<mail-wg0-f42.google.com>
Nov  9 01:50:42 ip-172-31-27-91 postfix/smtpd[2792]: disconnect from mail-wg0-f42.google.com[74.125.82.42]
```

Postfix - main.cf
```
smtpd_banner = $myhostname ESMTP
biff = no
append_dot_mydomain = no
readme_directory = no
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, defer_unauth_destination
myhostname = mail.mailserver.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost, localhost.mailserver.com
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_sender_restrictions = reject_unknown_sender_domain
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot.conf -m "${EXTENSION}"
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom

## Customized smtpd parameters
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, reject_non_fqdn_helo_hostname, reject_invalid_helo_hostname, reject_unknown_helo_hostname, permit
smtpd_recipient_restrictions = reject_unknown_client_hostname, reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_invalid_hostname, reject_non_fqdn_sender
#smtpd_sender_restrictions = reject_unknown_sender_domain, reject_sender_login_mismatch
#smtpd_sender_login_maps = $virtual_mailbox_maps

## Dealing with rejection: use permanent 550 errors to stop retries
unknown_address_reject_code = 550
unknown_hostname_reject_code = 550
unknown_client_reject_code = 550

## customized TLS parameters
smtpd_tls_ask_ccert = yes
smtpd_tls_cert_file = /etc/ssl/private/ssl-chain-mail-yourdomain.pem
smtpd_tls_key_file = /etc/ssl/private/ssl.key
smtpd_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtpd_tls_ciphers = high
smtpd_tls_loglevel = 1
smtpd_tls_security_level = may
smtpd_tls_session_cache_timeout = 3600s

## Customized Dovecot and virtual user-specific settings
canonical_maps = hash:/etc/postfix/canonical
home_mailbox = Maildir/
message_size_limit = 104857600
virtual_alias_maps = hash:/etc/postfix/virtual
virtual_mailbox_domains = hash:/etc/postfix/virtual-mailbox-domains
virtual_mailbox_maps = hash:/etc/postfix/virtual-mailbox-users
virtual_transport = dovecot

## This setting will generate an error if you restart Postfix before
## adding the appropriate service definition in master.cf, so make
## sure to get that taken care of!
dovecot_destination_recipient_limit = 1

## Customized milter settings
milter_default_action = accept
milter_connect_macros = j {daemon_name} v {if_name} _
non_smtpd_milters = $smtpd_milters
smtpd_milters = unix:/spamass/spamass.sock unix:/opendkim/opendkim.sock
 
## Other customized mail server settings
default_destination_concurrency_limit = 5
disable_vrfy_command = yes
relay_destination_concurrency_limit = 1
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
```

---

### Post by lisati on 2014-11-08
Is "mailserver.com" your domain?

The reason mail for "mailserver.com" from Google's servers is being rejected is that you need to tell Postfix to accept mail for "mailserver.com" - this can be done by adding it to the mydestination line in the main.cf file.

---

### Post by thevjm on 2014-11-08
> **lisati said:**
> Is "mailserver.com" your domain?

The reason mail for "mailserver.com" from Google's servers is being rejected is that you need to tell Postfix to accept mail for "mailserver.com" - this can be done by adding it to the mydestination line in the main.cf file.
OK that worked, thanks! Now I'm getting some permission errors, not sure why because I thought dovecot running as the vmail user... :/
```
Nov  9 04:31:38 ip-172-31-27-91 dovecot: lda(thevjm): Error: file_dotlock_open(/var/mail/vmail//thevjm/mail/dovecot.index.log) failed: Permission denied (euid=1001(thevjm) egid=1001(thevjm) missing +w perm: /var/mail/vmail//thevjm/mail, we're not in group 5000(vmail), dir owned by 5000:5000 mode=0775)
Nov  9 04:31:38 ip-172-31-27-91 dovecot: lda(thevjm): Error: open(/var/mail/vmail//thevjm/mail/tmp/1415507498.M501257P8033.ip-172-31-27-91) failed: Permission denied

```
Not sure why this process is not running as vmail

---

### Post by avinash7 on 2014-12-24
You Need to create a [COLOR=#000000][FONT=Ubuntu Mono]group 5000(vmail) There is the Problem[/FONT][/COLOR]

---

