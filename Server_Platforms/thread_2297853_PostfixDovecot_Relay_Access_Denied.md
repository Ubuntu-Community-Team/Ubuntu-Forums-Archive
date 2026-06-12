---
title: "Postfix/Dovecot Relay Access Denied"
date: 2015-10-07
forum: Server Platforms
---

### Post by terencewklau on 2015-10-07
Hi All,

I currently have a postfix (2.11)/dovecot (2.2.9) setup on Ubuntu Server 14.04.  Smtp relay is allowed by a config file where ip addresses that are allowed to relay are listed and delivery is via dovecot.  Mailboxes are virtual.

Smtp relay is working find as long as the client's ip addresses is listed in the config file.  But there is a case where the client will need to relay using credentials as its on DHCP.  I've created a local account in /etc/passwd (without a mailbox as it doesn't need to receive mail) but when I tried to send email from the client using this account, I get a 454 4.7.1 relay access denied.

How can I allow relaying using local user account credentials without having to first include the client's ip address in the config file?

Here's the postconf -n:

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
dovecot_destination_recipient_limit = 1
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = ipv4
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot.conf -m "${EXTENSION}"
mailbox_size_limit = 0
message_size_limit = 20480000
mydestination = smtp.domain.com, servername.domain.com, localhost.domain.com, localhost
myhostname = smtp.domain.com
mynetworks = /etc/postfix/domainrelays.cf
myorigin = /etc/mailname
postscreen_access_list = permit_mynetworks
postscreen_upstream_proxy_protocol = haproxy
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unknown_recipient_domain, reject_unauth_pipelining, reject_unauth_destination
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_CAfile = /etc/ssl/certs/DigiCertSecureServerCA.crt
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtp.domain.com.crt
smtpd_tls_key_file = /etc/ssl/private/smtp.domain.com.key
smtpd_tls_loglevel = 1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
virtual_alias_maps = hash:/etc/postfix/valias
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_transport = dovecot
virtual_uid_maps = static:5000
```

Thanks.

---

### Post by SeijiSensei on 2015-10-07
A simple but slightly insecure method would be to permit the entire subnet served by DHCP rather than an individual address.  Say the client gets an address like 192.168.1.34 one day and 192.168.1.58 another.  Permitting 192.168.1.0/24 would allow both addresses to connect.

I don't know if you have control over the DHCP server, but you might also consider giving the leases long lifetimes like months or a year.  On a network where there are fewer actual client machines than available addresses, long leases make the most sense. It's a simple alternative to static addressing, though DHCP servers also allow you to pre-allocate addresses to specific MACs and render them static.

---

### Post by terencewklau on 2015-10-07
I'm hoping to avoid having to change anything on the DHCP end.  And allowing the entire subnet is not permitted.

Thing is on our previous postfix/dovecot server, which was based on local users, I could relay through it using one of the local account credentials.  This is the previous config:

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = MailDir/
inet_interfaces = all
inet_protocols = ipv4
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 20480000
mydestination = smtp.domain.com, servername.domain.com, localhost.domain.com, localhost
myhostname = smtp.domain.com
mynetworks = /etc/postfix/domainrelays.cf
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_sasl_auth_enable = no
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_recipient_restrictions = permit_mynetworks, reject_unknown_recipient_domain, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/DigiCertSecureServerCA.crt
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtp.domain.com.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtp.domain.com.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
```

Now that we've upgraded and moved to virtual users, and using dovecot as the delivery agent, this doesn't work.  Looking at the logs, postfix seems to check the client ip address and if it doesn't match the mynetworks, its relay access denied.

No attempt at verifying the credentials at all.

---

### Post by Habitual on 2015-10-08
> **terencewklau said:**
> Looking at the logs, postfix seems to check the client ip address and if it doesn't match the mynetworks, its relay access denied.

No attempt at verifying the credentials at all.
You mean the IP of the "new" postfix host?

As stated allowing 192.168.1.0/24 in mynetworks should permit this new host to relay.

---

### Post by terencewklau on 2015-10-08
I meant the client who's sending the email (its ip address).  If its not in the config file configured in mynetworks, its not allowed to relay.

Poked around some more and saw "!include auth-system.conf.ext" in 10-auth.conf was not enabled.  Now authentication works when testing via telnet.

But the original issue actually came from a client using powershell (Windows 7) to send an email.  This is still not allowed to relay.  Must be something different in the way powershell sends the credentials through for authentication.

---

