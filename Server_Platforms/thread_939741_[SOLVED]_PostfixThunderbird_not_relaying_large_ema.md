---
title: "[SOLVED] Postfix/Thunderbird not relaying large emails"
date: 2008-10-06
forum: Server Platforms
---

### Post by cirobr on 2008-10-06
Hello,

I have Ubundu Hardy Server Edition installed on a local network PC.

Fetchmail/Postfix/Dovecot are installed for email server management. All softwares work perfectly on grabbing email from ISP POP3 account and transfering to clients. Thunderbird is the email client on the networked PCs.

When Thunderbird sends email from a client PC directly to the ISP SMTP server, no problem is found as well.

On the other hand, when Thunderbird sends to Postfix, which in turn sends to ISP SMTP server, the following happens:
- For emails smaller than 100 KB or so, no problem found. Emails are delivered to final destination.
- For those above 100 KB, upload from Thunderbird freezes, apparently when this limit is reached, therefore forcing manual cancellation.
- For large emails, both text-only and with attachments, problem is observed.

Any hint to solve the issue is appreciated.

Thanks.

---

### Post by MJN on 2008-10-06
Check/post the mail logs as if it is a Postfix issue the fact will likely be reported in them.
 
Also try testing with another mail client.
 
Mathew

---

### Post by cirobr on 2008-11-11
Hello,

It doesn´t seem to be any problem with Postix. Short messages are delivered as per the below log:

**********************************
Nov 11 20:19:02 note1-server postfix/smtpd[20033]: connect from unknown[192.168.0.126]
Nov 11 20:19:09 note1-server postfix/smtpd[20033]: 4352C1920CA: client=unknown[192.168.0.126], sasl_method=PLAIN, sasl_username=marina
Nov 11 20:19:09 note1-server postfix/cleanup[20040]: 4352C1920CA: message-id=<1226449141.18423.0.camel@note3-linux>
Nov 11 20:19:09 note1-server postfix/qmgr[19916]: 4352C1920CA: from=<marina.m.rosa@terra.com.br>, size=507, nrcpt=1 (queue active)
Nov 11 20:19:09 note1-server postfix/smtpd[20033]: disconnect from unknown[192.168.0.126]
Nov 11 20:19:17 note1-server postfix/smtp[20041]: 4352C1920CA: to=<ciro.rosa@st.com>, relay=smtp.sao.terra.com.br[200.154.55.5]:25, delay=8, delays=0.2/0.01/6/1.8, dsn=2.0.0, status=sent (250 Ok: queued as 1342FA000088)
Nov 11 20:19:17 note1-server postfix/qmgr[19916]: 4352C1920CA: removed
***********************************************

However, with large KB messages:

***********************************************
Nov 11 20:22:26 note1-server postfix/smtpd[20083]: connect from unknown[192.168.0.126]
Nov 11 20:22:27 note1-server postfix/smtpd[20083]: 29B461920CB: client=unknown[192.168.0.126], sasl_method=PLAIN, sasl_username=marina
***********************************************

After that, upload stops and process freezes.

Both Thunderbird and Evolution show up same behaviour.

---

### Post by MJN on 2008-11-12
By 'process freezes' which process are you talking about?
 
Try adding -v (or even -vv) to the smtpd command at the end of the smtp line in /etc/postfix/master.cf.
 
This will increase the verbosity of the logging to show exactly what stage is being reached.
 
Mathew

---

### Post by cirobr on 2008-11-12
Hello,

I meant by "process freezes" the uploading of the email from the mail client to the smtp server (postfix).

I've placed -v to start with, as suggested. Outcome follows:

