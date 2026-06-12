---
title: "[SOLVED] Postfix Relaying - Spam Attacks"
date: 2007-12-17
forum: Server Platforms
---

### Post by The Foz on 2007-12-17
My postfix email server is being attacked by spammers trying to relay vast quantities of spam.

I thought my postfix setup was pretty secure, but apparently not. I have had to shut down postfix.

In a 24 hour period close to 4GB of mail logs (mail.log & mail.info) were generated.

I tightened up the security settings, to the point where I can no longer send email myself, but the spammer(s) keep getting in. The spamming seems to be intelligent - the nature of the traffic seems to adapt after a few seconds to any changes that I make to security settings. I am finding hundreds of emails arriving in /var/spool/postfix/active, every minute. It looks like these are not just failure notifications being sent back to the supposed source (the majority of attempts are being rejected), but also real outbound spam emails waiting to be sent.

I need my email server to:
[LIST]
[*]Receive emails for holders of local domain accounts
[*]Allow holders of local accounts to send emails (including from remote clients like Outlook)
[*]Not act as an open relay
[/LIST]

I am using SASL2 for authentication.

This is my (anonymised) postfix main.cf:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname
myhostname = mail.mydomainname.com
mydomain = mydomainname.com
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed.
maximal_queue_lifetime = 30d 

# max and min time in seconds between retries if connection failed 
minimal_backoff_time = 1000s 
maximal_backoff_time = 8000s 

# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s 

# how many address can be used in one message. 
# effective stopper to mass spammers, accidental copy in whole address list 
# but may restrict intentional mail shots. 
# smtpd_recipient_limit = 16 

# how many error before back off. 
# smtpd_soft_error_limit = 3 
# how many max errors before blocking it. 
# smtpd_hard_error_limit = 12

# TLS parameters
# smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
# smtpd_use_tls=yes

smtpd_use_tls = yes 
smtpd_tls_cert_file = /etc/postfix/postfix.cert 
smtpd_tls_key_file = /etc/postfix/postfix.key 
smtpd_data_restrictions = reject_unauth_pipelining

smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

# myhostname = df-server1
# alias_maps = hash:/etc/aliases
# alias_database = hash:/etc/aliases

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

myorigin = /etc/mailname
mydestination =  $myhostname, df-server1, localhost.$mydomain
relay_domains = billing-components.com, gmx.net, plus.cablesurf.de
relayhost = 
#mynetworks = 127.0.0.0/8, 192.168.0.0/24, 194.105.97.206/32, 88.217.0.0/16, 0.0.0.0/0
mynetworks = 127.0.0.0/8 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
#masquerade_domains = mydomainname.com

# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_helo_hostname, reject_invalid_helo_hostname , permit 
#smtpd_helo_restrictions =  permit
# Requirements for the sender details 
#smtpd_sender_restrictions =  permit 
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, reject_sender_login_mismatch, permit 
# Requirements for the connecting server 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org, reject_sender_login_mismatch 
#smtpd_client_restrictions = permit 
# Requirement for the recipient address 
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
#smtpd_recipient_restrictions =  permit_mynetworks, reject_unknown_recipient_domain, reject_unauth_destination

# check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit

# require proper helo at connections 
smtpd_helo_required = yes 
# waste spammers time before rejecting them 
smtpd_delay_reject = yes 
disable_vrfy_command = yes


# then add these 
smtpd_sasl_auth_enable = yes 
smtpd_sasl_type = cyrus
broken_sasl_auth_clients = yes 
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2 
# smtpd_sasl_path = smtpd
smtpd_sasl_application_name = smtpd
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname

```

Can someone help, please?

---

### Post by MJN on 2007-12-17
Post an excerpt from your log showing one of these spam messages being accepted and delivered. Do not alter any of the details of the log.

If you're not relaying the messages then there's little you can do as presumably they are not all originating from the same client?

Mathew

---

### Post by GigaVolt on 2007-12-17
My hint is:
```
dancho@thoth:~ > apt-cache search postfix grey listing
greylistd - Greylisting daemon for use with Exim 4
postfix-gld - greylisting daemon for postfix, written in C, uses MySQL
postfix-policyd - anti-spam plugin for Postfix
postgrey - greylisting implementation for Postfix
whitelister - a Postfix Whitelister daemon
dancho@thoth:~ >

