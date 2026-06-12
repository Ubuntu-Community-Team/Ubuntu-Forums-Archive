---
title: "Is this an SMTP attack?"
date: 2015-11-26
forum: Server Platforms
---

### Post by Matheo84 on 2015-11-26
I don't know what is a rewrite stream but this was on my postfix log and got me worried.

Note that seems that they executed an script maybe using an exploit, and tried to modify the configuration... any advice?

```

Nov 26 00:13:00 li367-73 postfix/smtpd[29285]: warning: hostname br13.srvmatrix.info does not resolve to address 177.11.51.75: Name or service not known
Nov 26 00:13:00 li367-73 postfix/smtpd[29285]: connect from unknown[177.11.51.75]
Nov 26 00:13:01 li367-73 postfix/smtpd[29285]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Nov 26 00:13:01 li367-73 postfix/smtpd[29285]: fatal: no SASL authentication mechanisms
Nov 26 00:13:01 li367-73 postfix/smtpd[29288]: warning: hostname br13.srvmatrix.info does not resolve to address 177.11.51.75: Name or service not known
Nov 26 00:13:01 li367-73 postfix/smtpd[29288]: connect from unknown[177.11.51.75]
Nov 26 00:13:01 li367-73 postfix/smtpd[29289]: warning: hostname br13.srvmatrix.info does not resolve to address 177.11.51.75: Name or service not known
Nov 26 00:13:01 li367-73 postfix/smtpd[29289]: connect from unknown[177.11.51.75]
Nov 26 00:13:01 li367-73 postfix/smtpd[29290]: warning: hostname br13.srvmatrix.info does not resolve to address 177.11.51.75: Name or service not known
Nov 26 00:13:01 li367-73 postfix/smtpd[29290]: connect from unknown[177.11.51.75]
Nov 26 00:13:01 li367-73 postfix/smtpd[29290]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
Nov 26 00:13:01 li367-73 postfix/smtpd[29290]: fatal: no SASL authentication mechanisms
Nov 26 00:13:02 li367-73 postfix/master[2372]: warning: process /usr/lib/postfix/smtpd pid 29285 exit status 1
Nov 26 00:13:02 li367-73 postfix/master[2372]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Nov 26 00:13:02 li367-73 postfix/smtpd[29288]: NOQUEUE: reject_warning: RCPT from unknown[177.11.51.75]: 554 5.7.1 <teste03.pop3@hotmail.com>: Relay access denied; from=<rjqzy@mydomain.com> to=<teste03.pop3@hotmail.com> proto=ESMTP helo=<mail.mydomain.com>
Nov 26 00:13:02 li367-73 postfix/smtpd[29288]: NOQUEUE: reject: RCPT from unknown[177.11.51.75]: 554 5.7.1 <teste03.pop3@hotmail.com>: Relay access denied; from=<rjqzy@mydomain.com> to=<teste03.pop3@hotmail.com> proto=ESMTP helo=<mail.mydomain.com>
Nov 26 00:13:02 li367-73 postfix/smtpd[29289]: NOQUEUE: reject_warning: RCPT from unknown[177.11.51.75]: 554 5.7.1 <teste03.pop3@hotmail.com>: Relay access denied; from=<agpzthu@gmail.com> to=<teste03.pop3@hotmail.com> proto=ESMTP helo=<mail.mydomain.com>
Nov 26 00:13:02 li367-73 postfix/smtpd[29289]: NOQUEUE: reject: RCPT from unknown[177.11.51.75]: 554 5.7.1 <teste03.pop3@hotmail.com>: Relay access denied; from=<agpzthu@gmail.com> to=<teste03.pop3@hotmail.com> proto=ESMTP helo=<mail.mydomain.com>
Nov 26 00:13:02 li367-73 postfix/smtpd[29288]: warning: non-SMTP command from unknown[177.11.51.75]: From: rjqzy@mydomain.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29288]: disconnect from unknown[177.11.51.75]
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: name_mask: all
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: inet_addr_local: configured 2 IPv4 addresses
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: inet_addr_local: configured 2 IPv6 addresses
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: process generation: 1236 (1236)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: mynetworks ~? debug_peer_list
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: mynetworks ~? fast_flush_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: mynetworks ~? mynetworks
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: relay_domains ~? debug_peer_list
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: relay_domains ~? fast_flush_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: relay_domains ~? mynetworks
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: relay_domains ~? permit_mx_backup_networks
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: relay_domains ~? qmqpd_authorized_clients
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: relay_domains ~? relay_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: permit_mx_backup_networks ~? debug_peer_list
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: permit_mx_backup_networks ~? fast_flush_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: permit_mx_backup_networks ~? mynetworks
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: permit_mx_backup_networks ~? permit_mx_backup_networks
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: connect to subsystem private/proxymap
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr request = open
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr table = unix:passwd.byname
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr flags = 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/proxymap socket: wanted attribute: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/proxymap socket: wanted attribute: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 16
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/proxymap socket: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: dict_proxy_open: connect to map=unix:passwd.byname status=0 server_flags=fixed
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: dict_open: proxy:unix:passwd.byname
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: Compiled against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: Run-time linked against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: dict_open: hash:/etc/aliases
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: Compiled against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: Run-time linked against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: dict_open: hash:/etc/postfix/virtual
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: smtpd_access_maps ~? debug_peer_list
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: smtpd_access_maps ~? fast_flush_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: smtpd_access_maps ~? mynetworks
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: smtpd_access_maps ~? permit_mx_backup_networks
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: smtpd_access_maps ~? qmqpd_authorized_clients
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: smtpd_access_maps ~? relay_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: smtpd_access_maps ~? smtpd_access_maps
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: dict_open: pcre:/etc/postfix/sender_access.pcre
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: Compiled against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: Run-time linked against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: dict_open: hash:/etc/postfix/sender_access
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: unknown_helo_hostname_tempfail_action = defer_if_permit
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: unknown_address_tempfail_action = defer_if_permit
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: unverified_recipient_tempfail_action = defer_if_permit
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: unverified_sender_tempfail_action = defer_if_permit
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: name_mask: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: auto_clnt_create: transport=local endpoint=private/tlsmgr
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: auto_clnt_open: connected to private/tlsmgr
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr request = seed
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr size = 32
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/tlsmgr: wanted attribute: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/tlsmgr: wanted attribute: seed
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: seed
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: oRjkp3Jtw1Ihub7/dG4cnDYUQEVmSACX6OMUftvlZ/Q=
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/tlsmgr: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr request = policy
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr cache_type = smtpd
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/tlsmgr: wanted attribute: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/tlsmgr: wanted attribute: cachable
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: cachable
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 1
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/tlsmgr: wanted attribute: timeout
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: timeout
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 3600
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/tlsmgr: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: fast_flush_domains ~? debug_peer_list
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_string: fast_flush_domains ~? fast_flush_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: auto_clnt_create: transport=local endpoint=private/anvil
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: connection established
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: master_notify: status 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: name_mask: resource
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: name_mask: software
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: warning: hostname br13.srvmatrix.info does not resolve to address 177.11.51.75: Name or service not known
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: connect from unknown[177.11.51.75]
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_list_match: unknown: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_list_match: 177.11.51.75: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_list_match: unknown: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_list_match: 177.11.51.75: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: smtp_stream_setup: maxtime=300 enable_deadline=0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_hostname: unknown ~? 127.0.0.0/8
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_hostaddr: 177.11.51.75 ~? 127.0.0.0/8
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_hostname: unknown ~? [::ffff:127.0.0.0]/104
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_hostaddr: 177.11.51.75 ~? [::ffff:127.0.0.0]/104
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_hostname: unknown ~? [::1]/128
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_hostaddr: 177.11.51.75 ~? [::1]/128
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_list_match: unknown: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_list_match: 177.11.51.75: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: auto_clnt_open: connected to private/anvil
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr request = connect
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr ident = smtps:177.11.51.75
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/anvil: wanted attribute: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/anvil: wanted attribute: count
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: count
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 1
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/anvil: wanted attribute: rate
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: rate
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 1
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/anvil: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 220 localhost ESMTP Postfix (Debian/GNU)
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: name_mask: all
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: inet_addr_local: configured 2 IPv4 addresses
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: inet_addr_local: configured 2 IPv6 addresses
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: process generation: 1237 (1237)
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: mynetworks ~? debug_peer_list
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: mynetworks ~? fast_flush_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: mynetworks ~? mynetworks
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: relay_domains ~? debug_peer_list
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: relay_domains ~? fast_flush_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: relay_domains ~? mynetworks
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: relay_domains ~? permit_mx_backup_networks
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: relay_domains ~? qmqpd_authorized_clients
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: relay_domains ~? relay_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: permit_mx_backup_networks ~? debug_peer_list
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: permit_mx_backup_networks ~? fast_flush_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: permit_mx_backup_networks ~? mynetworks
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: permit_mx_backup_networks ~? permit_mx_backup_networks
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: connect to subsystem private/proxymap
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: send attr request = open
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: send attr table = unix:passwd.byname
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: send attr flags = 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/proxymap socket: wanted attribute: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/proxymap socket: wanted attribute: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute value: 16
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/proxymap socket: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: dict_proxy_open: connect to map=unix:passwd.byname status=0 server_flags=fixed
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: dict_open: proxy:unix:passwd.byname
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: Compiled against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: Run-time linked against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: dict_open: hash:/etc/aliases
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: Compiled against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: Run-time linked against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: dict_open: hash:/etc/postfix/virtual
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: smtpd_access_maps ~? debug_peer_list
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: smtpd_access_maps ~? fast_flush_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: smtpd_access_maps ~? mynetworks
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: smtpd_access_maps ~? permit_mx_backup_networks
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: smtpd_access_maps ~? qmqpd_authorized_clients
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: smtpd_access_maps ~? relay_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: smtpd_access_maps ~? smtpd_access_maps
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: dict_open: pcre:/etc/postfix/sender_access.pcre
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: Compiled against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: Run-time linked against Berkeley DB: 5.3.28?
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: dict_open: hash:/etc/postfix/sender_access
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: unknown_helo_hostname_tempfail_action = defer_if_permit
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: unknown_address_tempfail_action = defer_if_permit
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: unverified_recipient_tempfail_action = defer_if_permit
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: unverified_sender_tempfail_action = defer_if_permit
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: name_mask: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: auto_clnt_create: transport=local endpoint=private/tlsmgr
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: auto_clnt_open: connected to private/tlsmgr
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: send attr request = seed
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: send attr size = 32
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/tlsmgr: wanted attribute: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/tlsmgr: wanted attribute: seed
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: seed
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute value: BnAmM+U6dSNvyO6LrLwwi+qD3PF2/cimZc2fLTTLO4A=
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/tlsmgr: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: send attr request = policy
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: send attr cache_type = smtpd
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/tlsmgr: wanted attribute: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/tlsmgr: wanted attribute: cachable
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: cachable
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute value: 1
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/tlsmgr: wanted attribute: timeout
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: timeout
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute value: 3600
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/tlsmgr: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: fast_flush_domains ~? debug_peer_list
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_string: fast_flush_domains ~? fast_flush_domains
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: auto_clnt_create: transport=local endpoint=private/anvil
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: connection established
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: master_notify: status 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: name_mask: resource
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: name_mask: software
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: warning: hostname br13.srvmatrix.info does not resolve to address 177.11.51.75: Name or service not known
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: connect from unknown[177.11.51.75]
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_list_match: unknown: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_list_match: 177.11.51.75: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_list_match: unknown: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_list_match: 177.11.51.75: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: smtp_stream_setup: maxtime=300 enable_deadline=0
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_hostname: unknown ~? 127.0.0.0/8
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_hostaddr: 177.11.51.75 ~? 127.0.0.0/8
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_hostname: unknown ~? [::ffff:127.0.0.0]/104
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_hostaddr: 177.11.51.75 ~? [::ffff:127.0.0.0]/104
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_hostname: unknown ~? [::1]/128
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_hostaddr: 177.11.51.75 ~? [::1]/128
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_list_match: unknown: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_list_match: 177.11.51.75: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: auto_clnt_open: connected to private/anvil
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: send attr request = connect
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: send attr ident = smtps:177.11.51.75
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/anvil: wanted attribute: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: status
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/anvil: wanted attribute: count
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: count
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute value: 2
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/anvil: wanted attribute: rate
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: rate
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute value: 2
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: private/anvil: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 220 localhost ESMTP Postfix (Debian/GNU)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: < unknown[177.11.51.75]: EHLO mail.mydomain.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_list_match: unknown: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: match_list_match: 177.11.51.75: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 250-localhost
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 250-PIPELINING
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 250-SIZE 10240000
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 250-ETRN
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 250-STARTTLS
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 250-ENHANCEDSTATUSCODES
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 250-8BITMIME
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 250 DSN
Nov 26 00:13:02 li367-73 postfix/smtpd[29289]: warning: non-SMTP command from unknown[177.11.51.75]: From: agpzthu@gmail.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29289]: disconnect from unknown[177.11.51.75]
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: < unknown[177.11.51.75]: EHLO mail.mydomain.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_list_match: unknown: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: match_list_match: 177.11.51.75: no match
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 250-localhost
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 250-PIPELINING
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 250-SIZE 10240000
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 250-ETRN
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 250-STARTTLS
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 250-ENHANCEDSTATUSCODES
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 250-8BITMIME
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 250 DSN
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: < unknown[177.11.51.75]: RSET
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 250 2.0.0 Ok
Nov 26 00:13:02 li367-73 postfix/master[2372]: warning: process /usr/lib/postfix/smtpd pid 29290 exit status 1
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: < unknown[177.11.51.75]: RSET
Nov 26 00:13:02 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 250 2.0.0 Ok
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: < unknown[177.11.51.75]: MAIL FROM: <oatwfdu@hotmail.com>
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: extract_addr: input: <oatwfdu@hotmail.com>
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: smtpd_check_addr: addr=oatwfdu@hotmail.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: connect to subsystem private/rewrite
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr request = rewrite
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr rule = local
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr address = oatwfdu@hotmail.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: address
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: address
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: oatwfdu@hotmail.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: rewrite_clnt: local: oatwfdu@hotmail.com -> oatwfdu@hotmail.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr request = resolve
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr sender = 
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr address = oatwfdu@hotmail.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: transport
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: transport
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: smtp
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: nexthop
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: nexthop
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: hotmail.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: recipient
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: recipient
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: oatwfdu@hotmail.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 4096
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: resolve_clnt: `' -> `oatwfdu@hotmail.com' -> transp=`smtp' host=`hotmail.com' rcpt=`oatwfdu@hotmail.com' flags= class=default
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: ctable_locate: install entry key oatwfdu@hotmail.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: extract_addr: in: <oatwfdu@hotmail.com>, result: oatwfdu@hotmail.com
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr request = rewrite
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr rule = local
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: send attr address = double-bounce
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: flags
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: 0
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: address
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: address
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute value: double-bounce@localhost
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: (list terminator)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: input attribute name: (end)
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: rewrite_clnt: local: double-bounce -> double-bounce@localhost
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: smtpd_check_rewrite: trying: permit_inet_interfaces
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: permit_inet_interfaces: unknown 177.11.51.75
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: fsspace: .: block size 4096, blocks free 4350914
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: smtpd_check_queue: blocks 4096 avail 4350914 min_free 0 msg_size_limit 10240000
Nov 26 00:13:02 li367-73 postfix/smtpd[29292]: > unknown[177.11.51.75]: 250 2.1.0 Ok
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: < unknown[177.11.51.75]: MAIL FROM: <lqbqpgis@mydomain.com>
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: extract_addr: input: <lqbqpgis@mydomain.com>
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: smtpd_check_addr: addr=lqbqpgis@mydomain.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: connect to subsystem private/rewrite
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: send attr request = rewrite
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: send attr rule = local
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: send attr address = lqbqpgis@mydomain.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: flags
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: flags
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute value: 0
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: address
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: address
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute value: lqbqpgis@mydomain.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: (list terminator)
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: (end)
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: rewrite_clnt: local: lqbqpgis@mydomain.com -> lqbqpgis@mydomain.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: send attr request = resolve
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: send attr sender = 
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: send attr address = lqbqpgis@mydomain.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: flags
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: flags
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute value: 0
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: transport
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: transport
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute value: error
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: nexthop
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: nexthop
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute value: 5.1.1 User unknown in virtual alias table
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: recipient
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: recipient
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute value: lqbqpgis@mydomain.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: flags
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: flags
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute value: 512
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: (list terminator)
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: (end)
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: resolve_clnt: `' -> `lqbqpgis@mydomain.com' -> transp=`error' host=`5.1.1 User unknown in virtual alias table' rcpt=`lqbqpgis@mydomain.com' flags= class=alias
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: ctable_locate: install entry key lqbqpgis@mydomain.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: extract_addr: in: <lqbqpgis@mydomain.com>, result: lqbqpgis@mydomain.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: send attr request = rewrite
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: send attr rule = local
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: send attr address = double-bounce
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: flags
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: flags
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute value: 0
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: address
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: address
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute value: double-bounce@localhost
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: (list terminator)
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: input attribute name: (end)
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: rewrite_clnt: local: double-bounce -> double-bounce@localhost
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: smtpd_check_rewrite: trying: permit_inet_interfaces
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: permit_inet_interfaces: unknown 177.11.51.75
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: fsspace: .: block size 4096, blocks free 4350911
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: smtpd_check_queue: blocks 4096 avail 4350911 min_free 0 msg_size_limit 10240000
Nov 26 00:13:03 li367-73 postfix/smtpd[29293]: > unknown[177.11.51.75]: 250 2.1.0 Ok
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: < unknown[177.11.51.75]: RCPT TO: <teste03.pop3@hotmail.com>
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: extract_addr: input: <teste03.pop3@hotmail.com>
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: smtpd_check_addr: addr=teste03.pop3@hotmail.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: send attr request = rewrite
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: send attr rule = local
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: send attr address = teste03.pop3@hotmail.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: flags
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: input attribute name: flags
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: input attribute value: 0
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: address
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: input attribute name: address
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: input attribute value: teste03.pop3@hotmail.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: private/rewrite socket: wanted attribute: (list terminator)
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: input attribute name: (end)
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: rewrite_clnt: local: teste03.pop3@hotmail.com -> teste03.pop3@hotmail.com
Nov 26 00:13:03 li367-73 postfix/smtpd[29292]: send attr request = resolve
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: < unknown[177.11.51.75]: RCPT TO: <teste03.pop3@hotmail.com>
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: extract_addr: input: <teste03.pop3@hotmail.com>
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: smtpd_check_addr: addr=teste03.pop3@hotmail.com
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: send attr request = rewrite
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: send attr rule = local
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: send attr address = teste03.pop3@hotmail.com
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: flags
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: input attribute name: flags
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: input attribute value: 0
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: address
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: input attribute name: address
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: input attribute value: teste03.pop3@hotmail.com
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: private/rewrite socket: wanted attribute: (list terminator)
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: input attribute name: (end)
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: rewrite_clnt: local: teste03.pop3@hotmail.com -> teste03.pop3@hotmail.com
Nov 26 00:13:05 li367-73 postfix/smtpd[29293]: send attr request = resolve
Nov 26 00:13:08 li367-73 postfix/smtpd[29292]: rewrite stream disconnect

