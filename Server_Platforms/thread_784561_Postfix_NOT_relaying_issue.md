---
title: "Postfix NOT relaying issue"
date: 2008-05-06
forum: Server Platforms
---

### Post by JeremyLaurenson on 2008-05-06
I have been going at this for around 5 hours and need help.

I want to receive emails in using smtp over SSL and relay those to a single host, non ssl.

I can send the emails fine - my TLS, aything against LDAP etc works fine... but I get this in my syslog:

May  6 16:44:15 wwwin postfix/bounce[24487]: bounce_append_proto: flags=0x0 service=defer id=44A9687BAC org_to=jlaurens@cisco.com to=jlaurens@cisco.com off=566 dsn_org=rfc822;jlaurens@cisco.com, notif=0x0 stat=4.3.0 act=delayed why=mail transport unavailable

See below for full log..

I can telnet tot he mail host I am trying to relay to on port 25 and do the EHLO command just fine.

My postfix main.cf:


smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
smtpd_tls_cert_file = /etc/ssl/certs/wwwinclear.crt
smtpd_tls_key_file = /etc/ssl/certs/wwwinclear.key
smtpd_use_tls = yes 
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = my.fqdn.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost
relayhost = isp.smtpserver.com
mailbox_size_limit = 0100000
recipient_delimiter =
inet_interfaces = all
inet_protocols = ipv4
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,reject_unauth_destination
home_mailbox = Maildir/
smtp_tls_note_starttls_offer = yes
smtpd_tls_chain_file = /etc/ssl/certs/gd_intermediate_bundle.crt
smtpd_tls_loglevel = 4
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_auth_only = yes
debug_peer_level = 99







Log:

May  6 16:44:15 wwwin postfix/smtpd[24472]: input attribute name: (end)
May  6 16:44:15 wwwin postfix/smtpd[24472]: > jlaurens-xp[10.10.10.45]: 250 2.0.0 Ok: queued as 44A9687BAC
May  6 16:44:15 wwwin postfix/trivial-rewrite[24474]: send attr nexthop = email.cisco.com
May  6 16:44:15 wwwin postfix/trivial-rewrite[24474]: send attr recipient = [email]jlaurens@dest.com[/email]
May  6 16:44:15 wwwin postfix/trivial-rewrite[24474]: send attr flags = 4096
May  6 16:44:15 wwwin postfix/trivial-rewrite[24474]: master_notify: status 1
May  6 16:44:15 wwwin postfix/cleanup[24475]: send attr status = 0
May  6 16:44:15 wwwin postfix/cleanup[24475]: send attr reason = 
May  6 16:44:15 wwwin postfix/cleanup[24475]: master_notify: status 1
May  6 16:44:15 wwwin postfix/cleanup[24475]: connection closed
May  6 16:44:15 wwwin postfix/qmgr[24456]: start sorted recipient list
May  6 16:44:15 wwwin postfix/qmgr[24456]: qmgr_message_sort: [email]jlaurens@dest.com[/email]
May  6 16:44:15 wwwin postfix/qmgr[24456]: end sorted recipient list
May  6 16:44:15 wwwin postfix/qmgr[24456]: mail_flow_put: 1 1
May  6 16:44:15 wwwin postfix/qmgr[24456]: qmgr_transport_select: smtp
May  6 16:44:15 wwwin postfix/qmgr[24456]: qmgr_active_drain: allocate smtp
May  6 16:44:15 wwwin postfix/qmgr[24456]: connect to subsystem private/smtp: Connection refused
May  6 16:44:15 wwwin postfix/qmgr[24456]: warning: connect to transport smtp: Connection refused
May  6 16:44:15 wwwin postfix/qmgr[24456]: done incoming queue scan
May  6 16:44:15 wwwin postfix/qmgr[24456]: transport_event: smtp
May  6 16:44:15 wwwin postfix/qmgr[24456]: qmgr_transport_throttle: transport smtp: status: 4.3.0 reason: mail transport unavailable
May  6 16:44:15 wwwin postfix/qmgr[24456]: defer transport smtp: 4.3.0 mail transport unavailable
May  6 16:44:15 wwwin postfix/qmgr[24456]: defer site email.cisco.com: 4.3.0 mail transport unavailable
May  6 16:44:15 wwwin postfix/qmgr[24456]: dict_eval: const  5s
May  6 16:44:15 wwwin postfix/qmgr[24456]: qmgr_transport_create: retry concurrency 20 recipients 50
May  6 16:44:15 wwwin postfix/qmgr[24456]: qmgr_transport_select: retry
May  6 16:44:15 wwwin postfix/qmgr[24456]: qmgr_active_drain: allocate retry
May  6 16:44:15 wwwin postfix/qmgr[24456]: connect to subsystem private/retry
May  6 16:44:15 wwwin postfix/qmgr[24456]: transport_event: retry
May  6 16:44:15 wwwin postfix/qmgr[24456]: private/retry socket: wanted attribute: status
May  6 16:44:15 wwwin postfix/qmgr[24456]: input attribute name: status
May  6 16:44:15 wwwin postfix/qmgr[24456]: input attribute value: 0
May  6 16:44:15 wwwin postfix/qmgr[24456]: private/retry socket: wanted attribute: (list terminator)
May  6 16:44:15 wwwin postfix/qmgr[24456]: input attribute name: (end)
May  6 16:44:15 wwwin postfix/qmgr[24456]: qmgr_peer_select: 44A9687BAC retry 4.3.0 mail transport unavailable (1 of 5)

---

