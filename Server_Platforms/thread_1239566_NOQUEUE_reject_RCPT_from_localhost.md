---
title: "NOQUEUE: reject: RCPT from localhost"
date: 2009-08-13
forum: Server Platforms
---

### Post by localfiend on 2009-08-13
Using Ubuntu 9.04, postfix, mysql, courier-imap

NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 554 5.7.1 <localhost[127.0.0.1]>: Client host rejected: Access denied; from=<localfiend@mydomain.com> to=<localfiend@mydomain.com> proto=ESMTP helo=<mydomain.com>

I had my mail server setup working and then ended up breaking something.  I have virtual domains & users set up. I can't send or receive mail - I get the error message mentioned above.  Been using telnet localhost 25 to test, and I get the error once I reach the RCPT TO: step.

Anyone see anything obvious that would be causing me all this trouble?

postconf -n results:

alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps = 
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = 
myhostname = mydomain.com
mynetworks_style = host
myorigin = mydomain.com
relayhost = 
smtp_helo_timeout = 60s
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

---

### Post by localfiend on 2009-08-13
Well, I feel stupid.  Found some residual filters in /etc/postfix/master.cf that were keeping things from working.  It didn't show anything on postconf -n and was driving me nuts.

---