```

My postconf doesn't show changes, and later activity only shows many attempts from another suspicious IP:

```

Nov 26 09:16:19 li367-73 postfix/smtpd[2654]: connect from unknown[199.19.105.111]
Nov 26 09:16:19 li367-73 postfix/smtpd[2657]: warning: hostname mta11.ragoonmoon.info does not resolve to address 199.19.105.111: Name or service not known
Nov 26 09:16:19 li367-73 postfix/smtpd[2657]: connect from unknown[199.19.105.111]
Nov 26 09:16:19 li367-73 postfix/smtpd[2654]: lost connection after CONNECT from unknown[199.19.105.111]

```

I just enforced the security of my VPS and this just happened, maybe the spammers got mad because now I block the 99% of their attemps? OMG

---

### Post by gtozzi on 2015-11-26
Probably it is.

If you are running an SMTP server on internet, it's normal to receive attacks every day.

---

### Post by Habitual on 2015-11-27
fail2ban can help reduce this "noise".

---

### Post by darkod on 2015-11-27
@Habitual

Since this subject is interesting to me too, would you have a recommended "configuration" of fail2ban? Is it simply installing it and off it goes? What happens in cases where you have custom iptables rules loaded with iptables-restore in /etc/network/interfaces?

---

### Post by Doug S on 2015-11-27
Darko,
I use these iptables rules to deal with e-mail issues (readers might note the similarity to the same ssh rules that I posted a bunch of times):
```
# Ver: 1.16: Switch to a full bad guy detector here. The simple rate limiting rule doesn't achieve the objective.
# e-mail connection floods of recent have prompted this change. Old rule, commented out, left for reference.
# Once they are on the BADGUY list then DROP all packets from them.
# Note: if e-mail distibution list type traffic ever goes through this server, the hitcount might need to increase a lot and
# the seconds might need to come down a lot. This method might not even work.
#
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -m limit --limit 5/minute --limit-burst 3 -s $UNIVERSE -d $EXTIP --dport 25 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 10 --seconds 90000 --name BADGUY_EMAIL -j LOG --log-prefix "EMAIL BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 10 --seconds 90000 --name BADGUY_EMAIL -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 25 -m recent --set --name BADGUY_EMAIL -j ACCEPT

