---
title: "how to trouble shoot 'fatal errors' in postfix/dovecot"
date: 2014-05-26
forum: Server Platforms
---

### Post by shad2 on 2014-05-26
how can I clear the error below:
root@bab-top:/home/babel# egrep '(warning|error|fatal|panic):' /var/log/mail* | more
/var/log/mail.err:May 25 16:15:58 bab-top postfix/smtp[1923]: fatal: valid 
hostname or network address required in server description: 0
/var/log/mail.err.1:May 18 08:48:04 bab-top postfix/smtp[15767]: fatal: val
id hostname or network address required in server description: 0


can someone tell me where to start?

---

### Post by ryan87 on 2014-05-28
Hi Shad2,

It looks like your postfix configuration doesn't have a valid domain / hostname entry. Could you post the output of[COLOR=#000000] postconf -n please. If you don't want to do that start by checking the entries for [/COLOR][FONT=Arial, Helvetica, sans-serif]mydomain, [/FONT][FONT=Arial]myhostname, [/FONT][FONT=Arial, Helvetica, sans-serif]mynetworks and [/FONT][FONT=Arial]smtpd_banner.
[/FONT]
Hope this helps.
Ryan

---

### Post by shad2 on 2014-05-29
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
body_checks = regexp:/etc/postfix/body_checks
broken_sasl_auth_clients = yes
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/lib/postfix
data_directory = /var/lib/postfix
header_checks = regexp:/etc/postfix/header_checks
home_mailbox = Maildir/
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
local_recipient_maps = unix:passwd.byname $alias_maps
mail_owner = postfix
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf -n -m "${EXTENSION}"
mailbox_size_limit = 0
mailq_path = /usr/bin/mailq
message_size_limit = 10485760
mydestination = $myhostname,localhost
mydomain = bal-laptop.localhost
myhostname = bal-laptop
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128, 10.0.0.0/24
myorigin = /etc/mailname
newaliases_path = /usr/bin/newaliases
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost = 0
sendmail_path = /usr/sbin/postfix
setgid_group = postdrop
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP
smtpd_client_restrictions = permit_mynetworks,reject_unknown_client,permit
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = /etc/dovecot/auth.d  #private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_CAfile = /etc/ssl/certs/CAcertbal-laptop.pem
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/bal-laptop.localhost.crt
smtpd_tls_key_file = /etc/ssl/private/bal-laptopserver.key
smtpd_tls_loglevel = 1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 550
virtual_alias_domains = 
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:1000
virtual_mailbox_base = /home/bal/vmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_transport = dovecot
virtual_uid_maps = static:1000

her it is,but iam sure  it is that which iam using.By the way what is the essence of the alias_maps = hash:/etc/aliases
i see there that i set postmaster to an adress not in the db,could that be a problem??

---

### Post by ryan87 on 2014-05-29
To me it looks like you fault is here:

[COLOR=#000000]relayhost = 0[/COLOR]

[COLOR=#000000]This should be the name of the hose you want to relay your mail on to i.e. smtp.myisp.com. If you don't want to relay to another SMTP server then remove the line. At the moment postfix doesn't know what to do with any message that don't belong to your domain.

Hope this helps.

[/COLOR]

---

### Post by shad2 on 2014-05-30
thanks iam going to try that,
but what is the use of this:
Edit the file /etc/aliases, making sure the "postmaster" and "root" directives are set properly for your organization.

File:[COLOR=#FF0000]/etc/aliases[/COLOR]
[COLOR=#40FF00]
postmaster: root
root: [EMAIL="postmaster@example.com"]postmaster@example.com[/EMAIL][/COLOR]

After modifying this file, you must run the following commands to update aliases and restart Postfix:

[COLOR=#FF0000]newaliases
service postfix restart

the postmaster  adress.in all the tutorials online  i have not seen any saying that this should be an email account in the database,or is my thinking and unknowingness the problem?Is it supposed to be a special account inside the users' database too??Please help,,,
[/COLOR]

---