```

---

### Post by koenn on 2007-12-17
> **The Foz said:**
> 
I need my email server to:
[LIST]
[*]Receive emails for holders of local domain accounts
[*]Allow holders of local accounts to send emails (including from remote clients like Outlook)
[*]Not act as an open relay
[/LIST]
sounds reasonable.

The basic "no relay" config is to tell the mail server for which domain(s) it handles the mail (eg my.com)
1- allow only outgoing mail FROM (addresses @ ) my.com
          this will still allow your clients to send spam, or 
          allow spammers to spoof a sender address but
          should prevent 'foreign' senders to send throug your server (to recipients not in your somain)

2- allow only incoming mail TO (addresses @ ) my.com, and preferably check that the destination address exists on the server (i.e. there is a mailbox for that server)
           this doesn't stop spam to your clients, but there"s other measures (blacklists, spam filters) to handle that

All the rest is relaying : mail from a foreign domain to a froreign domain is relayed mail that your server should refuse. 

I don't know postfix, so I can't tell from the config file wether you've implemented this, and if so, where the loopholes are, but maybe you can check that 
I notice that you commented out
#myorigin = /etc/mailname

could it be that your not checking case 1- ?


other than that - as MJN said : check the logs, look for patters or other clues in the relayed message, to try and find how people manage to relay through your server

---

### Post by rsw686 on 2007-12-17
Here's part of my configuration. I haven't had any issues with spammers relaying.

```

smtpd_helo_required = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions =
        permit_mynetworks,
        permit_sasl_authenticated,
        reject_non_fqdn_sender,
        reject_unknown_sender_domain,
        reject_non_fqdn_recipient,
        reject_unknown_recipient_domain,
        reject_unauth_destination,
        reject_rbl_client zen.spamhaus.org,
        reject_rbl_client bl.spamcop.net,
        permit