```Sorry for this tangent on the OP's thread. By the way, In my logs I have never seen anything like what the OP is seeing.

Edit: Some prefer to use "REJECT" rather than "DROP".

---

### Post by Habitual on 2015-11-27
> **darkod said:**
> @Habitual

Since this subject is interesting to me too, would you have a recommended "configuration" of fail2ban? Is it simply installing it and off it goes? What happens in cases where you have custom iptables rules loaded with iptables-restore in /etc/network/interfaces?
I wish it were as easy as installing it and "off it goes".
fail2ban only protects "out of the box" for ssh.

Up front, you can test (after installing fail2ban) the postfix filter by using 
```
fail2ban-regex /path/to/file.log /etc/fail2ban/filter.d/postfix.conf
```

The installation of fail2ban provides /etc/fail2ban/filter.d/postfix.conf
and that has regex filter for 554 "errors".

I stuck the OP's [snippet]("http://pastie.org/pastes/10584534/text?key=jtbu6lkutq2k8fblpva")  into /root/test.log and ran
```
fail2ban-regex /root/test.log  /etc/fail2ban/filter.d/postfix.conf
```
and it 'hit' twice:
```
Addresses found:
[1]
    177.11.51.75 (Thu Nov 26 00:13:02 2015)
    177.11.51.75 (Thu Nov 26 00:13:02 2015)
