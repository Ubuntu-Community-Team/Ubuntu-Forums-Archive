---
title: "Postfix, Dovecot, MySQL, PostfixAdmin is not working"
date: 2013-03-13
forum: Server Platforms
---

### Post by cryptodan on 2013-03-13
I am trying to configure for the first a server to be used for multiple domains to get used to hosting situations I may encounter in my job.

I have Postfix, Dovecot, MySQL, and Postfix admin configured.  However, Postfix is not handing off mail delivery to the virtual mailbox.  

I followed this howto: [http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/](http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/) with the exception of the clamav and amvisd setup.

Here is the debug information for my postfix setup:

```

Mar 13 20:23:55 andromeda postfix/smtpd[15316]: name_mask: ipv4
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: inet_addr_local: configured 2 IPv4 addresses
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: process generation: 3 (3)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: mynetworks ~? debug_peer_list
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: mynetworks ~? fast_flush_domains
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: mynetworks ~? mynetworks
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: relay_domains ~? debug_peer_list
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: relay_domains ~? fast_flush_domains
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: relay_domains ~? mynetworks
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: relay_domains ~? permit_mx_backup_networks
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: relay_domains ~? qmqpd_authorized_clients
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: relay_domains ~? smtpd_access_maps
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_list_match: relay_domains: no match
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: permit_mx_backup_networks ~? debug_peer_list
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: permit_mx_backup_networks ~? fast_flush_domains
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: permit_mx_backup_networks ~? mynetworks
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: permit_mx_backup_networks ~? permit_mx_backup_networks
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: connect to subsystem private/proxymap
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr request = open
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr table = unix:passwd.byname
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr flags = 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/proxymap socket: wanted attribute: status
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: status
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/proxymap socket: wanted attribute: flags
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: flags
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: 16
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/proxymap socket: wanted attribute: (list terminator)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: (end)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: dict_proxy_open: connect to map=unix:passwd.byname status=0 server_flags=fixed
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: dict_open: proxy:unix:passwd.byname
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: Compiled against Berkeley DB: 5.1.25?
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: Run-time linked against Berkeley DB: 5.1.25?
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: dict_open: hash:/etc/aliases
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: user = mail
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: password = hidden
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: dbname = mail
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: result_format = %s
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_int: /etc/postfix/mysql_va_maps.cf: expansion_limit = 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: query = <NULL>
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: table = alias
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: select_field = goto
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: where_field = address
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: additional_conditions = and active = '1'
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: domain = 
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_va_maps.cf: hosts = 127.0.0.1
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: dict_open: mysql:/etc/postfix/mysql_va_maps.cf
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_alias_domainaliases_maps.cf: user = mail
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_alias_domainaliases_maps.cf: password = hidden
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_alias_domainaliases_maps.cf: dbname = mail
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_alias_domainaliases_maps.cf: result_format = %s
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_int: /etc/postfix/mysql_virtual_alias_domainaliases_maps.cf: expansion_limit = 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_alias_domainaliases_maps.cf: query = SELECT goto FROM alias,alias_domain   WHERE alias_domain.alias_domain = '%d'   AND alias.address=concat('%u', '@', alias_domain.target_domain)   AND alias.active = 1
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_alias_domainaliases_maps.cf: domain = 
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_alias_domainaliases_maps.cf: hosts = 127.0.0.1
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: dict_open: mysql:/etc/postfix/mysql_virtual_alias_domainaliases_maps.cf
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: user = mail
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: password = hidden
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: dbname = mail
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: result_format = %s
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_int: /etc/postfix/mysql_vmb_maps.cf: expansion_limit = 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: query = <NULL>
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: table = mailbox
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: select_field = CONCAT(domain, '/', local_part)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: where_field = username
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: additional_conditions = and active = '1'
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: domain = 
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_vmb_maps.cf: hosts = 127.0.0.1
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: dict_open: mysql:/etc/postfix/mysql_vmb_maps.cf
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf: user = mail
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf: password = hidden
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf: dbname = mail
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf: result_format = %s
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_int: /etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf: expansion_limit = 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf: query = SELECT maildir FROM mailbox, alias_domain \  WHERE alias_domain.alias_domain = '%d' \  AND mailbox.username=concat('%u', '@', alias_domain.target_domain ) \  AND mailbox.active = 1
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf: domain = 
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: cfg_get_str: /etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf: hosts = 127.0.0.1
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: dict_open: mysql:/etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: smtpd_access_maps ~? debug_peer_list
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: smtpd_access_maps ~? fast_flush_domains
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: smtpd_access_maps ~? mynetworks
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: smtpd_access_maps ~? permit_mx_backup_networks
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: smtpd_access_maps ~? qmqpd_authorized_clients
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: smtpd_access_maps ~? smtpd_access_maps
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: unknown_helo_hostname_tempfail_action = defer_if_permit
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: unknown_address_tempfail_action = defer_if_permit
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: unverified_recipient_tempfail_action = defer_if_permit
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: unverified_sender_tempfail_action = defer_if_permit
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: name_mask: 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: auto_clnt_create: transport=local endpoint=private/tlsmgr
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: auto_clnt_open: connected to private/tlsmgr
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr request = seed
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr size = 32
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/tlsmgr: wanted attribute: status
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: status
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/tlsmgr: wanted attribute: seed
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: seed
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: AHVrzbFVvc2OBJm0YrMwfr0jnTbg7Iomx767MU6gr+4=
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/tlsmgr: wanted attribute: (list terminator)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: (end)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr request = policy
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr cache_type = smtpd
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/tlsmgr: wanted attribute: status
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: status
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/tlsmgr: wanted attribute: cachable
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: cachable
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: 1
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/tlsmgr: wanted attribute: (list terminator)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: (end)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: fast_flush_domains ~? debug_peer_list
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_string: fast_flush_domains ~? fast_flush_domains
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: auto_clnt_create: transport=local endpoint=private/anvil
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: connection established
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: master_notify: status 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: name_mask: resource
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: name_mask: software
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: connect from mail-ve0-f174.google.com[209.85.128.174]
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_list_match: mail-ve0-f174.google.com: no match
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_list_match: 209.85.128.174: no match
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_list_match: mail-ve0-f174.google.com: no match
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_list_match: 209.85.128.174: no match
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: smtp_stream_setup: maxtime=300 enable_deadline=0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_hostname: mail-ve0-f174.google.com ~? 127.0.0.0/8
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_hostaddr: 209.85.128.174 ~? 127.0.0.0/8
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_list_match: mail-ve0-f174.google.com: no match
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_list_match: 209.85.128.174: no match
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: auto_clnt_open: connected to private/anvil
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr request = connect
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr ident = smtp:209.85.128.174
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/anvil: wanted attribute: status
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: status
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/anvil: wanted attribute: count
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: count
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: 1
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/anvil: wanted attribute: rate
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: rate
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: 1
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/anvil: wanted attribute: (list terminator)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: (end)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: report connect to all milters
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: "j"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: result "andromeda.home"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: "{daemon_name}"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: result "andromeda.home"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: "v"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: result "Postfix 2.9.6"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_connect: non-protocol events for protocol version 6: 
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_connect: transport=inet endpoint=127.0.0.1:8891
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: trying... [127.0.0.1]
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: vstream_tweak_tcp: TCP_MAXSEG 16384
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_connect: my_version=0x6
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_connect: my_actions=0x1ff SMFIF_ADDHDRS SMFIF_CHGBODY SMFIF_ADDRCPT SMFIF_DELRCPT SMFIF_CHGHDRS SMFIF_QUARANTINE SMFIF_CHGFROM SMFIF_ADDRCPT_PAR SMFIF_SETSYMLIST
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_connect: my_events=0x1fffff SMFIP_NOCONNECT SMFIP_NOHELO SMFIP_NOMAIL SMFIP_NORCPT SMFIP_NOBODY SMFIP_NOHDRS SMFIP_NOEOH SMFIP_NR_HDR SMFIP_NOUNKNOWN SMFIP_NODATA SMFIP_SKIP SMFIP_RCPT_REJ SMFIP_NR_CONN SMFIP_NR_HELO SMFIP_NR_MAIL SMFIP_NR_RCPT SMFIP_NR_DATA SMFIP_NR_UNKN SMFIP_NR_EOH SMFIP_NR_BODY SMFIP_HDR_LEADSPC
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_connect: milter inet:127.0.0.1:8891 version 6
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_connect: events SMFIP_NOHELO SMFIP_NOUNKNOWN SMFIP_NODATA SMFIP_SKIP SMFIP_HDR_LEADSPC
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_connect: requests SMFIF_ADDHDRS SMFIF_CHGHDRS SMFIF_SETSYMLIST
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_conn_event: milter inet:127.0.0.1:8891: connect mail-ve0-f174.google.com/209.85.128.174
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: event: SMFIC_CONNECT; macros: j=andromeda.home {daemon_name}=andromeda.home v=Postfix 2.9.6
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: reply: SMFIR_CONTINUE data 0 bytes
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 220 andromeda.home ESMTP Postfix (Ubuntu)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: < mail-ve0-f174.google.com[209.85.128.174]: EHLO mail-ve0-f174.google.com
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: report helo to all milters
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: "{tls_version}"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: "{cipher}"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: "{cipher_bits}"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: "{cert_subject}"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter_macro_lookup: "{cert_issuer}"
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_helo_event: milter inet:127.0.0.1:8891: helo mail-ve0-f174.google.com
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: event: SMFIC_HELO; macros: (none)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: skipping event SMFIC_HELO for milter inet:127.0.0.1:8891
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_list_match: mail-ve0-f174.google.com: no match
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: match_list_match: 209.85.128.174: no match
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 250-andromeda.home
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 250-PIPELINING
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 250-SIZE 10240000
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 250-VRFY
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 250-ETRN
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 250-STARTTLS
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 250-ENHANCEDSTATUSCODES
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 250-8BITMIME
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 250 DSN
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: < mail-ve0-f174.google.com[209.85.128.174]: STARTTLS
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: query milter states for other event
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_other_event: milter inet:127.0.0.1:8891
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: > mail-ve0-f174.google.com[209.85.128.174]: 220 2.0.0 Ready to start TLS
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: abort all milters
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: milter8_abort: abort milter inet:127.0.0.1:8891
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr request = seed
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: send attr size = 32
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/tlsmgr: wanted attribute: status
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: status
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: 0
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/tlsmgr: wanted attribute: seed
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: seed
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute value: Yq65+voc3LQNVdBh7hwpJK7T0kNDyGKblUpQTyAY8oA=
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: private/tlsmgr: wanted attribute: (list terminator)
Mar 13 20:23:55 andromeda postfix/smtpd[15316]: input attribute name: (end)
Mar 13 20:23:55 andromeda postfix/cleanup[15325]: D43E610006A: message-id=<CADUOTo1h8zkNH-Pi-xpZ03Ko+n1_GqbhEdW23MN-npSYVyjYPA@mail.gmail.com>
Mar 13 20:23:55 andromeda opendkim[28129]: D43E610006A: mail-ve0-f174.google.com [209.85.128.174] not internal
Mar 13 20:23:55 andromeda opendkim[28129]: D43E610006A: not authenticated
Mar 13 20:23:55 andromeda opendkim[28129]: D43E610006A: no signing domain match for 'gmail.com'
Mar 13 20:23:55 andromeda opendkim[28129]: D43E610006A: no signing subdomain match for 'gmail.com'
Mar 13 20:23:55 andromeda postfix/qmgr[15301]: D43E610006A: from=<cryptodan@gmail.com>, size=6398, nrcpt=1 (queue active)
Mar 13 20:23:55 andromeda postfix/local[15327]: D43E610006A: to=<cryptodan@cryptodan.net>, relay=local, delay=0.16, delays=0.15/0.01/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Mar 13 20:23:55 andromeda postfix/qmgr[15301]: D43E610006A: removed
Mar 13 20:24:01 andromeda postfix/smtpd[15316]: proxymap stream disconnect
Mar 13 20:24:01 andromeda postfix/smtpd[15316]: auto_clnt_close: disconnect private/tlsmgr stream
Mar 13 20:24:01 andromeda postfix/smtpd[15316]: rewrite stream disconnect
Mar 13 20:25:35 andromeda postfix/smtpd[15316]: idle timeout -- exiting
Mar 13 20:27:12 andromeda dovecot: auth-worker: mysql(localhost): Connected to database mail
Mar 13 20:27:12 andromeda dovecot: pop3-login: Login: user=<cryptodan@cryptodan.net>, method=PLAIN, rip=96.244.76.114, lip=192.168.1.8, mpid=15341, TLS
Mar 13 20:27:12 andromeda dovecot: pop3(cryptodan@cryptodan.net): Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=0
Mar 13 20:27:15 andromeda postfix/anvil[15319]: statistics: max connection rate 1/60s for (smtp:209.85.128.174) at Mar 14 00:23:55
Mar 13 20:27:15 andromeda postfix/anvil[15319]: statistics: max connection count 1 for (smtp:209.85.128.174) at Mar 14 00:23:55
Mar 13 20:27:15 andromeda postfix/anvil[15319]: statistics: max cache size 1 at Mar 14 00:23:55

```

