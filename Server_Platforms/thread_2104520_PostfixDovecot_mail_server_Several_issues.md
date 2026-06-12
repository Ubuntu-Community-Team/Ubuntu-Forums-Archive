---
title: "Postfix/Dovecot mail server: Several issues"
date: 2013-01-13
forum: Server Platforms
---

### Post by TippingPoint on 2013-01-13
Hello dear community!

OS: Ubuntu 12.04, VPS server, static IP address.
DNS name: myserver.com (censored)
Mailbox on my server: [email]admin@myserver.com[/email]

I recently began to set up my mail server. In a nutshell, it is the typical postfix/dovecot/MySql/Postfixadmin combination. I followed the advises on [this]("http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/") howto.

I am right now testing my server configuration with various free webmail accounts (on hotmail/gmail) and via the command line, as well as with a local mail client.

I have 2 problems, and I strongly assume that my postfix configuration is the cause.
[LIST]
[*]Postfix doesn't store the mails in the mailbox.
[*]I cannot obtain my email of dovecot via pop3 from the client. But apparantly it works to log in via telnet on pop3 on the server itself. On a remote client instead, it fails, although I entered the exactly same login credentials (via openssl s_client -connect myserver.com:995)
[/LIST]

After I tried to send a email from my webmail account, monitored the logging with tail -f /var/log/mail.log

```
Jan 13 21:09:41 vps411 postfix/master[24814]: daemon started -- version 2.9.3, configuration /etc/postfix
Jan 13 21:10:16 vps411 postfix/smtpd[24824]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jan 13 21:10:16 vps411 postfix/smtpd[24824]: connect from bay0-omc2-s26.bay0.hotmail.com[65.54.190.101]
Jan 13 21:10:17 vps411 postfix/trivial-rewrite[24832]: warning: do not list domain myserver.com in BOTH mydestination and virtual_mailbox_domains
Jan 13 21:10:17 vps411 postfix/smtpd[24824]: 38D779262A9: client=bay0-omc2-s26.bay0.hotmail.com[65.54.190.101]
Jan 13 21:10:17 vps411 postfix/cleanup[24835]: 38D779262A9: message-id=<BAY153-W620E2C4E7CFB9C8457F082F72F0@phx.gbl>
Jan 13 21:10:17 vps411 postfix/qmgr[24818]: 38D779262A9: from=<testmailer@hotmail.com>, size=1121, nrcpt=1 (queue active)
Jan 13 21:10:17 vps411 postfix/smtpd[24824]: disconnect from bay0-omc2-s26.bay0.hotmail.com[65.54.190.101]
Jan 13 21:10:24 vps411 postfix/smtpd[24841]: connect from localhost[127.0.0.1]
Jan 13 21:10:24 vps411 postfix/trivial-rewrite[24832]: warning: do not list domain myserver.com in BOTH mydestination and virtual_mailbox_domains
Jan 13 21:10:24 vps411 postfix/smtpd[24841]: A0A669262EC: client=localhost[127.0.0.1]
Jan 13 21:10:24 vps411 postfix/cleanup[24835]: A0A669262EC: message-id=<BAY153-W620E2C4E7CFB9C8457F082F72F0@phx.gbl>
Jan 13 21:10:24 vps411 postfix/smtpd[24841]: disconnect from localhost[127.0.0.1]
Jan 13 21:10:24 vps411 postfix/qmgr[24818]: A0A669262EC: from=<testmailer@hotmail.com>, size=1604, nrcpt=1 (queue active)
Jan 13 21:10:24 vps411 postfix/trivial-rewrite[24832]: warning: do not list domain myserver.com in BOTH mydestination and virtual_mailbox_domains
Jan 13 21:10:24 vps411 postfix/local[24842]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Jan 13 21:10:24 vps411 postfix/local[24842]: A0A669262EC: to=<admin@myserver.com>, relay=local, delay=0.1, delays=0.01/0.07/0/0.02, dsn=5.1.1, status=bounced (unknown user: "admin")
Jan 13 21:10:24 vps411 postfix/cleanup[24835]: B8FFB9262F0: message-id=<20130113171024.B8FFB9262F0@mail.myserver.com>
Jan 13 21:10:24 vps411 postfix/bounce[24843]: A0A669262EC: sender non-delivery notification: B8FFB9262F0
Jan 13 21:10:24 vps411 postfix/qmgr[24818]: B8FFB9262F0: from=<>, size=3510, nrcpt=1 (queue active)
Jan 13 21:10:24 vps411 postfix/qmgr[24818]: A0A669262EC: removed
Jan 13 21:10:24 vps411 amavis[21351]: (21351-03) Passed CLEAN, [65.54.190.101] <testmailer@hotmail.com> -> <admin@myserver.com>, Message-ID: <BAY153-W620E2C4E7CFB9C8457F082F72F0@phx.gbl>, mail_id: vyoXvAslEyr2, Hits: 0.001, size: 1121, queued_as: A0A669262EC, 7133 ms
Jan 13 21:10:24 vps411 postfix/smtp[24837]: 38D779262A9: to=<admin@myserver.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=7.8, delays=0.55/0.02/0.31/6.9, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as A0A669262EC)
Jan 13 21:10:24 vps411 postfix/qmgr[24818]: 38D779262A9: removed
Jan 13 21:10:26 vps411 postfix/smtp[24844]: B8FFB9262F0: to=<testmailer@hotmail.com>, relay=mx2.hotmail.com[65.54.188.126]:25, delay=1.4, delays=0.07/0.02/0.5/0.81, dsn=2.0.0, status=sent (250  <20130113171024.B8FFB9262F0@mail.myserver.com> Queued mail for delivery)
Jan 13 21:10:26 vps411 postfix/qmgr[24818]: B8FFB9262F0: removed
```

