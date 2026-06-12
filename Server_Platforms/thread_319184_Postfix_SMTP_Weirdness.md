---
title: "Postfix SMTP Weirdness"
date: 2006-12-15
forum: Server Platforms
---

### Post by Blairboy on 2006-12-15
I'm a bit odded out right now, because up until late, my server was doing just fine.  Now, remote access to port 25 doesn't work.  If I try to send mail or telnet into the server from anywhere other than LAN it times out.  I can still send mail through webmail.  The port is open from my ISP and nothing has changed that I know of.  I'm running dapper and postfix+dovecot+various other modules.  Any help would be greatly appreciated.  Thanks.

---

### Post by MJN on 2006-12-15
Could your ISP be now blocking port 25?
 
Mathew

---

### Post by Blairboy on 2006-12-15
Nope.  But I made sure with a portscan yesterday.  Still open.

---

### Post by MJN on 2006-12-15
(Oops, sorry - missed that you already confirmed it was still open)
 
Hmmm...
 
Okay, a simple checklist then;
 
- Is Postfix running? *Yes, as you can connect to it from elsewhere on the LAN*
- Is it listening on port 25? *Yes, as you can connect to it from the elsewhere on the LAN*
- Is port 25 being forwarded properly from your WAN connection? *Yes, because the port scan revealed it to be open - presumably this was by listening for a response on that port*
 
What's the exact client message you get when telnetting to your server on port 25? Do your mail logs say anything when you try and connect from the WAN? Can you run a packet sniffer (e.g. Ethereal) to see if packets are reaching your server and, if so, what those packets are?
 
Mathew

---

### Post by chrisfay on 2006-12-15
> If I try to send mail or telnet into the server from anywhere other than LAN it times out.

So relaying fails, but sending locally succeeds? How about receving mail?

---

### Post by Blairboy on 2006-12-15
Receiving is just fine.

---

### Post by MJN on 2006-12-15
What do the logs say? Can you connect at all?

Come on Blairboy, the batteries in our crystal balls have run out! ;)

Mathew

---

### Post by Blairboy on 2006-12-15
Sorry.  When I try to send from outside the LAN, mail.log and syslog don't say anything.  I was looking at my postfix config files earlier and checking them against the docs on flurdy.com.  In main.cf I have this "relayhost = " because I thought I was supposed to leave it blank to do the relaying myself.  I tried changing it to my static IP address earlier but nothing changed.  For reference, here's what syslog yields when I send a mail through squirrelmail ```
Dec 15 16:36:21 Server postfix/smtpd[10683]: connect from localhost[127.0.0.1]
Dec 15 16:36:21 Server postfix/smtpd[10683]: B588D30C159: client=localhost[127.0.0.1]
Dec 15 16:36:21 Server postfix/cleanup[10688]: B588D30C159: message-id=<37462.64.218.162.130.1166222181.squirrel@webmail.kincke.com>
Dec 15 16:36:21 Server postfix/smtpd[10683]: disconnect from localhost[127.0.0.1]
Dec 15 16:36:21 Server postfix/qmgr[4853]: B588D30C159: from=<meade@kincke.com>, size=716, nrcpt=1 (queue active)
Dec 15 16:36:21 Server amavis[4451]: (04451-10) ESMTP::10024 /var/lib/amavis/tmp/amavis-20061214T211803-04451: <meade@kincke.com> -> <kincke@gmail.com> Received: SIZE=716 BODY=8BITMIME from mail.kincke.com ([127.0.0.1]) by localhost (mail.kincke.com [127.0.0.1]) (amavisd-new, port 10024) with ESMTP id 04451-10 for <kincke@gmail.com>; Fri, 15 Dec 2006 16:36:21 -0600 (CST)
Dec 15 16:36:21 Server amavis[4451]: (04451-10) Checking: 1MWZttUFHd2z [127.0.0.1] <meade@kincke.com> -> <kincke@gmail.com>
Dec 15 16:36:21 Server amavis[4451]: (04451-10) p001 1 Content-Type: text/plain, size: 2 B, name:
Dec 15 16:36:21 Server postfix/smtpd[10693]: connect from localhost[127.0.0.1]
Dec 15 16:36:21 Server postfix/smtpd[10693]: E482A30C15B: client=localhost[127.0.0.1]
Dec 15 16:36:21 Server postfix/cleanup[10695]: E482A30C15B: message-id=<37462.64.218.162.130.1166222181.squirrel@webmail.kincke.com>
Dec 15 16:36:22 Server postfix/qmgr[4853]: E482A30C15B: from=<meade@kincke.com>, size=1093, nrcpt=1 (queue active)
Dec 15 16:36:22 Server postfix/smtpd[10693]: disconnect from localhost[127.0.0.1]
Dec 15 16:36:22 Server amavis[4451]: (04451-10) FWD via SMTP: <meade@kincke.com> -> <kincke@gmail.com>, BODY=8BITMIME, 250 2.6.0 Ok, id=04451-10, from MTA([127.0.0.1]:10025): 250 Ok: queued as E482A30C15B
Dec 15 16:36:22 Server amavis[4451]: (04451-10) Passed CLEAN, LOCAL [127.0.0.1] [64.218.162.130] <meade@kincke.com> -> <kincke@gmail.com>, Message-ID: <37462.64.218.162.130.1166222181.squirrel@webmail.kincke.com>, mail_id: 1MWZttUFHd2z, Hits: -, 191 ms
Dec 15 16:36:22 Server amavis[4451]: (04451-10) TIMING [total 195 ms] - SMTP EHLO: 5 (2%)2, SMTP pre-MAIL: 1 (1%)3, SMTP pre-DATA-flush: 2 (1%)4, SMTP DATA: 37 (19%)23, body_digest: 1 (1%)24, gen_mail_id: 0 (0%)24, mime_decode: 8 (4%)28, get-file-type1: 9 (4%)32, decompose_part: 0 (0%)33, parts_decode: 0 (0%)33, update_cache: 3 (1%)34, fwd-connect: 37 (19%)53, fwd-mail-from: 3 (1%)55, fwd-rcpt-to: 19 (10%)64, write-header: 1 (1%)65, fwd-data: 0 (0%)65, fwd-data-end: 53 (27%)92, fwd-rundown: 2 (1%)93, main_log_entry: 11 (6%)99, update_snmp: 1 (1%)99, unlink-1-files: 1 (1%)100, rundown: 0 (0%)100
Dec 15 16:36:22 Server postfix/smtp[10690]: B588D30C159: to=<kincke@gmail.com>, relay=127.0.0.1[127.0.0.1], delay=1, status=sent (250 2.6.0 Ok, id=04451-10, from MTA([127.0.0.1]:10025): 250 Ok: queued as E482A30C15B)
Dec 15 16:36:22 Server postfix/qmgr[4853]: B588D30C159: removed
Dec 15 16:36:22 Server amavis[4451]: (04451-10) Requesting process rundown after 10 tasks (and 10 sessions)
Dec 15 16:36:22 Server amavis[10698]: TIMING [total 6 ms] - bdb-open: 6 (100%)100, rundown: 0 (0%)100
Dec 15 16:36:23 Server postfix/smtp[10697]: E482A30C15B: to=<kincke@gmail.com>, relay=gmail-smtp-in.l.google.com[72.14.247.27], delay=2, status=sent (250 2.0.0 OK 1166222133 20si3434790agb)
Dec 15 16:36:23 Server postfix/qmgr[4853]: E482A30C15B: removed
```