Here is the output of postconf -d:

```

root@andromeda:/etc/postfix# postconf -d
2bounce_notice_recipient = postmaster
access_map_defer_code = 450
access_map_reject_code = 554
address_verify_cache_cleanup_interval = 12h
address_verify_default_transport = $default_transport
address_verify_local_transport = $local_transport
address_verify_map = btree:$data_directory/verify_cache
address_verify_negative_cache = yes
address_verify_negative_expire_time = 3d
address_verify_negative_refresh_time = 3h
address_verify_poll_count = ${stress?1}${stress:3}
address_verify_poll_delay = 3s
address_verify_positive_expire_time = 31d
address_verify_positive_refresh_time = 7d
address_verify_relay_transport = $relay_transport
address_verify_relayhost = $relayhost
address_verify_sender = $double_bounce_sender
address_verify_sender_dependent_default_transport_maps = $sender_dependent_default_transport_maps
address_verify_sender_dependent_relayhost_maps = $sender_dependent_relayhost_maps
address_verify_sender_ttl = 0s
address_verify_service_name = verify
address_verify_transport_maps = $transport_maps
address_verify_virtual_transport = $virtual_transport
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases, nis:mail.aliases
allow_mail_to_commands = alias, forward
allow_mail_to_files = alias, forward
allow_min_user = no
allow_percent_hack = yes
allow_untrusted_routing = no
alternate_config_directories =
always_add_missing_headers = no
always_bcc =
anvil_rate_time_unit = 60s
anvil_status_update_time = 600s
append_at_myorigin = yes
append_dot_mydomain = yes
application_event_drain_time = 100s
authorized_flush_users = static:anyone
authorized_mailq_users = static:anyone
authorized_submit_users = static:anyone
backwards_bounce_logfile_compatibility = yes
berkeley_db_create_buffer_size = 16777216
berkeley_db_read_buffer_size = 131072
best_mx_transport =
biff = yes
body_checks =
body_checks_size_limit = 51200
bounce_notice_recipient = postmaster
bounce_queue_lifetime = 5d
bounce_service_name = bounce
bounce_size_limit = 50000
bounce_template_file =
broken_sasl_auth_clients = no
bsmtp_delivery_slot_cost = $default_delivery_slot_cost
bsmtp_delivery_slot_discount = $default_delivery_slot_discount
bsmtp_delivery_slot_loan = $default_delivery_slot_loan
bsmtp_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
bsmtp_destination_concurrency_limit = $default_destination_concurrency_limit
bsmtp_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
bsmtp_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
bsmtp_destination_rate_delay = $default_destination_rate_delay
bsmtp_destination_recipient_limit = $default_destination_recipient_limit
bsmtp_extra_recipient_limit = $default_extra_recipient_limit
bsmtp_initial_destination_concurrency = $initial_destination_concurrency
bsmtp_minimum_delivery_slots = $default_minimum_delivery_slots
bsmtp_recipient_limit = $default_recipient_limit
bsmtp_recipient_refill_delay = $default_recipient_refill_delay
bsmtp_recipient_refill_limit = $default_recipient_refill_limit
bsmtp_time_limit = $command_time_limit
canonical_classes = envelope_sender, envelope_recipient, header_sender, header_recipient
canonical_maps =
cleanup_service_name = cleanup
command_directory = /usr/sbin
command_execution_directory =
command_expansion_filter = 1234567890!@%-_=+:,./abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
command_time_limit = 1000s
config_directory = /etc/postfix
connection_cache_protocol_timeout = 5s
connection_cache_service_name = scache
connection_cache_status_update_time = 600s
connection_cache_ttl_limit = 2s
content_filter =
cyrus_sasl_config_path =
daemon_directory = /usr/lib/postfix
daemon_table_open_error_is_fatal = no
daemon_timeout = 18000s
data_directory = /var/lib/postfix
debug_peer_level = 2
debug_peer_list =
debugger_command =
default_database_type = hash
default_delivery_slot_cost = 5
default_delivery_slot_discount = 50
default_delivery_slot_loan = 3
default_destination_concurrency_failed_cohort_limit = 1
default_destination_concurrency_limit = 20
default_destination_concurrency_negative_feedback = 1
default_destination_concurrency_positive_feedback = 1
default_destination_rate_delay = 0s
default_destination_recipient_limit = 50
default_extra_recipient_limit = 1000
default_filter_nexthop =
default_minimum_delivery_slots = 3
default_privs = nobody
default_process_limit = 100
default_rbl_reply = $rbl_code Service unavailable; $rbl_class [$rbl_what] blocked using $rbl_domain${rbl_reason?; $rbl_reason}
default_recipient_limit = 20000
default_recipient_refill_delay = 5s
default_recipient_refill_limit = 100
default_transport = smtp
default_verp_delimiters = +=
defer_code = 450
defer_service_name = defer
defer_transports =
delay_logging_resolution_limit = 2
delay_notice_recipient = postmaster
delay_warning_time = 0h
deliver_lock_attempts = 20
deliver_lock_delay = 1s
destination_concurrency_feedback_debug = no
detect_8bit_encoding_header = yes
disable_dns_lookups = no
disable_mime_input_processing = no
disable_mime_output_conversion = no
disable_verp_bounces = no
disable_vrfy_command = no
dnsblog_reply_delay = 0s
dnsblog_service_name = dnsblog
dont_remove = 0
double_bounce_sender = double-bounce
dovecot_delivery_slot_cost = $default_delivery_slot_cost
dovecot_delivery_slot_discount = $default_delivery_slot_discount
dovecot_delivery_slot_loan = $default_delivery_slot_loan
dovecot_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
dovecot_destination_concurrency_limit = $default_destination_concurrency_limit
dovecot_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
dovecot_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
dovecot_destination_rate_delay = $default_destination_rate_delay
dovecot_destination_recipient_limit = $default_destination_recipient_limit
dovecot_extra_recipient_limit = $default_extra_recipient_limit
dovecot_initial_destination_concurrency = $initial_destination_concurrency
dovecot_minimum_delivery_slots = $default_minimum_delivery_slots
dovecot_recipient_limit = $default_recipient_limit
dovecot_recipient_refill_delay = $default_recipient_refill_delay
dovecot_recipient_refill_limit = $default_recipient_refill_limit
dovecot_time_limit = $command_time_limit
duplicate_filter_limit = 1000
empty_address_default_transport_maps_lookup_key = <>
empty_address_recipient = MAILER-DAEMON
empty_address_relayhost_maps_lookup_key = <>
enable_long_queue_ids = no
enable_original_recipient = yes
error_delivery_slot_cost = $default_delivery_slot_cost
error_delivery_slot_discount = $default_delivery_slot_discount
error_delivery_slot_loan = $default_delivery_slot_loan
error_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
error_destination_concurrency_limit = $default_destination_concurrency_limit
error_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
error_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
error_destination_rate_delay = $default_destination_rate_delay
error_destination_recipient_limit = $default_destination_recipient_limit
error_extra_recipient_limit = $default_extra_recipient_limit
error_initial_destination_concurrency = $initial_destination_concurrency
error_minimum_delivery_slots = $default_minimum_delivery_slots
error_notice_recipient = postmaster
error_recipient_limit = $default_recipient_limit
error_recipient_refill_delay = $default_recipient_refill_delay
error_recipient_refill_limit = $default_recipient_refill_limit
error_service_name = error
execution_directory_expansion_filter = 1234567890!@%-_=+:,./abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
expand_owner_alias = no
export_environment = TZ MAIL_CONFIG LANG
fallback_transport =
fallback_transport_maps =
fast_flush_domains = $relay_domains
fast_flush_purge_time = 7d
fast_flush_refresh_time = 12h
fault_injection_code = 0
flush_service_name = flush
fork_attempts = 5
fork_delay = 1s
forward_expansion_filter = 1234567890!@%-_=+:,./abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
forward_path = $home/.forward${recipient_delimiter}${extension}, $home/.forward
frozen_delivered_to = yes
hash_queue_depth = 1
hash_queue_names = deferred, defer
header_address_token_limit = 10240
header_checks =
header_size_limit = 102400
helpful_warnings = yes
home_mailbox =
hopcount_limit = 50
html_directory = no
ifmail_delivery_slot_cost = $default_delivery_slot_cost
ifmail_delivery_slot_discount = $default_delivery_slot_discount
ifmail_delivery_slot_loan = $default_delivery_slot_loan
ifmail_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
ifmail_destination_concurrency_limit = $default_destination_concurrency_limit
ifmail_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
ifmail_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
ifmail_destination_rate_delay = $default_destination_rate_delay
ifmail_destination_recipient_limit = $default_destination_recipient_limit
ifmail_extra_recipient_limit = $default_extra_recipient_limit
ifmail_initial_destination_concurrency = $initial_destination_concurrency
ifmail_minimum_delivery_slots = $default_minimum_delivery_slots
ifmail_recipient_limit = $default_recipient_limit
ifmail_recipient_refill_delay = $default_recipient_refill_delay
ifmail_recipient_refill_limit = $default_recipient_refill_limit
ifmail_time_limit = $command_time_limit
ignore_mx_lookup_error = no
import_environment = MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
in_flow_delay = 1s
inet_interfaces = all
inet_protocols = all
initial_destination_concurrency = 5
internal_mail_filter_classes =
invalid_hostname_reject_code = 501
ipc_idle = 5s
ipc_timeout = 3600s
ipc_ttl = 1000s
line_length_limit = 2048
lmtp_address_preference = any
lmtp_assume_final = no
lmtp_bind_address =
lmtp_bind_address6 =
lmtp_body_checks =
lmtp_cname_overrides_servername = no
lmtp_connect_timeout = 0s
lmtp_connection_cache_destinations =
lmtp_connection_cache_on_demand = yes
lmtp_connection_cache_time_limit = 2s
lmtp_connection_reuse_time_limit = 300s
lmtp_data_done_timeout = 600s
lmtp_data_init_timeout = 120s
lmtp_data_xfer_timeout = 180s
lmtp_defer_if_no_mx_address_found = no
lmtp_delivery_slot_cost = $default_delivery_slot_cost
lmtp_delivery_slot_discount = $default_delivery_slot_discount
lmtp_delivery_slot_loan = $default_delivery_slot_loan
lmtp_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
lmtp_destination_concurrency_limit = $default_destination_concurrency_limit
lmtp_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
lmtp_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
lmtp_destination_rate_delay = $default_destination_rate_delay
lmtp_destination_recipient_limit = $default_destination_recipient_limit
lmtp_discard_lhlo_keyword_address_maps =
lmtp_discard_lhlo_keywords =
lmtp_dns_resolver_options =
lmtp_enforce_tls = no
lmtp_extra_recipient_limit = $default_extra_recipient_limit
lmtp_generic_maps =
lmtp_header_checks =
lmtp_host_lookup = dns
lmtp_initial_destination_concurrency = $initial_destination_concurrency
lmtp_lhlo_name = $myhostname
lmtp_lhlo_timeout = 300s
lmtp_line_length_limit = 998
lmtp_mail_timeout = 300s
lmtp_mime_header_checks =
lmtp_minimum_delivery_slots = $default_minimum_delivery_slots
lmtp_mx_address_limit = 5
lmtp_mx_session_limit = 2
lmtp_nested_header_checks =
lmtp_per_record_deadline = no
lmtp_pix_workaround_delay_time = 10s
lmtp_pix_workaround_maps =
lmtp_pix_workaround_threshold_time = 500s
lmtp_pix_workarounds = disable_esmtp,delay_dotcrlf
lmtp_quit_timeout = 300s
lmtp_quote_rfc821_envelope = yes
lmtp_randomize_addresses = yes
lmtp_rcpt_timeout = 300s
lmtp_recipient_limit = $default_recipient_limit
lmtp_recipient_refill_delay = $default_recipient_refill_delay
lmtp_recipient_refill_limit = $default_recipient_refill_limit
lmtp_reply_filter =
lmtp_rset_timeout = 20s
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
lmtp_send_dummy_mail_auth = no
lmtp_send_xforward_command = no
lmtp_sender_dependent_authentication = no
lmtp_skip_5xx_greeting = yes
lmtp_skip_quit_response = no
lmtp_starttls_timeout = 300s
lmtp_tcp_port = 24
lmtp_tls_CAfile =
lmtp_tls_CApath =
lmtp_tls_block_early_mail_reply = no
lmtp_tls_cert_file =
lmtp_tls_ciphers = export
lmtp_tls_dcert_file =
lmtp_tls_dkey_file = $lmtp_tls_dcert_file
lmtp_tls_eccert_file =
lmtp_tls_eckey_file = $lmtp_tls_eccert_file
lmtp_tls_enforce_peername = yes
lmtp_tls_exclude_ciphers =
lmtp_tls_fingerprint_cert_match =
lmtp_tls_fingerprint_digest = md5
lmtp_tls_key_file = $lmtp_tls_cert_file
lmtp_tls_loglevel = 0
lmtp_tls_mandatory_ciphers = medium
lmtp_tls_mandatory_exclude_ciphers =
lmtp_tls_mandatory_protocols = !SSLv2
lmtp_tls_note_starttls_offer = no
lmtp_tls_per_site =
lmtp_tls_policy_maps =
lmtp_tls_protocols = !SSLv2
lmtp_tls_scert_verifydepth = 9
lmtp_tls_secure_cert_match = nexthop
lmtp_tls_security_level =
lmtp_tls_session_cache_database =
lmtp_tls_session_cache_timeout = 3600s
lmtp_tls_verify_cert_match = hostname
lmtp_use_tls = no
lmtp_xforward_timeout = 300s
local_command_shell =
local_delivery_slot_cost = $default_delivery_slot_cost
local_delivery_slot_discount = $default_delivery_slot_discount
local_delivery_slot_loan = $default_delivery_slot_loan
local_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
local_destination_concurrency_limit = 2
local_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
local_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
local_destination_rate_delay = $default_destination_rate_delay
local_destination_recipient_limit = 1
local_extra_recipient_limit = $default_extra_recipient_limit
local_header_rewrite_clients = permit_inet_interfaces
local_initial_destination_concurrency = $initial_destination_concurrency
local_minimum_delivery_slots = $default_minimum_delivery_slots
local_recipient_limit = $default_recipient_limit
local_recipient_maps = proxy:unix:passwd.byname $alias_maps
local_recipient_refill_delay = $default_recipient_refill_delay
local_recipient_refill_limit = $default_recipient_refill_limit
local_transport = local:$myhostname
luser_relay =
mail_name = Postfix
mail_owner = postfix
mail_release_date = 20130203
mail_spool_directory = /var/mail
mail_version = 2.9.6
mailbox_command =
mailbox_command_maps =
mailbox_delivery_lock = fcntl, dotlock
mailbox_size_limit = 51200000
mailbox_transport =
mailbox_transport_maps =
maildrop_delivery_slot_cost = $default_delivery_slot_cost
maildrop_delivery_slot_discount = $default_delivery_slot_discount
maildrop_delivery_slot_loan = $default_delivery_slot_loan
maildrop_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
maildrop_destination_concurrency_limit = $default_destination_concurrency_limit
maildrop_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
maildrop_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
maildrop_destination_rate_delay = $default_destination_rate_delay
maildrop_destination_recipient_limit = $default_destination_recipient_limit
maildrop_extra_recipient_limit = $default_extra_recipient_limit
maildrop_initial_destination_concurrency = $initial_destination_concurrency
maildrop_minimum_delivery_slots = $default_minimum_delivery_slots
maildrop_recipient_limit = $default_recipient_limit
maildrop_recipient_refill_delay = $default_recipient_refill_delay
maildrop_recipient_refill_limit = $default_recipient_refill_limit
maildrop_time_limit = $command_time_limit
mailman_delivery_slot_cost = $default_delivery_slot_cost
mailman_delivery_slot_discount = $default_delivery_slot_discount
mailman_delivery_slot_loan = $default_delivery_slot_loan
mailman_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
mailman_destination_concurrency_limit = $default_destination_concurrency_limit
mailman_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
mailman_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
mailman_destination_rate_delay = $default_destination_rate_delay
mailman_destination_recipient_limit = $default_destination_recipient_limit
mailman_extra_recipient_limit = $default_extra_recipient_limit
mailman_initial_destination_concurrency = $initial_destination_concurrency
mailman_minimum_delivery_slots = $default_minimum_delivery_slots
mailman_recipient_limit = $default_recipient_limit
mailman_recipient_refill_delay = $default_recipient_refill_delay
mailman_recipient_refill_limit = $default_recipient_refill_limit
mailman_time_limit = $command_time_limit
mailq_path = /usr/bin/mailq
manpage_directory = /usr/share/man
maps_rbl_domains =
maps_rbl_reject_code = 554
masquerade_classes = envelope_sender, header_sender, header_recipient
masquerade_domains =
masquerade_exceptions =
master_service_disable =
max_idle = 100s
max_use = 100
maximal_backoff_time = 4000s
maximal_queue_lifetime = 5d
message_reject_characters =
message_size_limit = 10240000
message_strip_characters =
milter_command_timeout = 30s
milter_connect_macros = j {daemon_name} v
milter_connect_timeout = 30s
milter_content_timeout = 300s
milter_data_macros = i
milter_default_action = tempfail
milter_end_of_data_macros = i
milter_end_of_header_macros = i
milter_header_checks =
milter_helo_macros = {tls_version} {cipher} {cipher_bits} {cert_subject} {cert_issuer}
milter_macro_daemon_name = $myhostname
milter_macro_v = $mail_name $mail_version
milter_mail_macros = i {auth_type} {auth_authen} {auth_author} {mail_addr} {mail_host} {mail_mailer}
milter_protocol = 6
milter_rcpt_macros = i {rcpt_addr} {rcpt_host} {rcpt_mailer}
milter_unknown_command_macros =
mime_boundary_length_limit = 2048
mime_header_checks = $header_checks
mime_nesting_limit = 100
minimal_backoff_time = 300s
multi_instance_directories =
multi_instance_enable = no
multi_instance_group =
multi_instance_name =
multi_instance_wrapper =
multi_recipient_bounce_reject_code = 550
mydestination = $myhostname, localhost.$mydomain, localhost
mydomain = localdomain
myhostname = andromeda.home
mynetworks = 127.0.0.0/8 192.168.1.0/24
mynetworks_style = subnet
myorigin = $myhostname
nested_header_checks = $header_checks
newaliases_path = /usr/bin/newaliases
non_fqdn_reject_code = 504
non_smtpd_milters =
notify_classes = resource, software
owner_request_special = yes
parent_domain_matches_subdomains = debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,smtpd_access_maps
permit_mx_backup_networks =
pickup_service_name = pickup
plaintext_reject_code = 450
postmulti_control_commands = reload flush
postmulti_start_commands = start
postmulti_stop_commands = stop abort drain quick-stop
postscreen_access_list = permit_mynetworks
postscreen_bare_newline_action = ignore
postscreen_bare_newline_enable = no
postscreen_bare_newline_ttl = 30d
postscreen_blacklist_action = ignore
postscreen_cache_cleanup_interval = 12h
postscreen_cache_map = btree:$data_directory/postscreen_cache
postscreen_cache_retention_time = 7d
postscreen_client_connection_count_limit = $smtpd_client_connection_count_limit
postscreen_command_count_limit = 20
postscreen_command_filter =
postscreen_command_time_limit = ${stress?10}${stress:300}s
postscreen_disable_vrfy_command = $disable_vrfy_command
postscreen_discard_ehlo_keyword_address_maps = $smtpd_discard_ehlo_keyword_address_maps
postscreen_discard_ehlo_keywords = $smtpd_discard_ehlo_keywords
postscreen_dnsbl_action = ignore
postscreen_dnsbl_reply_map =
postscreen_dnsbl_sites =
postscreen_dnsbl_threshold = 1
postscreen_dnsbl_ttl = 1h
postscreen_enforce_tls = $smtpd_enforce_tls
postscreen_expansion_filter = $smtpd_expansion_filter
postscreen_forbidden_commands = $smtpd_forbidden_commands
postscreen_greet_action = ignore
postscreen_greet_banner = $smtpd_banner
postscreen_greet_ttl = 1d
postscreen_greet_wait = ${stress?2}${stress:6}s
postscreen_helo_required = $smtpd_helo_required
postscreen_non_smtp_command_action = drop
postscreen_non_smtp_command_enable = no
postscreen_non_smtp_command_ttl = 30d
postscreen_pipelining_action = enforce
postscreen_pipelining_enable = no
postscreen_pipelining_ttl = 30d
postscreen_post_queue_limit = $default_process_limit
postscreen_pre_queue_limit = $default_process_limit
postscreen_reject_footer = $smtpd_reject_footer
postscreen_tls_security_level = $smtpd_tls_security_level
postscreen_use_tls = $smtpd_use_tls
postscreen_watchdog_timeout = 10s
postscreen_whitelist_interfaces = static:all
prepend_delivered_header = command, file, forward
process_id_directory = pid
propagate_unmatched_extensions = canonical, virtual
proxy_interfaces =
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $sender_bcc_maps $recipient_bcc_maps $smtp_generic_maps $lmtp_generic_maps $alias_maps
proxy_write_maps = $smtp_sasl_auth_cache_name $lmtp_sasl_auth_cache_name $address_verify_map $postscreen_cache_map
proxymap_service_name = proxymap
proxywrite_service_name = proxywrite
qmgr_clog_warn_time = 300s
qmgr_daemon_timeout = 1000s
qmgr_fudge_factor = 100
qmgr_ipc_timeout = 60s
qmgr_message_active_limit = 20000
qmgr_message_recipient_limit = 20000
qmgr_message_recipient_minimum = 10
qmqpd_authorized_clients =
qmqpd_client_port_logging = no
qmqpd_error_delay = 1s
qmqpd_timeout = 300s
queue_directory = /var/spool/postfix
queue_file_attribute_count_limit = 100
queue_minfree = 0
queue_run_delay = 300s
queue_service_name = qmgr
rbl_reply_maps =
readme_directory = /usr/share/doc/postfix
receive_override_options =
recipient_bcc_maps =
recipient_canonical_classes = envelope_recipient, header_recipient
recipient_canonical_maps =
recipient_delimiter =
reject_code = 554
reject_tempfail_action = defer_if_permit
relay_clientcerts =
relay_delivery_slot_cost = $default_delivery_slot_cost
relay_delivery_slot_discount = $default_delivery_slot_discount
relay_delivery_slot_loan = $default_delivery_slot_loan
relay_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
relay_destination_concurrency_limit = $default_destination_concurrency_limit
relay_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
relay_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
relay_destination_rate_delay = $default_destination_rate_delay
relay_destination_recipient_limit = $default_destination_recipient_limit
relay_domains = $mydestination
relay_domains_reject_code = 554
relay_extra_recipient_limit = $default_extra_recipient_limit
relay_initial_destination_concurrency = $initial_destination_concurrency
relay_minimum_delivery_slots = $default_minimum_delivery_slots
relay_recipient_limit = $default_recipient_limit
relay_recipient_maps =
relay_recipient_refill_delay = $default_recipient_refill_delay
relay_recipient_refill_limit = $default_recipient_refill_limit
relay_transport = relay
relayhost =
relocated_maps =
remote_header_rewrite_domain =
require_home_directory = no
reset_owner_alias = no
resolve_dequoted_address = yes
resolve_null_domain = no
resolve_numeric_domain = no
retry_delivery_slot_cost = $default_delivery_slot_cost
retry_delivery_slot_discount = $default_delivery_slot_discount
retry_delivery_slot_loan = $default_delivery_slot_loan
retry_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
retry_destination_concurrency_limit = $default_destination_concurrency_limit
retry_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
retry_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
retry_destination_rate_delay = $default_destination_rate_delay
retry_destination_recipient_limit = $default_destination_recipient_limit
retry_extra_recipient_limit = $default_extra_recipient_limit
retry_initial_destination_concurrency = $initial_destination_concurrency
retry_minimum_delivery_slots = $default_minimum_delivery_slots
retry_recipient_limit = $default_recipient_limit
retry_recipient_refill_delay = $default_recipient_refill_delay
retry_recipient_refill_limit = $default_recipient_refill_limit
rewrite_service_name = rewrite
sample_directory = /usr/share/doc/postfix/examples
scalemail-backend_delivery_slot_cost = $default_delivery_slot_cost
scalemail-backend_delivery_slot_discount = $default_delivery_slot_discount
scalemail-backend_delivery_slot_loan = $default_delivery_slot_loan
scalemail-backend_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
scalemail-backend_destination_concurrency_limit = $default_destination_concurrency_limit
scalemail-backend_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
scalemail-backend_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
scalemail-backend_destination_rate_delay = $default_destination_rate_delay
scalemail-backend_destination_recipient_limit = $default_destination_recipient_limit
scalemail-backend_extra_recipient_limit = $default_extra_recipient_limit
scalemail-backend_initial_destination_concurrency = $initial_destination_concurrency
scalemail-backend_minimum_delivery_slots = $default_minimum_delivery_slots
scalemail-backend_recipient_limit = $default_recipient_limit
scalemail-backend_recipient_refill_delay = $default_recipient_refill_delay
scalemail-backend_recipient_refill_limit = $default_recipient_refill_limit
scalemail-backend_time_limit = $command_time_limit
send_cyrus_sasl_authzid = no
sender_bcc_maps =
sender_canonical_classes = envelope_sender, header_sender
sender_canonical_maps =
sender_dependent_default_transport_maps =
sender_dependent_relayhost_maps =
sendmail_fix_line_endings = always
sendmail_path = /usr/sbin/sendmail
service_throttle_time = 60s
setgid_group = postdrop
show_user_unknown_table_name = yes
showq_service_name = showq
smtp_address_preference = any
smtp_always_send_ehlo = yes
smtp_bind_address =
smtp_bind_address6 =
smtp_body_checks =
smtp_cname_overrides_servername = no
smtp_connect_timeout = 30s
smtp_connection_cache_destinations =
smtp_connection_cache_on_demand = yes
smtp_connection_cache_time_limit = 2s
smtp_connection_reuse_time_limit = 300s
smtp_data_done_timeout = 600s
smtp_data_init_timeout = 120s
smtp_data_xfer_timeout = 180s
smtp_defer_if_no_mx_address_found = no
smtp_delivery_slot_cost = $default_delivery_slot_cost
smtp_delivery_slot_discount = $default_delivery_slot_discount
smtp_delivery_slot_loan = $default_delivery_slot_loan
smtp_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
smtp_destination_concurrency_limit = $default_destination_concurrency_limit
smtp_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
smtp_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
smtp_destination_rate_delay = $default_destination_rate_delay
smtp_destination_recipient_limit = $default_destination_recipient_limit
smtp_discard_ehlo_keyword_address_maps =
smtp_discard_ehlo_keywords =
smtp_dns_resolver_options =
smtp_enforce_tls = no
smtp_extra_recipient_limit = $default_extra_recipient_limit
smtp_fallback_relay = $fallback_relay
smtp_generic_maps =
smtp_header_checks =
smtp_helo_name = $myhostname
smtp_helo_timeout = 300s
smtp_host_lookup = dns
smtp_initial_destination_concurrency = $initial_destination_concurrency
smtp_line_length_limit = 998
smtp_mail_timeout = 300s
smtp_mime_header_checks =
smtp_minimum_delivery_slots = $default_minimum_delivery_slots
smtp_mx_address_limit = 5
smtp_mx_session_limit = 2
smtp_nested_header_checks =
smtp_never_send_ehlo = no
smtp_per_record_deadline = no
smtp_pix_workaround_delay_time = 10s
smtp_pix_workaround_maps =
smtp_pix_workaround_threshold_time = 500s
smtp_pix_workarounds = disable_esmtp,delay_dotcrlf
smtp_quit_timeout = 300s
smtp_quote_rfc821_envelope = yes
smtp_randomize_addresses = yes
smtp_rcpt_timeout = 300s
smtp_recipient_limit = $default_recipient_limit
smtp_recipient_refill_delay = $default_recipient_refill_delay
smtp_recipient_refill_limit = $default_recipient_refill_limit
smtp_reply_filter =
smtp_rset_timeout = 20s
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
smtp_send_dummy_mail_auth = no
smtp_send_xforward_command = no
smtp_sender_dependent_authentication = no
smtp_skip_5xx_greeting = yes
smtp_skip_quit_response = yes
smtp_starttls_timeout = 300s
smtp_tls_CAfile =
smtp_tls_CApath =
smtp_tls_block_early_mail_reply = no
smtp_tls_cert_file =
smtp_tls_ciphers = export
smtp_tls_dcert_file =
smtp_tls_dkey_file = $smtp_tls_dcert_file
smtp_tls_eccert_file =
smtp_tls_eckey_file = $smtp_tls_eccert_file
smtp_tls_enforce_peername = yes
smtp_tls_exclude_ciphers =
smtp_tls_fingerprint_cert_match =
smtp_tls_fingerprint_digest = md5
smtp_tls_key_file = $smtp_tls_cert_file
smtp_tls_loglevel = 0
smtp_tls_mandatory_ciphers = medium
smtp_tls_mandatory_exclude_ciphers =
smtp_tls_mandatory_protocols = !SSLv2
smtp_tls_note_starttls_offer = no
smtp_tls_per_site =
smtp_tls_policy_maps =
smtp_tls_protocols = !SSLv2
smtp_tls_scert_verifydepth = 9
smtp_tls_secure_cert_match = nexthop, dot-nexthop
smtp_tls_security_level =
smtp_tls_session_cache_database =
smtp_tls_session_cache_timeout = 3600s
smtp_tls_verify_cert_match = hostname
smtp_use_tls = no
smtp_xforward_timeout = 300s
smtpd_authorized_verp_clients = $authorized_verp_clients
smtpd_authorized_xclient_hosts =
smtpd_authorized_xforward_hosts =
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_connection_count_limit = 50
smtpd_client_connection_rate_limit = 0
smtpd_client_event_limit_exceptions = ${smtpd_client_connection_limit_exceptions:$mynetworks}
smtpd_client_message_rate_limit = 0
smtpd_client_new_tls_session_rate_limit = 0
smtpd_client_port_logging = no
smtpd_client_recipient_rate_limit = 0
smtpd_client_restrictions =
smtpd_command_filter =
smtpd_data_restrictions =
smtpd_delay_open_until_valid_rcpt = yes
smtpd_delay_reject = yes
smtpd_discard_ehlo_keyword_address_maps =
smtpd_discard_ehlo_keywords =
smtpd_end_of_data_restrictions =
smtpd_enforce_tls = no
smtpd_error_sleep_time = 1s
smtpd_etrn_restrictions =
smtpd_expansion_filter = \t\40!"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~
smtpd_forbidden_commands = CONNECT GET POST
smtpd_hard_error_limit = ${stress?1}${stress:20}
smtpd_helo_required = no
smtpd_helo_restrictions =
smtpd_history_flush_threshold = 100
smtpd_junk_command_limit = ${stress?1}${stress:100}
smtpd_milters =
smtpd_noop_commands =
smtpd_null_access_lookup_key = <>
smtpd_peername_lookup = yes
smtpd_per_record_deadline = ${stress?yes}${stress:no}
smtpd_policy_service_max_idle = 300s
smtpd_policy_service_max_ttl = 1000s
smtpd_policy_service_timeout = 100s
smtpd_proxy_ehlo = $myhostname
smtpd_proxy_filter =
smtpd_proxy_options =
smtpd_proxy_timeout = 100s
smtpd_recipient_limit = 1000
smtpd_recipient_overshoot_limit = 1000
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination
smtpd_reject_footer =
smtpd_reject_unlisted_recipient = yes
smtpd_reject_unlisted_sender = no
smtpd_restriction_classes =
smtpd_sasl_auth_enable = no
smtpd_sasl_authenticated_header = no
smtpd_sasl_exceptions_networks =
smtpd_sasl_local_domain =
smtpd_sasl_path = smtpd
smtpd_sasl_security_options = noanonymous
smtpd_sasl_tls_security_options = $smtpd_sasl_security_options
smtpd_sasl_type = cyrus
smtpd_sender_login_maps =
smtpd_sender_restrictions =
smtpd_service_name = smtpd
smtpd_soft_error_limit = 10
smtpd_starttls_timeout = ${stress?10}${stress:300}s
smtpd_timeout = ${stress?10}${stress:300}s
smtpd_tls_CAfile =
smtpd_tls_CApath =
smtpd_tls_always_issue_session_ids = yes
smtpd_tls_ask_ccert = no
smtpd_tls_auth_only = no
smtpd_tls_ccert_verifydepth = 9
smtpd_tls_cert_file =
smtpd_tls_ciphers = export
smtpd_tls_dcert_file =
smtpd_tls_dh1024_param_file =
smtpd_tls_dh512_param_file =
smtpd_tls_dkey_file = $smtpd_tls_dcert_file
smtpd_tls_eccert_file =
smtpd_tls_eckey_file = $smtpd_tls_eccert_file
smtpd_tls_eecdh_grade = strong
smtpd_tls_exclude_ciphers =
smtpd_tls_fingerprint_digest = md5
smtpd_tls_key_file = $smtpd_tls_cert_file
smtpd_tls_loglevel = 0
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_exclude_ciphers =
smtpd_tls_mandatory_protocols = !SSLv2
smtpd_tls_protocols =
smtpd_tls_received_header = no
smtpd_tls_req_ccert = no
smtpd_tls_security_level =
smtpd_tls_session_cache_database =
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_wrappermode = no
smtpd_use_tls = no
soft_bounce = no
stale_lock_time = 500s
stress =
strict_7bit_headers = no
strict_8bitmime = no
strict_8bitmime_body = no
strict_mailbox_ownership = yes
strict_mime_encoding_domain = no
strict_rfc821_envelopes = no
sun_mailtool_compatibility = no
swap_bangpath = yes
syslog_facility = mail
syslog_name = ${multi_instance_name:postfix}${multi_instance_name?$multi_instance_name}
tcp_windowsize = 0
tls_append_default_CA = no
tls_daemon_random_bytes = 32
tls_disable_workarounds =
tls_eecdh_strong_curve = prime256v1
tls_eecdh_ultra_curve = secp384r1
tls_export_cipherlist = aNULL:-aNULL:ALL:+RC4:@STRENGTH
tls_high_cipherlist = aNULL:-aNULL:ALL:!EXPORT:!LOW:!MEDIUM:+RC4:@STRENGTH
tls_legacy_public_key_fingerprints = no
tls_low_cipherlist = aNULL:-aNULL:ALL:!EXPORT:+RC4:@STRENGTH
tls_medium_cipherlist = aNULL:-aNULL:ALL:!EXPORT:!LOW:+RC4:@STRENGTH
tls_null_cipherlist = eNULL:!aNULL
tls_preempt_cipherlist = no
tls_random_bytes = 32
tls_random_exchange_name = ${data_directory}/prng_exch
tls_random_prng_update_period = 3600s
tls_random_reseed_period = 3600s
tls_random_source = dev:/dev/urandom
tlsproxy_enforce_tls = $smtpd_enforce_tls
tlsproxy_service_name = tlsproxy
tlsproxy_tls_CAfile = $smtpd_tls_CAfile
tlsproxy_tls_CApath = $smtpd_tls_CApath
tlsproxy_tls_always_issue_session_ids = $smtpd_tls_always_issue_session_ids
tlsproxy_tls_ask_ccert = $smtpd_tls_ask_ccert
tlsproxy_tls_ccert_verifydepth = $smtpd_tls_ccert_verifydepth
tlsproxy_tls_cert_file = $smtpd_tls_cert_file
tlsproxy_tls_ciphers = $smtpd_tls_ciphers
tlsproxy_tls_dcert_file = $smtpd_tls_dcert_file
tlsproxy_tls_dh1024_param_file = $smtpd_tls_dh1024_param_file
tlsproxy_tls_dh512_param_file = $smtpd_tls_dh512_param_file
tlsproxy_tls_dkey_file = $smtpd_tls_dkey_file
tlsproxy_tls_eccert_file = $smtpd_tls_eccert_file
tlsproxy_tls_eckey_file = $smtpd_tls_eckey_file
tlsproxy_tls_eecdh_grade = $smtpd_tls_eecdh_grade
tlsproxy_tls_exclude_ciphers = $smtpd_tls_exclude_ciphers
tlsproxy_tls_fingerprint_digest = $smtpd_tls_fingerprint_digest
tlsproxy_tls_key_file = $smtpd_tls_key_file
tlsproxy_tls_loglevel = $smtpd_tls_loglevel
tlsproxy_tls_mandatory_ciphers = $smtpd_tls_mandatory_ciphers
tlsproxy_tls_mandatory_exclude_ciphers = $smtpd_tls_mandatory_exclude_ciphers
tlsproxy_tls_mandatory_protocols = $smtpd_tls_mandatory_protocols
tlsproxy_tls_protocols = $smtpd_tls_protocols
tlsproxy_tls_req_ccert = $smtpd_tls_req_ccert
tlsproxy_tls_security_level = $smtpd_tls_security_level
tlsproxy_tls_session_cache_timeout = $smtpd_tls_session_cache_timeout
tlsproxy_use_tls = $smtpd_use_tls
tlsproxy_watchdog_timeout = 10s
trace_service_name = trace
transport_maps =
transport_retry_time = 60s
trigger_timeout = 10s
undisclosed_recipients_header =
unknown_address_reject_code = 450
unknown_address_tempfail_action = $reject_tempfail_action
unknown_client_reject_code = 450
unknown_helo_hostname_tempfail_action = $reject_tempfail_action
unknown_hostname_reject_code = 450
unknown_local_recipient_reject_code = 550
unknown_relay_recipient_reject_code = 550
unknown_virtual_alias_reject_code = 550
unknown_virtual_mailbox_reject_code = 550
unverified_recipient_defer_code = 450
unverified_recipient_reject_code = 450
unverified_recipient_reject_reason =
unverified_recipient_tempfail_action = $reject_tempfail_action
unverified_sender_defer_code = 450
unverified_sender_reject_code = 450
unverified_sender_reject_reason =
unverified_sender_tempfail_action = $reject_tempfail_action
uucp_delivery_slot_cost = $default_delivery_slot_cost
uucp_delivery_slot_discount = $default_delivery_slot_discount
uucp_delivery_slot_loan = $default_delivery_slot_loan
uucp_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
uucp_destination_concurrency_limit = $default_destination_concurrency_limit
uucp_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
uucp_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
uucp_destination_rate_delay = $default_destination_rate_delay
uucp_destination_recipient_limit = $default_destination_recipient_limit
uucp_extra_recipient_limit = $default_extra_recipient_limit
uucp_initial_destination_concurrency = $initial_destination_concurrency
uucp_minimum_delivery_slots = $default_minimum_delivery_slots
uucp_recipient_limit = $default_recipient_limit
uucp_recipient_refill_delay = $default_recipient_refill_delay
uucp_recipient_refill_limit = $default_recipient_refill_limit
uucp_time_limit = $command_time_limit
verp_delimiter_filter = -=+
virtual_alias_domains = $virtual_alias_maps
virtual_alias_expansion_limit = 1000
virtual_alias_maps = $virtual_maps
virtual_alias_recursion_limit = 1000
virtual_delivery_slot_cost = $default_delivery_slot_cost
virtual_delivery_slot_discount = $default_delivery_slot_discount
virtual_delivery_slot_loan = $default_delivery_slot_loan
virtual_destination_concurrency_failed_cohort_limit = $default_destination_concurrency_failed_cohort_limit
virtual_destination_concurrency_limit = $default_destination_concurrency_limit
virtual_destination_concurrency_negative_feedback = $default_destination_concurrency_negative_feedback
virtual_destination_concurrency_positive_feedback = $default_destination_concurrency_positive_feedback
virtual_destination_rate_delay = $default_destination_rate_delay
virtual_destination_recipient_limit = $default_destination_recipient_limit
virtual_extra_recipient_limit = $default_extra_recipient_limit
virtual_gid_maps =
virtual_initial_destination_concurrency = $initial_destination_concurrency
virtual_mailbox_base =
virtual_mailbox_domains = $virtual_mailbox_maps
virtual_mailbox_limit = 51200000
virtual_mailbox_lock = fcntl, dotlock
virtual_mailbox_maps =
virtual_minimum_delivery_slots = $default_minimum_delivery_slots
virtual_minimum_uid = 100
virtual_recipient_limit = $default_recipient_limit
virtual_recipient_refill_delay = $default_recipient_refill_delay
virtual_recipient_refill_limit = $default_recipient_refill_limit
virtual_transport = virtual
virtual_uid_maps =

```