I guess the critical line is here:
```
Jan 13 21:10:24 vps411 postfix/local[24842]: A0A669262EC: to=<admin@myserver.com>, relay=local, delay=0.1, delays=0.01/0.07/0/0.02, dsn=5.1.1, status=bounced (unknown user: "admin")
```
when postfix in it's MDU function (Does postfix alos deliver mail?) tries to handle dovecot the message.
What does here go wrong? Can't postfix read the MySql database? I checked all the mysql connections as username/database/password. I confirmed in postfixadmin that there exists a mailbox for [email]admin@myserver.com[/email] (As well as in the database itself and in the control panel). 

There is also no folder for the virtual mail boxes created in /var/vmail. 

So I would really appreciate your help, dear community. I kinda feel lost and miss the forest for the trees. I think I know too less meta information to track the problem down it's root cause. Where should I start troubleshooting? 

Thanks for any help!
Regards

Here is my /etc/postfix/main.cf

```
#  See /usr/share/postfix/main.cf.dist for a commented, more complete version
 
# The first text sent to a connecting process.
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
# appending .domain is the MUA's job.
append_dot_mydomain = no
readme_directory = no
 
# SASL parameters
# ---------------------------------
 
# Use Dovecot to authenticate.
smtpd_sasl_type = dovecot
# Referring to /var/spool/postfix/private/auth
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
smtpd_sasl_authenticated_header = yes
 
# TLS parameters
# ---------------------------------
 
# Replace this with your SSL certificate path if you are using one.
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
# The snakeoil self-signed certificate has no need for a CA file. But
# if you are using your own SSL certificate, then you probably have
# a CA certificate bundle from your provider. The path to that goes
# here.
#smtpd_tls_CAfile=/path/to/ca/file
smtpd_use_tls=yes
smtp_tls_security_level = may
smtpd_tls_security_level = may
#smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
 
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
 
# SMTPD parameters
# ---------------------------------
 
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
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
 
# This next set are important for determining who can send mail and relay mail
# to other servers. It is very important to get this right - accidentally producing
# an open relay that allows unauthenticated sending of mail is a Very Bad Thing.
#
# You are encouraged to read up on what exactly each of these options accomplish.
 
# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
# Requirement for the recipient address. Note that the entry for
# "check_policy_service inet:127.0.0.1:10023" enables Postgrey.
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_data_restrictions = reject_unauth_pipelining
 
# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes
 
# General host and delivery info
# ----------------------------------
 
# The myhostname parameter specifies the internet hostname of this
# mail system. The default is to use the fully-qualified domain name
# from gethostname(). $myhostname is used as a default value for many
# other configuration parameters.
#
myhostname = mail.myserver.com

# The mydomain parameter specifies the local internet domain name.
# The default is to use $myhostname minus the first component.
# $mydomain is used as a default value for many other configuration
# parameters.
mydomain = myserver.com 

myorigin = /etc/hostname
# Some people see issues when setting mydestination explicitly to the server
# subdomain, while leaving it empty generally doesn't hurt. So it is left empty here.
# mydestination = mail.example.com, localhost
mydestination = myserver.com
# If you have a separate web server that sends outgoing mail through this
# mailserver, you may want to add its IP address to the space-delimited list in
# mynetworks, e.g. as 111.222.333.444/32.
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
 
# This specifies where the virtual mailbox folders will be located.
virtual_mailbox_base = /var/vmail
# This is for the mailbox location for each user. The domainaliases
# map allows us to make use of Postfix Admin's domain alias feature.
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf, mysql:/etc/postfix/mysql_virtual_mailbox_domainaliases_maps.cf
# and their user id
virtual_uid_maps = static:150
# and group id
virtual_gid_maps = static:8
# This is for aliases. The domainaliases map allows us to make 
# use of Postfix Admin's domain alias feature.
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf, mysql:/etc/postfix/mysql_virtual_alias_domainaliases_maps.cf
# This is for domain lookups.
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
 
# Integration with other packages
# ---------------------------------------
 
# Tell postfix to hand off mail to the definition for dovecot in master.cf
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
 
# Use amavis for virus and spam scanning
content_filter = amavis:[127.0.0.1]:10024
 
# Header manipulation
# --------------------------------------
 
# Getting rid of unwanted headers. See: https://posluns.com/guides/header-removal/
header_checks = regexp:/etc/postfix/header_checks
# getting rid of x-original-to
enable_original_recipient = no
```

---

### Post by TippingPoint on 2013-01-13
Got the stuff somehow working. Maybe because not all mysql.conf files under /etc/dovecot/ where properly configured...Anyways.

---