```

The /etc/fail2ban/jail.local (copy of /etc/fail2ban/jail.conf) would need to have a stanza enabled for postfix, such as 
```
[postfix]

enabled  = true
port     = smtp,ssmtp,submission
filter   = postfix
logpath  = /var/log/mail.log
```

This jail came straight from /etc/fail2ban/jail.conf

Here is /etc/fail2ban/jail.conf's 'defaults'
```
[DEFAULT]
ignoreip = 127.0.0.1/8
bantime  = 600
findtime = 600
maxretry = 3
```

I use these as my 'defaults'
```
[DEFAULT]
ignoreip = 127.0.0.1/8 My_home_IP/32 Office_IP/32 Other_safe_IP/32
bantime  = 31556926 # 1 year in second #BoFH setting
```

Any jail that you enable that does not have these explicitly will use defaults (and defaults can be overwritten on a per-jail basis, eg: become explicit)
eg:
```
[postfix]

enabled  = true
port     = smtp,ssmtp,submission
filter   = postfix
logpath  = /var/log/mail.log
maxretry = 1

```

I have added code in my custom **action** filter.
```
iptables-save > /etc/iptables/rules.v4
``` which keeps my rules persistent across restarts of fail2ban since I installed
the *iptables-persistent* package.
But alas, this needs "tuning". :(
```
service fail2ban restart 
```
dumps quite a few of my rules. But Security is a verb, right?

You could modify your custom action filter to utilize
```
/sbin/iptables-restore < /path/to/saved/rules
```
in the actionstart = section of the action.d/filter.conf

I also have in /etc/rc.local```