Here is the output of my dovecot -n:

```

root@andromeda:/etc/postfix# dovecot -n
# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-38-generic-pae i686 Ubuntu 12.04.2 LTS ext4
disable_plaintext_auth = no
first_valid_uid = 150
last_valid_uid = 150
mail_gid = mail
mail_location = mbox:/var/vmail/%d/%n
mail_uid = vmail
managesieve_notify_capability = mailto
managesieve_sieve_capability = fileinto reject envelope encoded-character vacation subaddress comparator-i;ascii-numeric relational regex imap4flags copy include variables body enotify environment mailbox date ihave
passdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}
plugin {
  sieve = ~/.dovecot.sieve
  sieve_dir = ~/sieve
}
postmaster_address = postmaster@cryptodan.net
protocols = imap pop3 sieve
service auth {
  unix_listener /var/spool/postfix/private/dovecot-auth {
    group = postfix
    mode = 0660
    user = postfix
  }
  unix_listener auth-userdb {
    group = mail
    mode = 01224
    user = vmail
  }
}
ssl_ca = </etc/ssl/certs/ca-certificates.crt
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}
protocol imap {
  imap_client_workarounds = tb-extra-mailbox-sep
  mail_max_userip_connections = 10
}
protocol pop3 {
  mail_max_userip_connections = 10
  pop3_client_workarounds = outlook-no-nuls oe-ns-eoh
}
protocol lda {
  deliver_log_format = msgid=%m: %$
  mail_plugins = sieve
  postmaster_address = postmaster
  quota_full_tempfail = yes
  rejection_reason = Your message to <%t> was automatically rejected:%n%r
}

```

I hope I provided enough information.

---