```

---

### Post by ronald.higgins on 2007-12-20
I would second the Greylist addition to your MX Host.

rH

---

### Post by The Foz on 2007-12-23
Here is a recent section of my mail.log file.
```
Dec 22 07:41:31 df-server1 postfix/qmgr[6709]: F30AE64FA2A: from=<>, size=3884, nrcpt=1 (queue active)
Dec 22 07:41:32 df-server1 postfix/qmgr[6709]: B3BF364E5EE: from=<>, size=3869, nrcpt=1 (queue active)
Dec 22 07:41:32 df-server1 postfix/qmgr[6709]: warning: connect to transport retry: No such file or directory
Dec 22 07:41:32 df-server1 postfix/qmgr[6709]: B3BF364E5EE: to=<sfyj@cm1.hinet.net>, relay=none, delay=156030, delays=156030/0.07/0/0, dsn=4.3.0, status=deferred (ma
il transport unavailable)
Dec 22 07:41:32 df-server1 postfix/qmgr[6709]: BD3453A2797: from=<>, size=6096, nrcpt=1 (queue active)
Dec 22 07:41:32 df-server1 postfix/qmgr[6709]: B676164F632: from=<>, size=5546, nrcpt=1 (queue active)
Dec 22 07:41:32 df-server1 postfix/qmgr[6709]: B238B64D1A0: from=<>, size=3633, nrcpt=1 (queue active)
Dec 22 07:41:32 df-server1 postfix/qmgr[6709]: B238B64D1A0: to=<louischristine@cm1.hinet.net>, relay=none, delay=147721, delays=147721/0.04/0/0, dsn=4.4.1, status=de
ferred (delivery temporarily suspended: connect to cm1a.hinet.net[168.95.5.44]: Connection timed out)
Dec 22 07:41:32 df-server1 postfix/qmgr[6709]: BD24564FB7A: from=<>, size=7304, nrcpt=1 (queue active)
Dec 22 07:41:32 df-server1 postfix/qmgr[6709]: BD24564FB7A: to=<alvinsam@ms45.hinet.net>, relay=none, delay=156105, delays=156105/0.03/0/0, dsn=4.4.1, status=deferre
d (delivery temporarily suspended: connect to ms45a.hinet.net[168.95.5.45]: Connection timed out)
Dec 22 07:41:33 df-server1 postfix/qmgr[6709]: B136564E17E: from=<>, size=7478, nrcpt=1 (queue active)
Dec 22 07:41:33 df-server1 postfix/qmgr[6709]: BBA7D64DF2C: from=<>, size=3674, nrcpt=1 (queue active)
Dec 22 07:41:34 df-server1 postfix/smtp[14618]: BBA7D64DF2C: host mx1.mail.tw.yahoo.com[203.188.197.9] refused to talk to me: 453 Mail from 194.105.97.206 not allowe
d - [90]
Dec 22 07:41:34 df-server1 postfix/qmgr[6709]: B806264CEBC: from=<>, size=4803, nrcpt=1 (queue active)
Dec 22 07:41:34 df-server1 postfix/qmgr[6709]: B806264CEBC: to=<chaitsui@ms32.hinet.net>, relay=none, delay=17528, delays=17528/0.06/0/0, dsn=4.4.1, status=deferred 
(delivery temporarily suspended: connect to ms32a.hinet.net[168.95.5.32]: Connection timed out)
Dec 22 07:41:34 df-server1 postfix/qmgr[6709]: BADCC64F750: from=<>, size=4770, nrcpt=1 (queue active)
Dec 22 07:41:34 df-server1 postfix/qmgr[6709]: BFC6664D977: from=<>, size=8112, nrcpt=1 (queue active)
Dec 22 07:41:35 df-server1 postfix/qmgr[6709]: B6B5164D831: from=<>, size=3769, nrcpt=1 (queue active)
Dec 22 07:41:35 df-server1 postfix/qmgr[6709]: BB61A64F6E8: from=<>, size=6674, nrcpt=1 (queue active)
Dec 22 07:41:35 df-server1 postfix/qmgr[6709]: BCD273A27FC: from=<>, size=5790, nrcpt=1 (queue active)
Dec 22 07:41:35 df-server1 postfix/qmgr[6709]: B12A764CE86: from=<>, size=4260, nrcpt=1 (queue active)

```

---

### Post by koenn on 2007-12-23
like I said before, I don't know postfix, so I might be misinterpreting this, but
your mail server seems to accept mail with an empty "from" field :
> Dec 22 07:41:34 df-server1 postfix/qmgr[6709]: BFC6664D977: **from=<>**, size=8112, nrcpt=1 (queue active)
Dec 22 07:41:35 df-server1 postfix/qmgr[6709]: B6B5164D831: **from=<>**, size=3769, nrcpt=1 (queue active)
and if so, anyone can submit mail for delivery to any destination.

(If I'm correct,) you need to review your config file so that "from:" is mandatory and is an address in your mail domain.

---

### Post by MJN on 2007-12-23
No, it is an RFC requirement to accept mail from a null-sender. Non-delivery reports and other mail-related messages use them primarily to avoid routing loops which might otherwise occur if such reports keep bouncing of each other.

I'm still not seeing what the problem is, and given you've obfuscated your config file I'm not going to start guessing your setup.

The yahoo failure is likely down to their anti-spam measures and your IP address being on their blacklist.

Mathew

---

### Post by The Foz on 2007-12-24
Thanks everyone for your suggestions. I have solved it!

Somehow I had opened the "Submission" port (587, used for Sendmail to access the Mail Transport Agent) to the outside world. That is how they were getting in.

Now everything is working as it should.

---

### Post by MJN on 2007-12-24
I think you're confused as to what's going on (and why), but if you're happy things are working as desired then that's all that really matters!

Mathew

---