/sbin/iptables-restore < /path/to/saved/rules
``` as another 'safety measure' :)

**[COLOR=#ff0000]It takes work[/COLOR]** and some intermediate Linux kung.fu, so it is not recommended for the faint-of-heart, or Linux "newbies" which I know you are not.

If ***you*** wish to dialog further on this, shoot me a PM and I'll be glad to help you out.
It's not an issue that troubleshoots well in forum posts.
But I prefer to use email as the primary method of communication. So be prepared to give me an address. ;)
And if that's too intrusive for you, I'll hang with you here (in a new post of course).

Subscribed with interest...

---

### Post by Matheo84 on 2015-11-28
Wow, thanks guys!
I googled how to reject non-SMTP commands and found a reference to fail2ban too :D

Following the advices I'm quite happy now, and I want to share what I finally did:

First, I was happy with the set of Postfix restrictions I found, and blocks a ton of attempts: [https://gist.github.com/matheo/bad92ad2d5f111abb6e1](https://gist.github.com/matheo/bad92ad2d5f111abb6e1)
except the non-SMTP execution which got me scared, so fail2ban comes to play banning them all:
```

apt-get install fail2ban
nano /etc/fail2ban/filter.d/postfix.conf

```

The postfix filter to use:
```

# Fail2Ban filter for selected Postfix SMTP rejections