Nov 12 19:35:30 note1-server postfix/master[22979]: daemon started -- version 2.5.1, configuration /etc/postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  mail
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  ipv4
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: name_mask: ipv4
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  note1-server.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  Postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  postdrop
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand localhost, $myhostname, $mydomain, localhost.$mydomain -> localhost, note1-server.local.domain, local.domain, localhost.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $mydomain -> local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  [smtp.sao.terra.com.br]
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /usr/lib/postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /var/lib/postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /usr/sbin
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /var/spool/postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  pid
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  all
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  double-bounce
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  nobody
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  hash:/etc/aliases
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  20080216
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  2.5.1
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  hash
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  deferred, defer
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  +
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $mydestination -> localhost, note1-server.local.domain, local.domain, localhost.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $relay_domains -> localhost, note1-server.local.domain, local.domain, localhost.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  TZ MAIL_CONFIG LANG
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  subnet
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  +=
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  -=+
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  bounce
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  cleanup
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  defer
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  pickup
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  qmgr
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  rewrite
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  showq
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  error
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  flush
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  verify
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  trace
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  100s
Nov 12 19:35:38 note1-server last message repeated 3 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3600s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3600s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  5s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  5s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  10s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  10s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1s
Nov 12 19:35:38 note1-server last message repeated 3 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  500s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  500s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  18000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  18000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  127.0.0.0/8, 192.168.0.0/24
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: inet_addr_local: configured 2 IPv4 addresses
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $myhostname ESMTP $mail_name (Ubuntu) -> note1-server.local.domain ESMTP Postfix (Ubuntu)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  resource, software
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 4 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  postmaster
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $virtual_maps -> 
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  hash:/etc/aliases
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand proxy:unix:passwd.byname $alias_maps -> proxy:unix:passwd.byname hash:/etc/aliases
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  noanonymous
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  private/auth-client
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 6 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  CONNECT GET POST
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  <>
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $double_bounce_sender -> double-bounce
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $authorized_verp_clients -> 
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $myhostname -> note1-server.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand ${smtpd_client_connection_limit_exceptions:$mynetworks} -> 127.0.0.0/8, 192.168.0.0/24
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  permit_inet_interfaces
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $smtpd_sasl_security_options -> noanonymous
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /etc/ssl/certs/ssl-cert-snakeoil.pem
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /etc/ssl/private/ssl-cert-snakeoil.key
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $smtpd_tls_dcert_file -> 
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  medium
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  SSLv3, TLSv1
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  md5
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  dovecot
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  j {daemon_name} v
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  {tls_version} {cipher} {cipher_bits} {cert_subject} {cert_issuer}
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  i {auth_type} {auth_authen} {auth_author} {mail_addr}
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  i {rcpt_addr}
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  i
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  2
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  tempfail
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $myhostname -> note1-server.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $mail_name $mail_version -> Postfix 2.5.1
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  yes
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  100s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  100s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  100s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  100s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3600s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3600s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  30s
Nov 12 19:35:38 note1-server last message repeated 3 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: process generation: 3 (3)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: mynetworks ~? debug_peer_list
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: mynetworks ~? fast_flush_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: mynetworks ~? mynetworks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? debug_peer_list
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? fast_flush_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? mynetworks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? permit_mx_backup_networks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? qmqpd_authorized_clients
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? relay_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: permit_mx_backup_networks ~? debug_peer_list
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: permit_mx_backup_networks ~? fast_flush_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: permit_mx_backup_networks ~? mynetworks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: permit_mx_backup_networks ~? permit_mx_backup_networks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: connect to subsystem private/proxymap
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr request = open
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr table = unix:passwd.byname
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr flags = 16448
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/proxymap socket: wanted attribute: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/proxymap socket: wanted attribute: flags
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: 16464
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/proxymap socket: wanted attribute: (list terminator)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_proxy_open: connect to map=unix:passwd.byname status=0 server_flags=fixed|lock|fold_fix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_open: proxy:unix:passwd.byname
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: Compiled against Berkeley DB: 4.6.21?
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: Run-time linked against Berkeley DB: 4.6.21?
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_open: hash:/etc/aliases
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? debug_peer_list
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? fast_flush_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? mynetworks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? permit_mx_backup_networks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? qmqpd_authorized_clients
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? relay_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? smtpd_access_maps
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  ALL:!EXPORT:!LOW:!MEDIUM:+RC4:@STRENGTH
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  ALL:!EXPORT:!LOW:+RC4:@STRENGTH
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  ALL:!EXPORT:+RC4:@STRENGTH
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  ALL:+RC4:@STRENGTH
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  eNULL:!aNULL
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: auto_clnt_create: transport=local endpoint=private/tlsmgr
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: auto_clnt_open: connected to private/tlsmgr
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr request = seed
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr size = 32
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: seed
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: seed
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: Qa0l8TVJSyk+pMiKp+tpFHz4mSm5RatbnPMA1AGSRxo=
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: (list terminator)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr request = policy
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr cache_type = smtpd
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: cachable
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: cachable
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: 1
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: (list terminator)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: fast_flush_domains ~? debug_peer_list
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: fast_flush_domains ~? fast_flush_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: auto_clnt_create: transport=local endpoint=private/anvil
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: connection established
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: master_notify: status 0
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: name_mask: resource
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: name_mask: software
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_create: SASL service=smtp, realm=(null)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: name_mask: noanonymous
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: Connecting
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: auth reply: MECH?PLAIN?plaintext
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: name_mask: plaintext
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: auth reply: VERSION?1?0
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: auth reply: SPID?16764
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: auth reply: CUID?300
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: auth reply: DONE
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_mech_filter: keep mechanism: PLAIN
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: connect from unknown[192.168.0.126]
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_list_match: unknown: no match
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_list_match: 192.168.0.126: no match
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_list_match: unknown: no match
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_list_match: 192.168.0.126: no match
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_hostname: unknown ~? 127.0.0.0/8
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_hostaddr: 192.168.0.126 ~? 127.0.0.0/8
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_hostname: unknown ~? 192.168.0.0/24
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_hostaddr: 192.168.0.126 ~? 192.168.0.0/24
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 220 note1-server.local.domain ESMTP Postfix (Ubuntu)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: < unknown[192.168.0.126]: EHLO [192.168.0.126]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-note1-server.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-PIPELINING
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-SIZE 10240000
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-VRFY
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-ETRN
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-STARTTLS
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-AUTH PLAIN
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_list_match: unknown: no match
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_list_match: 192.168.0.126: no match
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-AUTH=PLAIN
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-ENHANCEDSTATUSCODES
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-8BITMIME
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250 DSN
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: < unknown[192.168.0.126]: AUTH PLAIN AG1hcmluYQBtb3NraXRv
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_first: sasl_method PLAIN, init_response AG1hcmluYQBtb3NraXRv
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: xsasl_dovecot_handle_reply: auth reply: OK?1?user=marina
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 235 2.7.0 Authentication successful
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: < unknown[192.168.0.126]: MAIL FROM:<marina.m.rosa@terra.com.br> SIZE=1337084
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: extract_addr: input: <marina.m.rosa@terra.com.br>
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: smtpd_check_addr: addr=marina.m.rosa@terra.com.br
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: connect to subsystem private/rewrite
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr request = rewrite
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr rule = local
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr address = [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: rewrite_clnt: local: [email]marina.m.rosa@terra.com.br[/email] -> [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr request = resolve
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr sender = 
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr address = [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: transport
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: transport
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: smtp
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: nexthop
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: nexthop
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [smtp.sao.terra.com.br]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: recipient
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: recipient
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 4096
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: resolve_clnt: `' -> `marina.m.rosa@terra.com.br' -> transp=`smtp' host=`[smtp.sao.terra.com.br]' rcpt=`marina.m.rosa@terra.com.br' flags= class=default
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: ctable_locate: install entry key [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: extract_addr: in: <marina.m.rosa@terra.com.br>, result: [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: fsspace: .: block size 4096, blocks free 8119909
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: smtpd_check_queue: blocks 4096 avail 8119909 min_free 0 msg_size_limit 10240000
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250 2.1.0 Ok
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: < unknown[192.168.0.126]: RCPT TO:<ciro.rosa@st.com>
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: extract_addr: input: <ciro.rosa@st.com>
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: smtpd_check_addr: addr=ciro.rosa@st.com
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr request = rewrite
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr rule = local
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr address = [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: rewrite_clnt: local: [email]ciro.rosa@st.com[/email] -> [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr request = resolve
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr sender = 
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr address = [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: transport
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: transport
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: smtp
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: nexthop
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: nexthop
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [smtp.sao.terra.com.br]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: recipient
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: recipient
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 4096
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: resolve_clnt: `' -> `ciro.rosa@st.com' -> transp=`smtp' host=`[smtp.sao.terra.com.br]' rcpt=`ciro.rosa@st.com' flags= class=default
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: ctable_locate: install entry key [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: extract_addr: in: <ciro.rosa@st.com>, result: [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr request = rewrite
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr rule = local
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr address = double-bounce
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [email]double-bounce@local.doma[/email]in
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: rewrite_clnt: local: double-bounce -> [email]double-bounce@local.doma[/email]in
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: >>> START Recipient address RESTRICTIONS <<<
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: generic_checks: name=permit_sasl_authenticated
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: generic_checks: name=permit_sasl_authenticated status=1
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: >>> CHECKING RECIPIENT MAPS <<<
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: ctable_locate: leave existing entry key [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: recipient_canonical_maps: [email]ciro.rosa@st.com[/email]: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? note1-server.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_list_match: st.com: no match
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: recipient_canonical_maps: @st.com: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: mail_addr_find: [email]ciro.rosa@st.com[/email] -> (not found)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: canonical_maps: [email]ciro.rosa@st.com[/email]: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? note1-server.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_list_match: st.com: no match
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: canonical_maps: @st.com: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: mail_addr_find: [email]ciro.rosa@st.com[/email] -> (not found)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: virtual_alias_maps: [email]ciro.rosa@st.com[/email]: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? note1-server.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_list_match: st.com: no match
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: virtual_alias_maps: @st.com: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: mail_addr_find: [email]ciro.rosa@st.com[/email] -> (not found)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: smtpd_check_rewrite: trying: permit_inet_interfaces
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: permit_inet_interfaces: unknown 192.168.0.126
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: before input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping enable_milters
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: after input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: connect to subsystem public/cleanup
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: public/cleanup socket: wanted attribute: queue_id
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: queue_id
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 1B1DB1920D4
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: public/cleanup socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr flags = 178
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: 1B1DB1920D4: client=unknown[192.168.0.126], sasl_method=PLAIN, sasl_username=marina
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250 2.1.5 Ok
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: < unknown[192.168.0.126]: DATA
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 354 End data with <CR><LF>.<CR><LF>

---

### Post by cirobr on 2008-11-12
Hello,

I meant by "process freezes" the uploading of the email from the mail client to the smtp server (postfix).

I've placed -v to start with, as suggested. Outcome follows:

Nov 12 19:35:30 note1-server postfix/master[22979]: daemon started -- version 2.5.1, configuration /etc/postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  mail
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  ipv4
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: name_mask: ipv4
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  note1-server.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  Postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  postdrop
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand localhost, $myhostname, $mydomain, localhost.$mydomain -> localhost, note1-server.local.domain, local.domain, localhost.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $mydomain -> local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  [smtp.sao.terra.com.br]
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /usr/lib/postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /var/lib/postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /usr/sbin
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /var/spool/postfix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  pid
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  all
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  double-bounce
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  nobody
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  hash:/etc/aliases
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  20080216
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  2.5.1
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  hash
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  deferred, defer
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  +
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $mydestination -> localhost, note1-server.local.domain, local.domain, localhost.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $relay_domains -> localhost, note1-server.local.domain, local.domain, localhost.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  TZ MAIL_CONFIG LANG
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  subnet
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  +=
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  -=+
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  bounce
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  cleanup
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  defer
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  pickup
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  qmgr
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  rewrite
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  showq
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  error
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  flush
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  verify
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  trace
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  100s
Nov 12 19:35:38 note1-server last message repeated 3 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3600s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3600s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  5s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  5s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  10s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  10s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1s
Nov 12 19:35:38 note1-server last message repeated 3 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  500s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  500s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  18000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  18000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  127.0.0.0/8, 192.168.0.0/24
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: inet_addr_local: configured 2 IPv4 addresses
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $myhostname ESMTP $mail_name (Ubuntu) -> note1-server.local.domain ESMTP Postfix (Ubuntu)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  resource, software
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 4 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  postmaster
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $virtual_maps -> 
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  hash:/etc/aliases
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand proxy:unix:passwd.byname $alias_maps -> proxy:unix:passwd.byname hash:/etc/aliases
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  noanonymous
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  private/auth-client
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 6 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  CONNECT GET POST
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  <>
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $double_bounce_sender -> double-bounce
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $authorized_verp_clients -> 
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $myhostname -> note1-server.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand ${smtpd_client_connection_limit_exceptions:$mynetworks} -> 127.0.0.0/8, 192.168.0.0/24
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  permit_inet_interfaces
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $smtpd_sasl_security_options -> noanonymous
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /etc/ssl/certs/ssl-cert-snakeoil.pem
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  /etc/ssl/private/ssl-cert-snakeoil.key
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $smtpd_tls_dcert_file -> 
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  medium
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  SSLv3, TLSv1
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  md5
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  dovecot
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  j {daemon_name} v
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  {tls_version} {cipher} {cipher_bits} {cert_subject} {cert_issuer}
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  i {auth_type} {auth_authen} {auth_author} {mail_addr}
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  i {rcpt_addr}
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  i
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  2
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  tempfail
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $myhostname -> note1-server.local.domain
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: expand $mail_name $mail_version -> Postfix 2.5.1
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  yes
Nov 12 19:35:38 note1-server last message repeated 2 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  100s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  100s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  100s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  100s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  1000s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3600s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  3600s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  30s
Nov 12 19:35:38 note1-server last message repeated 3 times
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  300s
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: process generation: 3 (3)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: mynetworks ~? debug_peer_list
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: mynetworks ~? fast_flush_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: mynetworks ~? mynetworks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? debug_peer_list
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? fast_flush_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? mynetworks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? permit_mx_backup_networks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? qmqpd_authorized_clients
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: relay_domains ~? relay_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: permit_mx_backup_networks ~? debug_peer_list
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: permit_mx_backup_networks ~? fast_flush_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: permit_mx_backup_networks ~? mynetworks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: permit_mx_backup_networks ~? permit_mx_backup_networks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: connect to subsystem private/proxymap
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr request = open
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr table = unix:passwd.byname
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr flags = 16448
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/proxymap socket: wanted attribute: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/proxymap socket: wanted attribute: flags
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: 16464
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/proxymap socket: wanted attribute: (list terminator)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_proxy_open: connect to map=unix:passwd.byname status=0 server_flags=fixed|lock|fold_fix
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_open: proxy:unix:passwd.byname
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: Compiled against Berkeley DB: 4.6.21?
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: Run-time linked against Berkeley DB: 4.6.21?
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_open: hash:/etc/aliases
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? debug_peer_list
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? fast_flush_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? mynetworks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? permit_mx_backup_networks
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? qmqpd_authorized_clients
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? relay_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: smtpd_access_maps ~? smtpd_access_maps
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  ALL:!EXPORT:!LOW:!MEDIUM:+RC4:@STRENGTH
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  ALL:!EXPORT:!LOW:+RC4:@STRENGTH
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  ALL:!EXPORT:+RC4:@STRENGTH
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  ALL:+RC4:@STRENGTH
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: dict_eval: const  eNULL:!aNULL
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: auto_clnt_create: transport=local endpoint=private/tlsmgr
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: auto_clnt_open: connected to private/tlsmgr
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr request = seed
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr size = 32
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: seed
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: seed
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: Qa0l8TVJSyk+pMiKp+tpFHz4mSm5RatbnPMA1AGSRxo=
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: (list terminator)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr request = policy
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: send attr cache_type = smtpd
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: status
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: cachable
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: cachable
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute value: 1
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: private/tlsmgr: wanted attribute: (list terminator)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: fast_flush_domains ~? debug_peer_list
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_string: fast_flush_domains ~? fast_flush_domains
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: auto_clnt_create: transport=local endpoint=private/anvil
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: connection established
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: master_notify: status 0
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: name_mask: resource
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: name_mask: software
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_create: SASL service=smtp, realm=(null)
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: name_mask: noanonymous
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: Connecting
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: auth reply: MECH?PLAIN?plaintext
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: name_mask: plaintext
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: auth reply: VERSION?1?0
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: auth reply: SPID?16764
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: auth reply: CUID?300
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_connect: auth reply: DONE
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_mech_filter: keep mechanism: PLAIN
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: connect from unknown[192.168.0.126]
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_list_match: unknown: no match
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_list_match: 192.168.0.126: no match
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_list_match: unknown: no match
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_list_match: 192.168.0.126: no match
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_hostname: unknown ~? 127.0.0.0/8
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_hostaddr: 192.168.0.126 ~? 127.0.0.0/8
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_hostname: unknown ~? 192.168.0.0/24
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: match_hostaddr: 192.168.0.126 ~? 192.168.0.0/24
Nov 12 19:35:38 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 220 note1-server.local.domain ESMTP Postfix (Ubuntu)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: < unknown[192.168.0.126]: EHLO [192.168.0.126]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-note1-server.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-PIPELINING
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-SIZE 10240000
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-VRFY
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-ETRN
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-STARTTLS
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-AUTH PLAIN
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_list_match: unknown: no match
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_list_match: 192.168.0.126: no match
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-AUTH=PLAIN
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-ENHANCEDSTATUSCODES
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250-8BITMIME
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250 DSN
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: < unknown[192.168.0.126]: AUTH PLAIN AG1hcmluYQBtb3NraXRv
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: xsasl_dovecot_server_first: sasl_method PLAIN, init_response AG1hcmluYQBtb3NraXRv
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: xsasl_dovecot_handle_reply: auth reply: OK?1?user=marina
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 235 2.7.0 Authentication successful
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: < unknown[192.168.0.126]: MAIL FROM:<marina.m.rosa@terra.com.br> SIZE=1337084
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: extract_addr: input: <marina.m.rosa@terra.com.br>
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: smtpd_check_addr: addr=marina.m.rosa@terra.com.br
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: connect to subsystem private/rewrite
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr request = rewrite
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr rule = local
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr address = [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: rewrite_clnt: local: [email]marina.m.rosa@terra.com.br[/email] -> [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr request = resolve
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr sender = 
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr address = [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: transport
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: transport
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: smtp
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: nexthop
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: nexthop
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [smtp.sao.terra.com.br]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: recipient
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: recipient
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 4096
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: resolve_clnt: `' -> `marina.m.rosa@terra.com.br' -> transp=`smtp' host=`[smtp.sao.terra.com.br]' rcpt=`marina.m.rosa@terra.com.br' flags= class=default
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: ctable_locate: install entry key [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: extract_addr: in: <marina.m.rosa@terra.com.br>, result: [email]marina.m.rosa@terra.com.br[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: fsspace: .: block size 4096, blocks free 8119909
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: smtpd_check_queue: blocks 4096 avail 8119909 min_free 0 msg_size_limit 10240000
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250 2.1.0 Ok
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: < unknown[192.168.0.126]: RCPT TO:<ciro.rosa@st.com>
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: extract_addr: input: <ciro.rosa@st.com>
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: smtpd_check_addr: addr=ciro.rosa@st.com
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr request = rewrite
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr rule = local
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr address = [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: rewrite_clnt: local: [email]ciro.rosa@st.com[/email] -> [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr request = resolve
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr sender = 
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr address = [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: transport
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: transport
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: smtp
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: nexthop
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: nexthop
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [smtp.sao.terra.com.br]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: recipient
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: recipient
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 4096
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: resolve_clnt: `' -> `ciro.rosa@st.com' -> transp=`smtp' host=`[smtp.sao.terra.com.br]' rcpt=`ciro.rosa@st.com' flags= class=default
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: ctable_locate: install entry key [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: extract_addr: in: <ciro.rosa@st.com>, result: [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr request = rewrite
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr rule = local
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr address = double-bounce
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: flags
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 0
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: address
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: [email]double-bounce@local.doma[/email]in
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: private/rewrite socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: rewrite_clnt: local: double-bounce -> [email]double-bounce@local.doma[/email]in
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: >>> START Recipient address RESTRICTIONS <<<
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: generic_checks: name=permit_sasl_authenticated
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: generic_checks: name=permit_sasl_authenticated status=1
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: >>> CHECKING RECIPIENT MAPS <<<
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: ctable_locate: leave existing entry key [email]ciro.rosa@st.com[/email]
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: recipient_canonical_maps: [email]ciro.rosa@st.com[/email]: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? note1-server.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_list_match: st.com: no match
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: recipient_canonical_maps: @st.com: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: mail_addr_find: [email]ciro.rosa@st.com[/email] -> (not found)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: canonical_maps: [email]ciro.rosa@st.com[/email]: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? note1-server.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_list_match: st.com: no match
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: canonical_maps: @st.com: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: mail_addr_find: [email]ciro.rosa@st.com[/email] -> (not found)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: virtual_alias_maps: [email]ciro.rosa@st.com[/email]: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? note1-server.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_string: st.com ~? localhost.local.domain
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: match_list_match: st.com: no match
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: maps_find: virtual_alias_maps: @st.com: not found
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: mail_addr_find: [email]ciro.rosa@st.com[/email] -> (not found)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: smtpd_check_rewrite: trying: permit_inet_interfaces
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: permit_inet_interfaces: unknown 192.168.0.126
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: before input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping enable_milters
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: after input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: connect to subsystem public/cleanup
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: public/cleanup socket: wanted attribute: queue_id
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: queue_id
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute value: 1B1DB1920D4
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: public/cleanup socket: wanted attribute: (list terminator)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: input attribute name: (end)
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: send attr flags = 178
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: 1B1DB1920D4: client=unknown[192.168.0.126], sasl_method=PLAIN, sasl_username=marina
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 250 2.1.5 Ok
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: < unknown[192.168.0.126]: DATA
Nov 12 19:35:39 note1-server postfix/smtpd[22986]: > unknown[192.168.0.126]: 354 End data with <CR><LF>.<CR><LF>

---

### Post by MJN on 2008-11-13
It is certainly getting to the stage of Postfix asking for the message body... so I wonder what's happening then?
 
Only sure way to find out is to run a packet sniffer and see what's happening on the wire. In particular, see what is happening immediately following the final '354 End data with <CR><LF>.<CR><LF>' statement from the server.
 
You could always save the trace as a libpcap file and attach it your post if you need help diagnosing it (packet captures don't copy-and-paste well as they are multi-layered).
 
Mathew

---

### Post by cirobr on 2008-11-13
Hello Mathew,

I've found these options for sniffers. Any particular recommendation?

[http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html](http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html)

Thanks,

Ciro.

---

### Post by MJN on 2008-11-13
I've only ever used Ethereal (now called Wireshark) and for that reason alone it is my recommendation. However, it is widely known - indeed 'Ethereal' has almost become a generic term for a packet sniffer in many circles which has got to mean something.
 
(it kind of makes you wonder why they changed the name to Wireshark doesn't it?!)
 
Mathew

---

### Post by cirobr on 2008-12-08
Hello MJN,

Thanks for the tip. I'll need a bit more time to dig into it.

I strongly suspect neither postfix nor Thunderbird are the problem: I've found same behaviour when sending large files over WIFI from one computer to another, within the same network. So far, playing with MTA gave me no result.

I'll certainly get back to more comments here.

---

### Post by MJN on 2008-12-08
> **cirobr said:**
> [...] I've found same behaviour when sending large files over WIFI from one computer to another, within the same network.Ah, right. I wrongly assumed Thunderbird and Postfix had also been tested on the same machine.
 
This is an easy one to eliminate - just install Thunderbird on the server and retest. If you still get the problem then you can rule out the network.
 
Mathew

---

### Post by cirobr on 2008-12-22
Hello MJN,

I did nothing since my last post. However, problem is now solved, apparently thanks to the updates from Ubuntu. To me, case is closed.

---