Sorry about the lack of input guys.  Was spacey and trying to figure something out earlier with no luck.
Also, being that I didn't change any config files, anybody got any ideas why my server would change seemingly on its own to stop relaying?

---

### Post by Blairboy on 2006-12-15
Another addition, my main.cf file.  See if there's anything obviously wrong with it.  ```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.kincke.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = kincke.com, Server, localhost.localdomain, localhost
mydestination = $myhostname, localhost.$mydomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
masquerade_domains = mail.kincke.com !kincke.com
masquerade_exceptions = root
local_recipient_maps =
# how long if undelivered before sending warning update to sender
delay_warning_time = 4h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed
# some have 3 days, I have 16 days as I am backup server for some peopl
# whom go on holiday with their server switched off
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s
# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 16
# how many error before back off.
smtpd_soft_error_limit = 3
# how many max errors before blocking it.
smtpd_hard_error_limit = 12
# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes
# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and their user id
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
# and group id
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

content_filter = amavis:[127.0.0.1]:10024
#receieve_override_options = no_address_mappings


#adding the postgrey policy:
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit


# modify the existing smtpd_recipient_restrictions
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit

# modify the existing smtpd_sender_restrictions
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

# then add these
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = 


smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_data_restrictions = reject_unauth_pipelining

```

---

### Post by Blairboy on 2006-12-15
I think I've figured out the problem.  I'm staying at my friend's house currently, and I can't connect to SMTP on any server through thunderbird.  So either her router or ISP is blocking access to it because I can't even connect to my school account.

---

### Post by MJN on 2006-12-16
I can telnet to your server just fine. What do you get when you do **telnet your.server 25** ?

(I just sent you a mail manually in case you're wondering where it came from)

Surely your logs must say something when you connect, if only directly via telnet on port 25? If not, try adding a -v to the end of the **smtpd** on the **smtp **line in /etc/postfix/master.cf and restart Postfix. Post your logs covering the period of time when you connect via telnet on port 25 (and/or using Thunderbird etc).

Incidentally, I notice your server is allowing usernames/password in the clear - you can stop this (i.e. force clients to use TLS before sending usernames/passwords) with **smtpd_tls_auth_only = yes**

Mathew

---

### Post by chrisfay on 2006-12-16
> I think I've figured out the problem. I'm staying at my friend's house currently, and I can't connect to SMTP on any server through thunderbird. So either her router or ISP is blocking access to it because I can't even connect to my school account.

I had the exact same problem last week trying to relay mail through my mail server at my mother-in-law's. Just about dismantled the entire thing until I realised...duh....Cox blocks port 25.](*,) 

Hope it was that easy for you....

---