[INCLUDES]


before = common.conf


[Definition]


_daemon = postfix/smtpd


failregex = reject: RCPT from \S+\[<HOST>\]
            reject_warning: RCPT from \S+\[<HOST>\]
            warning: non-SMTP command from \S+\[<HOST>\]


ignoreregex =

```

I tested it successfully with:
```

fail2ban-regex /var/log/mail.log /etc/fail2ban/filter.d/postfix.conf --print-no-missed -v

```

Then configured the jail on a new file **/etc/fail2ban/jail.local**
```

[DEFAULT]
ignoreip = 127.0.0.1/8
bantime  = 31556926  ; 1 year in second #BoFH setting


[postfix]
enabled  = true
port     = smtp,ssmtp,submission
filter   = postfix
logpath  = /var/log/mail.log
maxretry = 1

```

and restarted the service checking the log to see what's up:
```

service fail2ban restart
tail -f /var/log/fail2ban.log

```

and it's working :3
```

2015-11-28 20:16:14,363 fail2ban.server [4426]: INFO    Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.13
2015-11-28 20:16:14,364 fail2ban.jail   [4426]: INFO    Creating new jail 'ssh'
2015-11-28 20:16:14,383 fail2ban.jail   [4426]: INFO    Jail 'ssh' uses pyinotify
2015-11-28 20:16:14,401 fail2ban.jail   [4426]: INFO    Initiated 'pyinotify' backend
2015-11-28 20:16:14,402 fail2ban.filter [4426]: INFO    Added logfile = /var/log/auth.log
2015-11-28 20:16:14,403 fail2ban.filter [4426]: INFO    Set maxRetry = 6
2015-11-28 20:16:14,404 fail2ban.filter [4426]: INFO    Set findtime = 600
2015-11-28 20:16:14,405 fail2ban.actions[4426]: INFO    Set banTime = 31556926
2015-11-28 20:16:14,440 fail2ban.jail   [4426]: INFO    Creating new jail 'postfix'
2015-11-28 20:16:14,440 fail2ban.jail   [4426]: INFO    Jail 'postfix' uses pyinotify
2015-11-28 20:16:14,444 fail2ban.jail   [4426]: INFO    Initiated 'pyinotify' backend
2015-11-28 20:16:14,445 fail2ban.filter [4426]: INFO    Added logfile = /var/log/mail.log
2015-11-28 20:16:14,446 fail2ban.filter [4426]: INFO    Set maxRetry = 1
2015-11-28 20:16:14,447 fail2ban.filter [4426]: INFO    Set findtime = 600
2015-11-28 20:16:14,447 fail2ban.actions[4426]: INFO    Set banTime = 31556926
2015-11-28 20:16:14,455 fail2ban.jail   [4426]: INFO    Jail 'ssh' started
2015-11-28 20:16:14,458 fail2ban.jail   [4426]: INFO    Jail 'postfix' started
2015-11-28 20:17:09,539 fail2ban.actions[4426]: WARNING [postfix] Ban 46.149.84.12
2015-11-28 20:34:14,739 fail2ban.actions[4426]: WARNING [postfix] Ban 185.109.144.170


