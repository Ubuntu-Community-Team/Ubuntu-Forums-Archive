---
title: "Postfix mail loop"
date: 2015-04-18
forum: Server Platforms
---

### Post by bbell2000 on 2015-04-18
I've just configured postfix on a newly installed server and everything is working except mail sent to root on that host.

The details:

This server is a mail gateway. I want it to accept email from the outside for the two domains I manage and forward that mail for those domains to another server. I also want it to accept and send mail destined for external domains. Finally, I want it to send mail for postmaster, abuse and root to a user on one of the domains I manage.

Everything is working in both directions except mail sent to root-at-server-domain. In that case, I keep getting delivery failures like this one:

```

<root-at-server-domain>:
172.30.1.3 failed after I sent the message.
Remote host said: 554 5.4.0 Error: too many hops

```

My config:

```
sudo postconf alias_maps
alias_maps = hash:/etc/aliases

```

```
$ cat /etc/aliases
postmaster:    <snip>@theotherbell.com
abuse:  <snip>@theotherbell.com
root:   <snip>@theotherbell.com

```

```
$ cat virtual
postmaster      <snip>@theotherbell.com
abuse   <snip>@theotherbell.com
root    <snip>@theotherbell.com

```

```
$ cat relay_recipients
@theotherbell.com OK
@brendaabell.com OK

```

```
$ cat main.cf
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# Commented on install 18-Apr-2015
#smtpd_relay_restrictions = check_client_access hash:/etc/postfix/client_checks, permit_mynetworks reject__unauth_destination
myhostname = saturn.theotherbell.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
# Changed on install 18-Apr-2015
myorigin = theotherbell.com
# Commented on install 18-Apr-2015
mydestination =
relayhost = smtp.theotherbell.com
# Changed on install 18-Apr-2015
mynetworks = 127.0.0.0/8 172.30.0.0/16
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all

# Added on install 18-Apr-2015
relay_domains = theotherbell.com, brendaabell.com
relay_recipient_maps = hash:/etc/postfix/relay_recipients
transport_maps = hash:/etc/postfix/transport
local_recipient_maps =
local_transport = error:local mail delivery is disabled
virtual_alias_maps = hash:/etc/postfix/virtual
parent_domain_matches_subdomains = debug_peer_list smtpd_access_maps
smtpd_recipient_restrictions = check_client_access hash:/etc/postfix/client_checks, permit_mynetworks reject_unauth_destination

```

I've rebuilt the hashes (newaliases & postmap) and restarted the server.

The top part of the loop looks like this (the bottom part is just more of the same):

```
Received: from smtp.theotherbell.com (snappy.theotherbell.com [172.30.1.6])
	by saturn.theotherbell.com (Postfix) with SMTP id E2904120BF2
	for <root-at-server-domain>; Sat, 18 Apr 2015 14:24:58 -0400 (EDT)
Received: (qmail 25787 invoked by uid 1022); 18 Apr 2015 18:18:00 -0000
Received: from saturn.theotherbell.com by snappy (envelope-from <user-at-domain>, uid 1015) with qmail-scanner-2.05 
(clamdscan: 0.92.1/8666. spamassassin: 3.2.5. perlscan: 2.05st.  
Clear:RC:1(172.30.1.3):. 
Processed in 0.025293 secs); 18 Apr 2015 18:18:00 -0000
Received: from saturn.theotherbell.com (172.30.1.3)
 by smtp.theotherbell.com with SMTP; 18 Apr 2015 18:18:00 -0000
Received: from smtp.theotherbell.com (snappy.theotherbell.com [172.30.1.6])
	by saturn.theotherbell.com (Postfix) with SMTP id B6D36120BF1
	for <root-at-server-domain>; Sat, 18 Apr 2015 14:24:58 -0400 (EDT)
Received: (qmail 25777 invoked by uid 1022); 18 Apr 2015 18:18:00 -0000
Received: from saturn.theotherbell.com by snappy (envelope-from <user-at-domain>, uid 1015) with qmail-scanner-2.05 
(clamdscan: 0.92.1/8666. spamassassin: 3.2.5. perlscan: 2.05st.  
Clear:RC:1(172.30.1.3):. 
Processed in 0.025289 secs); 18 Apr 2015 18:18:00 -0000
Received: from saturn.theotherbell.com (172.30.1.3)
 by smtp.theotherbell.com with SMTP; 18 Apr 2015 18:18:00 -0000
Received: from smtp.theotherbell.com (snappy.theotherbell.com [172.30.1.6])
	by saturn.theotherbell.com (Postfix) with SMTP id 8732A120BF1
	for <root-at-server-domain>; Sat, 18 Apr 2015 14:24:58 -0400 (EDT)
Received: (qmail 25767 invoked by uid 1022); 18 Apr 2015 18:18:00 -0000
Received: from saturn.theotherbell.com by snappy (envelope-from <user-at-domain>, uid 1015) with qmail-scanner-2.05 
(clamdscan: 0.92.1/8666. spamassassin: 3.2.5. perlscan: 2.05st.  
Clear:RC:1(172.30.1.3):. 
Processed in 0.025216 secs); 18 Apr 2015 18:18:00 -0000
Received: from saturn.theotherbell.com (172.30.1.3)
 by smtp.theotherbell.com with SMTP; 18 Apr 2015 18:17:59 -0000
Received: from [172.30.1.70] (unknown [172.30.1.70])
	by saturn.theotherbell.com (Postfix) with ESMTPS id 3F5AD120BF1
	for <root-at-server-domain>; Sat, 18 Apr 2015 14:24:58 -0400 (EDT)

```

What'd I miss?

---

