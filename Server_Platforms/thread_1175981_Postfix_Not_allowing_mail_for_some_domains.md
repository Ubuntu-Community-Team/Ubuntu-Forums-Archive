---
title: "Postfix Not allowing mail for some domains"
date: 2009-06-01
forum: Server Platforms
---

### Post by jdrost on 2009-06-01
We are having an issue where we cannot accept mail from some doamins. results of the postfix -n here 
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
debug_peer_list = my domains I am debugging
inet_interfaces = all
inet_protocols = ipv4
local_recipient_maps = 
local_transport = error:local mail delivery is disabled
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = $mydomain
myhostname = mydomain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = my domain
parent_domain_matches_subdomains = debug_peer_list smtpd_access_maps
readme_directory = no
recipient_delimiter = +
relay_domains = cmmy relay domains
relay_recipient_maps = 
relayhost = 192.168.1.8
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_helo_restrictions = check_helo_access hash:/etc/postfix/helo_whitelist
smtpd_recipient_restrictions = permit_mynetworks reject_unauth_destination check_client_access hash:/etc/postfix/whitelist reject_rbl_client bl.spamcop.net
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = no
transport_maps = hash:/etc/postfix/transport
virtual_alias_maps = hash:/etc/postfix/virtual






	Many legit domains are getting dropped almost immediately before any RBL or content checks occur?


Jun  1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 220 mailserver.mydomain.com ESMTP Postfix (Ubuntu)
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: watchdog_pat: 0xb9b7f478
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: < mx1.mail.twtelecom.net[64.129.67.68]: EHLO mx1.mail.twtelecom.net
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-mailserver.mydomain.com
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-PIPELINING
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-SIZE 10240000
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-VRFY
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: match_list_match: mx1.mail.twtelecom.net: no match
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: match_list_match: 64.129.67.68: no match
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-ETRN
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-ENHANCEDSTATUSCODES
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-8BITMIME
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250 DSN
Jun  1 16:46:20 mailserver postfix/smtpd[12349]: watchdog_pat: 0xb9b7f478
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: smtp_get: EOF
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: match_hostname: mx1.mail.twtelecom.net ~? 127.0.0.0/8
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: match_hostaddr: 64.129.67.68 ~? 127.0.0.0/8
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: match_hostname: mx1.mail.twtelecom.net ~? [::ffff:127.0.0.0]/104
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: match_hostaddr: 64.129.67.68 ~? [::ffff:127.0.0.0]/104
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: match_hostname: mx1.mail.twtelecom.net ~? [::1]/128
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: match_hostaddr: 64.129.67.68 ~? [::1]/128
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: match_list_match: mx1.mail.twtelecom.net: no match
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: match_list_match: 64.129.67.68: no match
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: send attr request = disconnect
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: send attr ident = smtp:64.129.67.68
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: private/anvil: wanted attribute: status
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: input attribute name: status
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: input attribute value: 0
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: private/anvil: wanted attribute: (list terminator)
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: input attribute name: (end)
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: lost connection after EHLO from mx1.mail.twtelecom.net[64.129.67.68]
Jun  1 16:46:21 mailserver postfix/smtpd[12349]: disconnect from mx1.mail.twtelecom.net[64.129.67.68]

---

### Post by gombadi on 2009-06-01
> 
Jun 1 16:48:29 mailserver postfix/smtpd[12349]: NOQUEUE: reject: RCPT from 201-95-229-71.dsl.telesp.net.br[201.95.229.71]: 554 5.7.1 Service unavailable; Client host [201.95.229.71] blocked using bl.spamcop.net; Blocked - see [http://www.spamcop.net/bl.shtml?201.95.229.71;](http://www.spamcop.net/bl.shtml?201.95.229.71;) from=<misjhlw@bradleyallen.com.au> to=<carolineprice@mydomain.com> proto=ESMTP helo=<pc-casa>


Sometimes debug output can flood the screen and cover up the problem.

Have you been to the link above to see if that is the cause of the problem you are having?

---

### Post by jdrost on 2009-06-02
My real concern is the following entries that get dropped before the RBL lookup?

Jun 1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 220 mailserver.mydomain.com ESMTP Postfix (Ubuntu)
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: watchdog_pat: 0xb9b7f478
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: < mx1.mail.twtelecom.net[64.129.67.68]: EHLO mx1.mail.twtelecom.net
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-mailserver.mydomain.com
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-PIPELINING
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-SIZE 10240000
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-VRFY
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: match_list_match: mx1.mail.twtelecom.net: no match
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: match_list_match: 64.129.67.68: no match
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-ETRN
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-ENHANCEDSTATUSCODES
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250-8BITMIME
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: > mx1.mail.twtelecom.net[64.129.67.68]: 250 DSN
Jun 1 16:46:20 mailserver postfix/smtpd[12349]: watchdog_pat: 0xb9b7f478
Jun 1 16:46:21 mailserver postfix/smtpd[12349]: smtp_get: EOF
Jun 1 16:46:21 mailserver postfix/smtpd[12349]: match_hostname: mx1.mail.twtelecom.net ~? 127.0.0.0/8
Jun 1 16:46:21 mailserver postfix/smtpd[12349]: match_hostaddr: 64.129.67.68 ~? 127.0.0.0/8
Jun 1 16:46:21 mailserver postfix/smtpd[12349]: match_hostname: mx1.mail.twtelecom.net ~? [::ffff:127.0.0.0]/104
Jun 1 16:46:21 mailserver postfix/smtpd[12349]: match_hostaddr: 64.129.67.68 ~? [::ffff:127.0.0.0]/104
Jun 1 16:46:21 mailserver postfix/smtpd[12349]: match_hostname: mx1.mail.twtelecom.net ~? [::1]/128
Jun 1 16:46:21 mailserver postfix/smtpd[12349]: match_hostaddr: 64.129.67.68 ~? [::1]/128
Jun 1 16:46:21 mailserver postfix/smtpd[12349]: match_list_match: mx1.mail.twtelecom.net: no match
Jun 1 16:46:21 mailserver postfix/smtpd[12349]: match_list_match: 64.129.67.68: no match
Jun 1 16:46:21 mailserver postfix/smtpd[12349]: send attr request = disconnect

---

### Post by eugenevdm on 2010-01-12
I have similar entries in my log file. On our network port 25 is DST-NATted and we get these entries when using an Outlook client that has authentication enabled. I am hoping to find a solution for still using DST-NAT port 25 WITH authentication enabled. Configuring Postfix to allow these connections as such...

---