```

I would like additional info on how to fetch the banned IPs to a file and persist the ban.
Thanks a lot!!!

---

### Post by Habitual on 2015-11-28
Good job and Well Done!
Since you are motivated, search engine [recidive+fail2ban]("https://duckduckgo.com/?q=recidive+fail2ban") or something like:
```

[recidive]

enabled  = true
filter   = recidive
logpath  = /var/log/fail2ban.log
action   = iptables-allports[name=recidive]
           sendmail-whois-lines[name=recidive, logpath=/var/log/fail2ban.log]
bantime  = 604800  ; 1 week
findtime = 86400   ; 1 day
maxretry = 3

```^[Reference]("https://github.com/fail2ban/fail2ban/issues/605")^

Test:
```
fail2ban-regex /var/log/fail2ban.log /etc/fail2ban/filter.d/recidive.conf
```

Hope that helps.

---

### Post by Matheo84 on 2015-11-29
Yes!
searching for "persist fail2ban ip" found a nice article about it:
[http://zach.seifts.us/posts/2013/07/14/how-make-fail2ban-bans-persistent](http://zach.seifts.us/posts/2013/07/14/how-make-fail2ban-bans-persistent)

Making some improvements and understanding that stuff, the final setup is this:
Add a new action file **/etc/fail2ban/action.d/iptables-persist.conf** with:

```

# Fail2Ban configuration file
#
# Author: Cyril Jaquier
# Modified by Yaroslav Halchenko for multiport banning
# Modified with http://zach.seifts.us/posts/2013/07/14/how-make-fail2ban-bans-persistent
#


[INCLUDES]


before = iptables-blocktype.conf


[Definition]


# Option:  actionstart
# Notes.:  command executed once at the start of Fail2Ban.
# Values:  CMD
#
actionstart = iptables -N fail2ban-<name>
              iptables -A fail2ban-<name> -j RETURN
              iptables -I <chain> -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
              touch /etc/fail2ban/ip.<name>.blacklist
              cat /etc/fail2ban/ip.<name>.blacklist | while read IP; do fail2ban-client set <name> banip $IP; done


