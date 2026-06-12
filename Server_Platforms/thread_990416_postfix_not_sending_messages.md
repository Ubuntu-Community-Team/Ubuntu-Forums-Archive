---
title: "postfix not sending messages"
date: 2008-11-22
forum: Server Platforms
---

### Post by javierccs on 2008-11-22
hello i have this error and i have search all over google, but i cant seem to find any solution....

Nov 22 17:34:23 smtpserver postfix/smtpd[18533]: connect from fqdnclient[192.168.4.22]
Nov 22 17:34:23 smtpserver postfix/smtpd[18533]: warning: unknown smtpd restriction: "\"
Nov 22 17:34:23 smtpserver postfix/smtpd[18533]: NOQUEUE: reject: RCPT from fqdnclient[192.168.4.22]: 451 Server configuration error; from=<javier@mydomain> to=<javier@gmail.com> proto=ESMTP helo=<fqdnclient>
Nov 22 17:34:23 smtpserver postfix/cleanup[18534]: 51C7DF0055: message-id=<20081122213423.51C7DF0055@smtpserverfqdn>
Nov 22 17:34:23 smtpserver postfix/smtpd[18533]: disconnect from fqdnclient[192.168.4.22]
Nov 22 17:34:23 smtpserver postfix/qmgr[18435]: 51C7DF0055: from=<double-bounce@fqdncli>, size=903, nrcpt=1 (queue active)
Nov 22 17:34:23 smtpserver postfix/smtp[18535]: 51C7DF0055: to=<postmaster@smtpserverfqdn>, orig_to=<postmaster>, relay=192.168.4.22[192.168.4.22], delay=0, status=sent (250 Ok: queued as 33905C0734)
Nov 22 17:34:23 smtpserver postfix/qmgr[18435]: 51C7DF0055: removed
Nov 22 17:34:23 smtpserver postfix/smtpd[18533]: connect from fqdnclient[192.168.4.22]
Nov 22 17:34:23 smtpservera postfix/smtpd[18533]: 59AB4F0055: client=fqdncliente[192.168.4.22]
Nov 22 17:34:23 smtpserver postfix/cleanup[18534]: 59AB4F0055: message-id=<20081122213423.51C7DF0055@autana.antv.gob.ve>
Nov 22 17:34:23 smtpserver postfix/smtpd[18533]: disconnect from fqdnclient[192.168.4.22]
Nov 22 17:34:23 smtpserver postfix/qmgr[18435]: 59AB4F0055: from=<double-bounce@smtpserverfqdn>, size=1318, nrcpt=1 (queue active)
Nov 22 17:34:23 smtpserver postfix/smtp[18535]: 59AB4F0055: to=<postmaster@smtpserverfqdne>, relay=none, delay=0, status=bounced (Host or domain name not found. Name service error for name=localhost type=AAAA: Host not found)
Nov 22 17:34:23 smtpserver postfix/bounce[18536]: warning: 59AB4F0055: undeliverable postmaster notification discarded
Nov 22 17:34:23 smtpserver postfix/qmgr[18435]: 59AB4F0055: removed

now im just trying to send an email to my gmail account, heres my postconf -n

