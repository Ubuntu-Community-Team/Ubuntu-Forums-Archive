---
title: "Cannot send out through postfix from external clients"
date: 2015-08-28
forum: Server Platforms
---

### Post by brad42 on 2015-08-28
Hi all!

I'm running myself mad trying to figure out how to solve an issue that has cropped up in the past few weeks, seemingly out of no where. Everything was working fine, chugging along, when my VPS provider shut down all port 25 traffic since they got abused by spammers. Anyway, that got cleared up, resolved, no issues sending or receiving from the local host, or even getting mail on remote clients.

The only issue is... sending from a remote host. I get this:

```
Aug 28 13:30:08 s1 postfix/smtps/smtpd[3876]: connect from ##-##-###-###.pools.spcsdns.net[##.##.###.###]
Aug 28 13:30:09 s1 postfix/smtps/smtpd[3876]: Anonymous TLS connection established from ##-##-###-###.pools.spcsdns.net[##.##.###.###]: TLSv1.2 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
Aug 28 13:30:09 s1 postfix/smtps/smtpd[3876]: NOQUEUE: reject: CONNECT from ##-##-###-###.pools.spcsdns.net[##.##.###.###]: 554 5.7.1 <##-##-###-###.pools.spcsdns.net[##.##.###.###]>: Client host rejected: Access denied; proto=SMTP
Aug 28 13:30:11 s1 postfix/smtps/smtpd[3876]: lost connection after CONNECT from ##-##-###-###.pools.spcsdns.net[##.##.###.###]
Aug 28 13:30:11 s1 postfix/smtps/smtpd[3876]: disconnect from ##-##-###-###.pools.spcsdns.net[##.##.###.###]
Aug 28 13:30:16 s1 postfix/smtps/smtpd[3876]: connect from ##-##-###-###.pools.spcsdns.net[##.##.###.###]
Aug 28 13:30:16 s1 postfix/smtps/smtpd[3876]: Anonymous TLS connection established from ##-##-###-###.pools.spcsdns.net[##.##.###.###]: TLSv1.2 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
Aug 28 13:30:16 s1 postfix/smtps/smtpd[3876]: NOQUEUE: reject: CONNECT from ##-##-###-###.pools.spcsdns.net[##.##.###.###]: 554 5.7.1 <##-##-###-###.pools.spcsdns.net[##.##.###.###]>: Client host rejected: Access denied; proto=SMTP


```

I know my mail client is set up to authenticate, so I can rule that out.

Here is my main.cf:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# The first text sent to a connecting process.
smtpd_banner = $myhostname ESMTP $mail_name - Ubuntu - Do you have any mail for the NSA?
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


# The default snakeoil certificate. Comment if using a purchased
# SSL certificate.
smtpd_tls_cert_file=/miniserv.crt
smtpd_tls_key_file=/miniserv.pem


# Uncomment if using a purchased SSL certificate.
# smtpd_tls_cert_file=/etc/ssl/certs/example.com.crt
# smtpd_tls_key_file=/etc/ssl/private/example.com.key


# The snakeoil self-signed certificate has no need for a CA file. But
# if you are using your own SSL certificate, then you probably have
# a CA certificate bundle from your provider. The path to that goes
# here.
smtpd_tls_CAfile=/miniserv.chain


# Ensure we're not using no-longer-secure protocols.
smtpd_tls_mandatory_protocols=!SSLv2,!SSLv3


smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# Note that forcing use of TLS is going to cause breakage - most mail servers
# don't offer it and so delivery will fail, both incoming and outgoing. This is
# unfortunate given what various governmental agencies are up to these days.
#
# Enable (but don't force) all incoming smtp connections to use TLS.
smtpd_tls_security_level = encrypt
# Enable (but don't force) all outgoing smtp connections to use TLS.
smtp_tls_security_level = encrypt


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
smtpd_client_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_invalid_hostname, reject_rbl_client zen.spamhaus.org, reject_rbl_client tw.yahoo.com, reject_rbl_client yahoo.com.tw, reject_rbl_$
# Requirement for the recipient address. Note that the entry for
# "check_policy_service inet:127.0.0.1:10023" enables Postgrey.
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service$
smtpd_data_restrictions = reject_unauth_pipelining
# This is a new option as of Postfix 2.10, and is required in addition to
# smtpd_recipient_restrictions for things to work properly in this setup.
smtpd_relay_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit


# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = no
disable_vrfy_command = yes


# General host and delivery info
# ----------------------------------


myhostname = s1.4ec.me
myorigin = /etc/hostname
# Some people see issues when setting mydestination explicitly to the server
# subdomain, while leaving it empty generally doesn't hurt. So it is left empty here.
# mydestination = mail.example.com, localhost
mydestination =
# If you have a separate web server that sends outgoing mail through this
# mailserver, you may want to add its IP address to the space-delimited list in
# mynetworks, e.g. as 10.10.10.10/32.
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
relayhost = 4ec.me.outbound10.mxlogic.net


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
alias_maps = hash:/etc/aliases


# Integration with other packages
# ---------------------------------------


# Tell postfix to hand off mail to the definition for dovecot in master.cf
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1


# Use amavis for virus and spam scanning
# content_filter = amavis:[127.0.0.1]:10024


# Header manipulation
# --------------------------------------


# Getting rid of unwanted headers. See: https://posluns.com/guides/header-removal/
# header_checks = regexp:/etc/postfix/header_checks
# getting rid of x-original-to
enable_original_recipient = no


sender_bcc_maps = hash:/etc/postfix/sender_bcc
recipient_bcc_maps = hash:/etc/postfix/recipient_bcc

```

Yes, I know my TLS requirements are set to Encrypt from May, but that's due to using a cloud filter inbound and outbound to relay all messages, so it's fine.

Can anyone see an error that I'm not seeing? I'd like to have this work the way it had for the longest time: allow me to login via a mail client from any connection without being an Open Relay.

Much appreciate any help that can be provided.

---