# Option:  actionstop
# Notes.:  command executed once at the end of Fail2Ban
# Values:  CMD
#
actionstop = iptables -D <chain> -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
             iptables -F fail2ban-<name>
             iptables -X fail2ban-<name>


# Option:  actioncheck
# Notes.:  command executed once before each actionban command
# Values:  CMD
#
actioncheck = iptables -n -L <chain> | grep -q 'fail2ban-<name>[ \t]'


# Option:  actionban
# Notes.:  command executed when banning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    See jail.conf(5) man page
# Values:  CMD
#
actionban = iptables -I fail2ban-<name> 1 -s <ip> -j <blocktype>
            grep <ip> /etc/fail2ban/ip.<name>.blacklist || echo <ip> >> /etc/fail2ban/ip.<name>.blacklist


# Option:  actionunban
# Notes.:  command executed when unbanning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    See jail.conf(5) man page
# Values:  CMD
#
actionunban = iptables -D fail2ban-<name> -s <ip> -j <blocktype>


[Init]


# Default name of the chain
#
name = default


# Option:  protocol
# Notes.:  internally used by config reader for interpolations.
# Values:  [ tcp | udp | icmp | all ] Default: tcp
#
protocol = all


# Option:  chain
# Notes    specifies the iptables chain to which the fail2ban rules should be
#          added
# Values:  STRING  Default: INPUT
chain = INPUT

```

Enable it in the **/etc/fail2ban/jail.local** so my final file looks like this:

```

[DEFAULT]
banaction = iptables-persist
bantime  = 31556926  ; 1 year in second #BoFH setting
maxretry = 2
ignoreip = 127.0.0.1/8


[postfix]
actionstart = iptables-persist
enabled  = true
port     = smtp,ssmtp,submission
filter   = postfix
logpath  = /var/log/mail.log
maxretry = 1

```

So the blacklists are created dinamically by jail <name> on /etc/fail2ban/ip.<name>.blacklist files :D
```

              touch /etc/fail2ban/ip.<name>.blacklist

```


add the banned ip to the file without repeat it
```

            grep <ip> /etc/fail2ban/ip.<name>.blacklist || echo <ip> >> /etc/fail2ban/ip.<name>.blacklist

```

And restarting the service read those files and ban the ips again:
```

              cat /etc/fail2ban/ip.<name>.blacklist | while read IP; do fail2ban-client set <name> banip $IP; done

```

Fun stuff. Thank you all!!

---

### Post by Habitual on 2015-11-29
A little unconventional, but ok.

Note: from [http://zach.seifts.us/posts/2013/07/14/how-make-fail2ban-bans-persistent](http://zach.seifts.us/posts/2013/07/14/how-make-fail2ban-bans-persistent)
he says "Then you can either make a copy or edit the /etc/fail2ban/action.d/iptables-multiport.conf file.
I prefer to make a copy of it because I version all of my configs."
** You should make your own copy of original files as your copies will not be overwritten during an upgrade.**

I have kept my "bad guys" is one list like so:
```
uniq /etc/fail2ban/blacklists/bad.guys | while read IP; do iptables -I fail2ban-mycustom 1 -s $IP -j DROP; done
```

---

### Post by Matheo84 on 2015-12-01
Indeed,
based on iptables-multiport.conf I created the new non-existing one that I shared below:
**/etc/fail2ban/action.d/iptables-persist.conf **;)

Thanks for the advice!

---

### Post by Habitual on 2015-12-01
Notes and Observations:
I had to go with
```
actionstart = iptables -N fail2ban-<name>
              iptables -A fail2ban-<name> -j RETURN
              iptables -I <chain> -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
              /sbin/iptables-restore < /etc/iptables/rules.v4
...
actionban = iptables -I fail2ban-<name> 1 -s <ip> -j DROP
            /sbin/iptables-save > /etc/iptables/rules.v4
...
```

/sbin/iptables-restore < /path/to/file.save just wouldn't do it on 
```
service fail2ban restart
```

I have iptables-persistent installed and I believe this conflicts with the recidive jail.

Hello darkod!

If it was "easy" I'd be out of work, tossing pizzas somewhere, so I'm grateful that it's not "that easy".
Have a Great Day!

---

### Post by Habitual on 2015-12-03
wrong fail2ban post updated. ignore.

---

### Post by Habitual on 2015-12-03
wrong fail2ban [post]("http://ubuntuforums.org/showthread.php?t=2305198&p=13401254#post13401254") updated. ignore.

---

