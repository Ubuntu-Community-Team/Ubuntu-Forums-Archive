---
title: "Postfix doesn't deliver mail internally"
date: 2008-06-29
forum: Server Platforms
---

### Post by Ronni Elken Lindsgaard on 2008-06-29
Hi

I've followed [this]("http://flurdy.com/docs/postfix") guide for installing virtual domains with postfix+mysql. It all seems to be working properly, but for some odd reason it seems like postfix isn't delivering the mail to the local system. Nothing gets created in /var/spool/mail

I've connected to postfix via telnet and tried to send a mail. In mail.log this happens

```
Jun 29 13:48:46 aladdin postfix/smtpd[14892]: connect from localhost[127.0.0.1]
Jun 29 13:49:41 aladdin postfix/smtpd[14892]: 77B245F422A: client=localhost[127.0.0.1]
Jun 29 13:49:55 aladdin postfix/cleanup[14896]: 77B245F422A: message-id=<20080629114941.77B245F422A@aladdin.localdomain>
Jun 29 13:50:14 aladdin postfix/smtpd[14892]: disconnect from localhost[127.0.0.1]

```

I am completely new to mailing, so I have no idea how to read this. But it doesn't seem like there's any errors.

At the same time, mysql.log outputs 

```
080629 13:49:13	     23 Connect     mail@localhost on maildb
		     23 Query       SELECT destination FROM aliases WHERE mail='mediastyle.dk' and enabled = 1
		     24 Connect     mail@localhost on maildb
		     24 Query       SELECT domain FROM domains WHERE domain='mediastyle.dk' and enabled = 1
080629 13:49:40	     23 Query       SELECT destination FROM aliases WHERE mail='lala.com' and enabled = 1
		     24 Query       SELECT domain FROM domains WHERE domain='lala.com' and enabled = 1
		     25 Connect     mail@localhost on maildb
		     25 Query       SELECT destination FROM aliases WHERE mail='xandros@lala.com' and enabled = 1
		     25 Query       SELECT destination FROM aliases WHERE mail='@lala.com' and enabled = 1
080629 13:49:41	     26 Connect     mail@localhost on maildb
		     26 Query       SELECT destination FROM aliases WHERE mail='xandros@lala.com' and enabled = 1
		     26 Query       SELECT destination FROM aliases WHERE mail='@lala.com' and enabled = 1
		     26 Query       SELECT destination FROM aliases WHERE mail='xandros@blobber.org' and enabled = 1
080629 13:50:40	     25 Quit       

```

my main.cf looks like this

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

#myhostname = aladdin.fullrate.dk
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
myorigin = mediastyle.dk
mydestination =
relayhost = 
mynetworks = host
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
local_recipient_maps =

#Setup mysql stuff
#The base of where the mails are stored
virtual_mailbox_base = /var/spool/mail/virtual
#The file for mailbox location
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
#The user id's
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
#Group id's
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
#For the aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
#Domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
#How to connect the domains
#transportmaps = mysql:/etc/postfix/mysql_transport.cf

postalias = /etc/postfix/aliases

#Setup some restriction stuff i don't quite understand yet...copy/paste from: http://flurdy.com/docs/postfix/#conf_firewall

delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit 
smtpd_data_restrictions = reject_unauth_pipelining

smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes

```

Any ideas why my mails don't get further than the log?

Help greatly appreciated

---

