---
title: "Postfix is sending spam"
date: 2012-09-19
forum: Server Platforms
---

### Post by kfcSmitty on 2012-09-19
Hi everyone,

My postfix server is sending spam and has thus been blacklisted from both yahoo and hotmail.

Going through my config, it seems to be "locked down," but anyone can telnet in and send email using ehlo. Can anyone explain how I can stop that?

I'm probably confused, but everywhere I read, it says you can require a username/password, but then anyone connecting needs that username and password. If I set that up, would Google, Yahoo, etc need that password to connect to my server?

Below is a sample of what I'm getting in my logs:

> **mail.log]
Sep 19 19:08:47 dragon746 postfix/qmgr[2529]: E1C154700D52: from=<*email address with my domain*>, size=1457, nrcpt=1 (queue active)
Sep 19 19:08:47 dragon746 postfix/smtp[2635]: E1C154700D52: host mta5.am0.yahoodns.net[66.196.118.33] refused to talk to me: 421 4.7.1 [TS03] All messages from *my ip* will be permanently deferred said:**
> http://postmaster.yahoo.com/errors/421-ts03.html[/url]
Sep 19 19:08:47 dragon746 postfix/smtp[2635]: E1C154700D52: host mta7.am0.yahoodns.net[66.196.118.36] refused to talk to me: 421 4.7.1 [TS03] All messages from *my ip* will be permanently deferred; Retrying will NOT succeed. See [http://postmaster.yahoo.com/errors/421-ts03.html](http://postmaster.yahoo.com/errors/421-ts03.html)
Sep 19 19:08:47 dragon746 postfix/smtp[2635]: E1C154700D52: host mta7.am0.yahoodns.net[98.139.54.60] refused to talk to me: 421 4.7.1 [TS03] All messages from *my ip* will be permanently deferred; Retrying will NOT succeed. See [http://postmaster.yahoo.com/421-ts03.html](http://postmaster.yahoo.com/421-ts03.html)
Sep 19 19:08:48 dragon746 postfix/smtp[2635]: E1C154700D52: host mta6.am0.yahoodns.net[66.94.237.139] refused to talk to me: 421 4.7.1 [TS03] All messages from *my ip* will be permanently deferred; Retrying will NOT succeed. See [http://postmaster.yahoo.com/errors/421-ts03.html](http://postmaster.yahoo.com/errors/421-ts03.html)
Sep 19 19:08:48 dragon746 postfix/smtp[2635]: E1C154700D52: to=<*email being emailed*>, relay=mta6.am0.yahoodns.net[98.136.217.202]:25, delay=29589, delays=29587/0.03/1.1/0, dsn=4.7.1, status=deferred (host mta6.am0.yahoodns.net[98.136.217.202] refused to talk to me: 421 4.7.1 [TS03] All messages from *my ip* will be permanently deferred; Retrying will NOT succeed. See [http://postmaster.yahoo.com/421-ts03.html](http://postmaster.yahoo.com/421-ts03.html))


My main.cf
[quote=main.cf]
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

inet_interfaces = all
unknown_local_recipient_reject_code = 450

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_auth_only = no
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination, reject_unauth_pipelining, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unknown_sender_domain, reject_invalid_hostname, reject_unknown_recipient_domain, reject_unauth_destination, reject_rbl_client bl.spamcop.net, reject_rbl_client list.dsbl.org, reject_rbl_client zen.spamhaus.org, reject_rbl_client dnsbl.sorbs.net, permit
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, permit

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
#mailbox_transport = cyrus
myhostname = *my domain*
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_mailbox_domains = hash:/etc/postfix/virtual_domains
virtual_alias_maps = hash:/etc/postfix/virtual_aliases
virtual_mailbox_base = /var/mail
myorigin = /etc/mailname
mydestination = *my domain*, localhost, *another one of my domains*
relayhost =
mynetworks = 127.0.0.0/8
mynetworks_style = host
mailbox_size_limit = 0
recipient_delimiter = +
broken_sasl_auth_clients = yes
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
[/quote]

Any help would be appreciated.


Thanks,

Smitty

---

### Post by volkswagner on 2012-09-20
It appears you are running an open relay.  This is bad.

Also are you on a static ip address from your isp?  Dynamic ip's are automatically blacklisted.

To prevent an open relay check the [Postfix docs on open relays]("http://www.postfix.org/SMTPD_ACCESS_README.html").

You will likely need a line similar to the following:

```
smtpd_client_restrictions = permit_mynetworks, reject
```

Notice the trailing "reject", this is important... if you put accept, then it will run through all the rules and any that don't apply will be accepted hence causing an open relay.

It is important to have a great understanding when running your own mail server, you don't want to be contributing to the problem of SPAM.

---

### Post by kfcSmitty on 2012-09-20
*edit*

Found the culprit. I had a "permit" as the last entry in "smtpd_recipient_restrictions." Once I removed it, it seems to have fixed it.

Thanks for the reply. Yeah I'm trying to secure it down.

All I want, is so anyone who emails an address listed in my virtual_aliases file, it passes it to the address I've set up for forward.

I do not want anyone to be able to send an email from any address period.

Adding the line you listed above completely stops all flow of email. So before, if someone emailed [email]admin@domain.com[/email], it forwarded to my [email]admin@gmail.com[/email] account. Once I added the line you listed above, it completely failed.

---

### Post by volkswagner on 2012-09-20
You would need to have your client ip or domain in the "MyNetworks" file, or add verbage to meet your needs.  The restrict_clients would need to match how you are using the system.

---

