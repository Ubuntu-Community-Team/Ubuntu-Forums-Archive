---
title: "new PostFix will not send/recieve mail"
date: 2008-10-16
forum: Server Platforms
---

### Post by FawnOfFeist on 2008-10-16
I have a new postfix mail server I built from this guide [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

I am able to telnet to port 25, but can not set the from address.  Here is what happens:
t
ehallock@AlbPostFix01:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 AlbPostFix01.localdomain ESMTP Postfix (Ubuntu)
helo localhost
250 AlbPostFix01.localdomain
Mail From:<Test@testing.com>

I then get no reply from the mail server.  Obviously I then can not get the mail to send.

Here is the current stuff from /var/log/mail.log

Oct 16 15:08:59 AlbPostFix01 postfix/smtpd[6942]: connect from localhost[127.0.0.1]
Oct 16 15:09:26 AlbPostFix01 postfix/trivial-rewrite[6917]: warning: connect to mysql server 127.0.0.1: Access denied for us$
Oct 16 15:09:26 AlbPostFix01 postfix/trivial-rewrite[6917]: fatal: mysql:/etc/postfix/mysql_alias.cf(0,lock|fold_fix): table$
Oct 16 15:09:27 AlbPostFix01 postfix/master[6911]: warning: process /usr/lib/postfix/trivial-rewrite pid 6917 exit status 1
Oct 16 15:09:28 AlbPostFix01 postfix/trivial-rewrite[6953]: warning: connect to mysql server 127.0.0.1: Access denied for us$
Oct 16 15:09:28 AlbPostFix01 postfix/trivial-rewrite[6953]: fatal: mysql:/etc/postfix/mysql_alias.cf(0,lock|fold_fix): table$
Oct 16 15:09:29 AlbPostFix01 postfix/smtpd[6942]: warning: problem talking to service rewrite: Success
Oct 16 15:09:29 AlbPostFix01 postfix/master[6911]: warning: process /usr/lib/postfix/trivial-rewrite pid 6953 exit status 1
Oct 16 15:09:29 AlbPostFix01 postfix/master[6911]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttl$
Oct 16 15:09:32 AlbPostFix01 postfix/pickup[6914]: warning: A2B4D8D0BA: message has been queued for 1 days
Oct 16 15:09:32 AlbPostFix01 postfix/pickup[6914]: A2B4D8D0BA: uid=1000 from=<ehallock>
Oct 16 15:10:29 AlbPostFix01 postfix/trivial-rewrite[6954]: warning: connect to mysql server 127.0.0.1: Access denied for us$
Oct 16 15:10:29 AlbPostFix01 postfix/trivial-rewrite[6954]: fatal: mysql:/etc/postfix/mysql_alias.cf(0,lock|fold_fix): table$
Oct 16 15:10:30 AlbPostFix01 postfix/smtpd[6942]: warning: problem talking to service rewrite: Success
Oct 16 15:10:30 AlbPostFix01 postfix/cleanup[6916]: warning: problem talking to service rewrite: Connection reset by peer
Oct 16 15:10:30 AlbPostFix01 postfix/master[6911]: warning: process /usr/lib/postfix/trivial-rewrite pid 6954 exit status 1
Oct 16 15:10:30 AlbPostFix01 postfix/master[6911]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttl$


I have been looking around but not found anything that has helped.

Where should I be looking for the reason of the error?

---

### Post by FawnOfFeist on 2008-10-16
I was expecting to get 250 2.1.0 Ok    after I tried to set the Mail From:

---

### Post by FawnOfFeist on 2008-10-16
Also thought this may be helpful.

Still can't figure this out,  Still not able to send or recieve mail.


ehallock@AlbPostFix01:/etc/postfix$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_vrfy_command = yes
home_mailbox = Maildir/
inet_interfaces = all
local_recipient_maps =
mailbox_command =
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = DOMAIN.com
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
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

---

### Post by MJN on 2008-10-17
The clue is staring you right in the face - check your logs!! Ignore warning/critical errors at your peril!
 
This looks like a MySQL permissions issue. I don't use it so cannot help directly but that's where your searching should concentrate on.
 
Mathew

---

