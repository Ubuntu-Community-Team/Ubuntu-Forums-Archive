---
title: "Postfix - bogus emails from unknown users sent"
date: 2010-12-02
forum: Server Platforms
---

### Post by Rob65 on 2010-12-02
Hi all,

I've been banging my head against the screen on this strange problem.
Somehow my server sends out spam mails to a lot of aol mail addressess.
The mail.log file looks like:

```
Dec  2 16:10:55 Ubuntu-904-jaunty-64-minimal postfix/qmgr[7685]: E95C2B48DB4: from=<HappyShopping@somedomain.nl>, size=1912, nrcpt=1 (queue active)
Dec  2 16:10:55 Ubuntu-904-jaunty-64-minimal postfix/qmgr[7685]: 5D4E0B48DB5: from=<HappyShopping@somedomain.nl>, size=1904, nrcpt=1 (queue active)
Dec  2 16:10:55 Ubuntu-904-jaunty-64-minimal postfix/qmgr[7685]: 8F540B48D04: from=<NewYearSale@somedomain.nl>, size=1894, nrcpt=1 (queue active)
Dec  2 16:10:55 Ubuntu-904-jaunty-64-minimal postfix/qmgr[7685]: 6DE3EB48ADD: from=<NewYearSale@somedomain.nl>, size=1930, nrcpt=1 (queue active)
Dec  2 16:10:55 Ubuntu-904-jaunty-64-minimal postfix/smtp[7807]: 5D4E0B48DB5: host gateway-f2.isp.att.net[207.115.11.16] refused to talk to me: 521-188.40.99.213 blocked by ldap:ou=rblmx,dc=att,dc=net 521 Error - Blocked for abuse. Contact abuse_rbl@abuse-att.net.
Dec  2 16:10:55 Ubuntu-904-jaunty-64-minimal postfix/smtp[7807]: 5D4E0B48DB5: to=<enos@bellsouth.net>, relay=gateway-f1.isp.att.net[204.127.217.16]:25, delay=101003, delays=101003/0.05/0.7/0, dsn=4.0.0, status=deferred (host gateway-f1.isp.att.net[204.127.217.16] refused to talk to me: 521-188.40.99.213 blocked by ldap:ou=rblmx,dc=att,dc=net 521 Error - Blocked for abuse. Contact abuse_rbl@abuse-att.net.)

```It may be clear that users like HappyShopping and NewYearSale do not exists on my server. The domain somedomain.nl does exist on the server as a virtual domain but it does not exist as such in the mysql maildb database with virtual users.

I do not see how a user on the system can send a mail in this way. Normally all mail coming to the server is processed by smtpd (even local mails sent from e.g. php scripts are handled in this way) but these messages seem to originate directly to qmgr.

There are just a few users on the system, all handled by me, and these are only used to handle different web domains (using http only). Yes ... with php access ...
I've removed the 'somedomain.nl' completely from the sites-enabled list in apache and there are no MX records pointing to somedomain.nl

I've been searching for a way to disallow users to send emails when they are not in the mysql maildb with virtual domains and users for postfix.

I changed:

```
smtpd_sender_restrictions =  check_sender_access mysql:/etc/postfix/mysql_mailbox.cf
```afaik this should disallow any mails from users that are not in the maildb mysql database but these strange mails are still being send to aol (and others).

Is there any way to identify where these mails are coming from and how to block these mails in postfix/smtp ?

My system contains *Ubuntu* + *Postfix* + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV, configured using one of the many howtos on the web (yes: I am a unix/linux user but don't have much knowledge on system configuration)

Regards,

Rob

---

### Post by CharlesA on 2010-12-02
Did you configure postfix to access mail from everyone, or just your domain/localhost?

---

### Post by Rob65 on 2010-12-02
Charles,

I'm not sure I completely understand your question (almost feel like a Noob...).

I have configured postfix to serve the users on my server using virtual domains - it also accepts mails from normal users so I can use stuff like the mail() function in PHP to send emails.
There is an SMTP port to accept incoming mail (and a corresponding MX record at my provider) but relaying mails is not allowed - so mails cannot be relayed via my server.

Rob

---

### Post by CharlesA on 2010-12-02
I worded it wrong. I guess it should have said: Have you configured postfix to accept mail from "everywhere" and now just your domain.

Judging from the log, it looks like it's incoming mail that's being sent out, but I'm not 100% sure as I don't know all that much about mail servers.

---

### Post by KB1JWQ on 2010-12-02
Howdy!

Please paste the output from "postconf -n" here.

---

### Post by SeijiSensei on 2010-12-02
You need to take this server offline, or at least stop accepting SMTP connections, until you fix this problem.  Right now you appear to be running an "open relay."  Your IP has apparently already been blocked for abuse by ATT.  I'm not a Postfix expert so I can't tell you how to fix this problem, but you can't continue to be an open relay without serious and annoying consequences down the road.

Check your external IP address here: [http://www.mxtoolbox.com/blacklists.aspx](http://www.mxtoolbox.com/blacklists.aspx)

---

### Post by Rob65 on 2010-12-03
SeijiSensei,

yes - that's what I was worried about. I checked the postfix config and there I have relaying disabled, when I try to relay via the SMTP port I receive an error message:

450 4.1.8 <stefke@somedomain.nl>: Sender address rejected: Domain not found

This also results in an error message in my mail.log file:

postfix/smtpd: NOQUEUE: reject: RCPT from .... >: Sender address rejected: Domain not found;

So it appears not to be an open relay.
Also, incoming traffic is marked with postfix/smtpd but these spam mails appear in postfix/qmgr without any apparent source - something I cannot explain.

KB1JWQ,

here's my postconf output:

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = localhost
myhostname = mail.maindomain.nl
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org,reject_rbl_client blackholes.easynet.nl,reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname,reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = permit_sasl_authenticated, reject_sender_login_mismatch, reject_unauth_pipelining, permit_mynetworks,reject_non_fqdn_recipient, reject_unknown_recipient_domain,reject_unauth_destination, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender,reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

```

The silly thing is that these spam mails only arrive from 3 different (invalid) mail addresses only.

---

### Post by Rob65 on 2010-12-09
OK, I found a solution for the problem.

Mails that are being rejected by the receiver are stored in /var/spool/postfix/defer and .../deferred.
each mail is stored as an (almost) readable file with at least the user ID responsible for generating this mail in readable format.

The responsible user only has a website with a webshop running - using OS-Commerce.
In that installation I found a number of .php files with malicious code.

So the easy solution was to remove all the outgoing mail for this used from the queue and remove the website.

Rob

---

