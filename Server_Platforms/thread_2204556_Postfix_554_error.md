---
title: "Postfix 554 error"
date: 2014-02-09
forum: Server Platforms
---

### Post by TheWayno104 on 2014-02-09
I need help if anyone is willing to provide :)

This is the mail server guide i have referenced >>>>  [http://flurdy.com/docs/postfix/#intro](http://flurdy.com/docs/postfix/#intro) 
I have only installed the basic setup for now until i can get everything working, so far everything works bar being able to send an email from a client, i can only send from the console using telnet and i presume if i installed roundcube that would work also. 

System specs: ubuntu 12.04 

Please note i have changed my actual domain name to domain.com as to protect my security and that of the email addresses in the mail.log

The error i get while tailing >>>> /var/log/mail.log -f 

Feb  9 22:28:03 domain.com postfix/smtpd[4923]: connect from unknown[192.168.1.254]Feb  9 22:28:03 domain.com postfix/smtpd[4923]: NOQUEUE: reject: RCPT from unknown[192.168.1.254]:           554 5.7.1 <mail@gmail.com>: Relay access denied; from=<wayne@domain.com> to=                                 <mail@gmail.com>   proto=ESMTP helo=<[127.0.0.1]>
Feb  9 22:28:11 domain postfix/smtpd[4923]: disconnect from unknown[192.168.1.254]

here is my /postfix/main.cf

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname
myorigin= domain.com


smtpd_banner = $mail.domain.com.au ESMTP $domain.com.au  (Ubuntu)
biff = no


# appending .domain is the MUA's job.
append_dot_mydomain = no


# Uncomment the next line to generate "delayed mail" warnings
# how long if undelivered before sending warning update to sender
delay_warning_time = 4h
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


# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl
# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_data_restrictions = reject_unauth_pipelining


readme_directory = no


# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = mail.domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
local_recipient_maps =
mydestination =
# relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host


masquerade_domains = mail.domain.com [www.domain.com](www.domain.com)
masquerade_exceptions = root


# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf


virtual_uid_maps = static:5000
virtual_gid_maps = static:5000


Any help would be highly appreciated, let me know if you need any other config posted to determine the cause of this Relay access denied from a mail client.

---

### Post by brokenhachi on 2014-02-11
```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 
```

As a start, Postfix cannot relay messages because you told it to only accept connections from 127.0.0.0/8. Change this line to ```
mynetworks = 
``` then you will have "open relay" and postfix will accept connections from anywhere. Or, you can add the networks you want to accept from, such as ```
mynetworks = 192.168.1.0/24, 192.168.2.0/24, ... 
``` to prevent your sever from becoming a spam server.

also please comment out the below line as ```
#mynetworks_style = host
```

---

