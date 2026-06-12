---
title: "I cant telnet into my local mail server on port 25"
date: 2009-05-06
forum: Server Platforms
---

### Post by kustomjs on 2009-05-06
Hi Guys
I am having problems trying to telnet into my mail server on port 25 and its not connecting. I am using postfix and here is my main.cf.

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

myhostname = kustomjs.com
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
myorigin = /etc/mailname
local_recipient_maps = 
mydestination =
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host

# how long if undelivered before sending warning update to sender 
delay_warning_time = 4h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450 
# how long to keep message on queue before return as failed.
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s
# how many address can be used in one message
smtpd_recipient_limit = 16
# how many error before back off
smtpd_soft_error_limit = 3
# how many max errors before blocking it
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

```

---

### Post by ejschaefer on 2009-05-06
Hi, 

Whats your output of

```

netstat -plant | grep ":25"

```

It should be something like this

```

tcp        0      0 0.0.0.0:25               0.0.0.0:*                   LISTEN      3783/master

```

If it is, check iptables, chances are port 25 is blocked. Unblock it with 

```

iptables -I INPUT -p tcp --dport 25 -j ACCEPT

```

Let me know what you find.

---