smtpserver:/etc/postfix # postconf -n
alias_maps = hash:/etc/aliases, ldap:/etc/postfix/ldapalias_maps_member.cf, ldap:/etc/postfix/ldapalias_maps.cf
biff = no
canonical_maps = hash:/etc/postfix/canonical
command_directory = /usr/sbin
config_directory = /etc/postfix
content_filter =
daemon_directory = /usr/lib/postfix
debug_peer_level = 2
defer_transports =
disable_mime_output_conversion = no
home_mailbox =
html_directory = /usr/share/doc/packages/postfix/html
inet_interfaces = all
inet_protocols = all
local_recipient_maps = $alias_maps, ldap:/etc/postfix/ldaplocal_recipient_maps.cf
mail_owner = postfix
mail_spool_directory = /var/spool/mail
mailbox_command =
mailbox_size_limit = 0
mailbox_transport =
mailq_path = /usr/bin/mailq
manpage_directory = /usr/share/man
masquerade_classes = envelope_sender, header_sender, header_recipient
masquerade_domains = ldap:/etc/postfix/ldapmasquerade_domains.cf
masquerade_exceptions = root
message_size_limit = 10240000
mydestination = $myhostname, localhost.$mydomain, $mydomain, ldap:/etc/postfix/ldapmydestination.cf
mydomain = domain
myhostname = hostname.fqdn
mynetworks = 127.0.0.0/8, 192.168.4.0/24
mynetworks_style = subnet
newaliases_path = /usr/bin/newaliases
readme_directory = /usr/share/doc/packages/postfix/README_FILES
relay_domains = $mydomain
relayhost =
relocated_maps = hash:/etc/postfix/relocated
sample_directory = /usr/share/doc/packages/postfix/samples
sender_canonical_maps = hash:/etc/postfix/sender_canonical
sendmail_path = /usr/sbin/sendmail
setgid_group = maildrop
smtp_enforce_tls = no
smtp_sasl_auth_enable = no
smtp_sasl_security_options = noanonymous
smtp_tls_enforce_peername = yes
smtp_tls_note_starttls_offer = yes
smtp_tls_per_site = ldap:/etc/postfix/ldapsmtp_tls_per_site.cf
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client multi.uribl.com, \         reject_rbl_client dsn.rfc-ignorant.org, reject_rbl_client dul.dnsbl.sorbs.net, \         reject_rbl_client list.dsbl.org, reject_rbl_client sbl-xbl.spamhaus.org, \         reject_rbl_client bl.spamcop.net, reject_rbl_client dnsbl.sorbs.net, \         reject_rbl_client cbl.abuseat.org, reject_rbl_client combined.rbl.msrbl.net, \         reject_rbl_client rabl.nuclearelephant.com, ldap:/etc/postfix/ldapaccess.cf
smtpd_helo_required = yes
smtpd_helo_restrictions =
smtpd_recipient_restrictions = permit_auth_destination, permit_mynetworks,\         reject_unauth_destination, reject
smtpd_sasl_auth_enable = no
smtpd_sender_restrictions = ldap:/etc/postfix/ldapaccess.cf, reject_unknown_sender_domain
smtpd_tls_CApath = /etc/ssl/certs
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/servercerts/servercert.pem
smtpd_tls_key_file = /etc/ssl/servercerts/serverkey.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
strict_8bitmime = no
strict_rfc821_envelopes = no
transport_maps = ldap:/etc/postfix/ldaptransport_maps.cf
unknown_local_recipient_reject_code = 550
virtual_alias_domains = ldap:/etc/postfix/ldapvirtual_alias_maps.cf
virtual_alias_maps = ldap:/etc/postfix/ldaplocal_recipient_maps.cf

---

### Post by alastair on 2008-11-22
> **javierccs said:**
> 
Nov 22 17:34:23 smtpserver postfix/smtpd[18533]: warning: unknown smtpd restriction: "\"

Start with that error ...

> **javierccs said:**
> 
smtpd_client_restrictions = reject_rbl_client multi.uribl.com, \         reject_rbl_client dsn.rfc-ignorant.org, reject_rbl_client
...


and have a look in your /etc/postfix/main.cf file. Is that "\" meant to be there? See the postfix docs :

[http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

"Specify a list of restrictions, separated by commas and/or whitespace. Continue long lines by starting the next line with whitespace."

P.S. Be careful setting up mail servers - don't be an open relay.

Alastair

---

### Post by Dr Small on 2008-11-22
> **alastair said:**
> P.S. Be careful setting up mail servers - don't be an open relay.

I plan on writing a guide on securely relaying mail through postfix.

---

