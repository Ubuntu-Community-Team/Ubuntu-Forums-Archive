---
title: "smtpd_recipient_restrictions reject_rbl_client"
date: 2012-11-11
forum: Server Platforms
---

### Post by matthew1471 on 2012-11-11
Hi,

I'm confused about my main.cf config and could do with an explanation.

In the UK, the entire sky.com ip range is on the Spamhaus PBL [[http://www.spamhaus.org/pbl/query/PBL251585]](http://www.spamhaus.org/pbl/query/PBL251585]).

I thought that the main.cf below would allow my users who are on the sky.com network to send mail through my server, but it doesn't - sky.com users get a relay denied error, which I've traced to the smtpd_recipient_restrictions reject_rbl_client setting.

Why do the smtpd_recipient_restrictions reject_rbl_client checks stop their mail being sent when the users should already be authenticated by smtpd_recipient_restrictions permit_sasl_authenticated?

Thanks,
Matt


postconf -n

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
home_mailbox = Maildir
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination =
myhostname = server.server.co.uk
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_helo_required = yes
smtpd_recipient_restrictions =
permit_sasl_authenticated,              
reject_non_fqdn_sender,              
reject_non_fqdn_recipient,              
reject_unknown_sender_domain,              
reject_unknown_recipient_domain,              
reject_unauth_pipelining,              
permit_mynetworks,             
reject_unauth_destination,              
reject_rbl_client zen.spamhaus.org,             
reject_rbl_client list.dsbl.org,              
permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_address
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_gid_maps = static:5000
virtual_mailbox_base = /
virtual_mailbox_domains = ldap:/etc/postfix/ldap-domains.cf
virtual_mailbox_maps = ldap:/etc/postfix/ldap-maps.cf
virtual_uid_maps = static:5000

---

### Post by lisati on 2012-11-11
I use postfix too. In my experience, a rejection message which mentions "relay denied" is more likely to be caused by postfix not recognising the domain part of the recipient's email address as one it deals with locally. This is usually set with a virtual domain name or on the mydestinations parameter.

edit: oh, I read your post again. Are you wanting to let users of your email system to send mail FROM your server?

---

### Post by matthew1471 on 2012-11-11
Hi,

Yes, the users are authenticated by Dovecot, so I don't understand why they're reaching the reject_rbl_client stage.

It's very strange.

---

