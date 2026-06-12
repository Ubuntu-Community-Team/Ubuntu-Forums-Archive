---
title: "Postfix error only from AOL messages..."
date: 2009-01-23
forum: Server Platforms
---

### Post by maiwurd on 2009-01-23
The original message was received at Thu, 22 Jan 2009 13:07:45 -0500 (EST) from imo-m20.mail.aol.com [172.20.107.66]


*** ATTENTION ***

Your e-mail is being returned to you because there was a problem with its delivery. The address which was undeliverable is listed in the section
labeled: "----- The following addresses had permanent fatal errors -----".

The reason your mail is being returned to you is listed in the section
labeled: "----- Transcript of Session Follows -----".

The line beginning with "<<<" describes the specific reason your e-mail could not be delivered. The next line contains a second error message which is a general translation for other e-mail servers.

Please direct further questions regarding this message to the e-mail administrator or Postmaster at that destination.

--AOL Postmaster



----- The following addresses had permanent fatal errors ----- <user@mydomain.com>
(reason: 451 4.3.5 Server configuration problem)

----- Transcript of session follows ----- ... while talking to mydomain.com.:
>>> DATA
<<< 451 4.3.5 Server configuration problem <user@mydomain.com>... Deferred: 451 4.3.5 Server configuration problem <<< 554 5.5.1 Error: no valid recipients Message could not be delivered for 3 hours Message will be deleted from queue


Final-Recipient: RFC822; [email]user@mydomain.com[/email]
Action: failed
Status: 4.4.7
Remote-MTA: DNS; mydomain.com
Diagnostic-Code: SMTP; 451 4.3.5 Server configuration problem
Last-Attempt-Date: Thu, 22 Jan 2009 16:07:52 -0500 (EST)


Received: from imo-m20.mx.aol.com (imo-m20.mail.aol.com [172.20.107.66]) by imr-m06.mx.aol.com (v107.10) with ESMTP id RELAYIN1-24978b5f1367; Thu, 22 Jan 2009 13:07:45 -0500
Received: from [email]sender@aol.com[/email]
by imo-m20.mx.aol.com (mail_out_v39.1.) id o.d2d.459d7fb5 (39329)
for <user@mydomain.com>; Thu, 22 Jan 2009 12:52:23 -0500


Here is the result of the postconf -n:



> postconf -n
alias_maps = mysql:/etc/postfix/mysql-aliases.cf
broken_sasl_auth_clients = yes
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/libexec/postfix
html_directory = /usr/share/doc/postfix-2.4.7-documentation/html
inet_interfaces = $myhostname, localhost
local_recipient_maps = $alias_maps $virtual_mailbox_maps unixasswd.byname
mail_owner = postfix
mailbox_size_limit = 0
mailq_path = /usr/bin/mailq.postfix
manpage_directory = /usr/share/man
message_size_limit = 0
mydestination = mydomain.com, $transport_maps
mydomain = $myhostname
myhostname = mydomain.com
myorigin = $mydomain
newaliases_path = /usr/bin/newaliases.postfix
queue_directory = /var/spool/postfix
readme_directory = /usr/share/doc/postfix-2.4.7-documentation/readme
relocated_maps = mysql:/etc/postfix/mysql-relocated.cf
sample_directory = /etc/postfix
sendmail_path = /usr/sbin/sendmail.postfix
setgid_group = postdrop
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-client.cf
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination, reject_rbl_client zen.spamhaus.org, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_non_fqdn_recipient, reject_unknown_recipient_domain, check_policy_service unixrivate/policy, reject_invalid_helo_hostname, reject_non_fqdn_helo_hostname, check_policy_service inet:127.0.0.1:10023
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = smtpd
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-sender.cf
smtpd_tls_CAfile = /usr/local/ssl/PositiveSSL-bundle.crt
smtpd_tls_cert_file = /usr/local/ssl/mydomain.com.pem
smtpd_tls_key_file = $smtpd_tls_cert_file
smtpd_tls_loglevel = 0
smtpd_tls_security_level = may
smtpd_use_tls = yes
transport_maps = mysql:/etc/postfix/mysql-transport.cf
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual.cf
virtual_gid_maps = mysql:/etc/postfix/mysql-virtual-gid.cf
virtual_mailbox_base = /home/vmail
virtual_mailbox_limit = 0
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-maps.cf
virtual_uid_maps = mysql:/etc/postfix/mysql-virtual-uid.cf


What has changed is the implementation of SPF to stop spoofed spam messages from China which were inundating our Presidents Outlook account.
I also modified the - adding what is in bold.

smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination, reject_rbl_client zen.spamhaus.org, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_non_fqdn_recipient, reject_unknown_recipient_domain, check_policy_service unixrivate/policy, reject_invalid_helo_hostname, reject_non_fqdn_helo_hostname, check_policy_service inet:127.0.0.1:10023

---

### Post by maiwurd on 2009-01-23
Mod pls delete this thread.

---

