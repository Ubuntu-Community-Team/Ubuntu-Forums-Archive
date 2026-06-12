---
title: "Postfix on Ubuntu server 8.04"
date: 2008-07-03
forum: Server Platforms
---

### Post by @ngkor on 2008-07-03
Hi everyone,

I'm running postfix on ubuntu server 8.04 at a small branch office as MTA for our office staffs.

My Postfix is running without the real internet hostname, our Head Office's mail server received emails for all users, so our staffs have to get their email from Head Office's mail server. Postfix send email to outside world through our ISP SMTP server: relayhost = [ISP_SMTP_SERVER]

I am facing a problem when our staffs send email to other users at Head Office (it's the same domain name), Postfix did not accept that email and return User unknown in virtual mailbox error message at the mail client.

After I add: smtpd_reject_unlisted_recipient = no in main.cf

Postfix accept that email but could not found the recipient in the virtual_mailbox_maps (yes their mail box located in Head Office's mail server and I don't have catch all) then it return an unknown recipient nondelivery mail to the sender.

How can I forward those mails (RCPT TO <Head Office users>) to Head
Office MTA?

Thanks and Regard,
@ngkor

---

### Post by @ngkor on 2008-07-05
Below is my main.cf file:

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = ipv4
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 10240000
mydestination = vm-ubuntu.local, localhost.local, localhost
myhostname = vm-ubuntu.local
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.2.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = 
relayhost = [202.93.8.3]          #my ISP smtp server IP address
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks, permit_auth_destination, reject_unauth_destination
smtpd_reject_unlisted_recipient = no
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_maps = hash:/etc/postfix/vmailbox_aliases
virtual_gid_maps = static:2000
virtual_mailbox_base = /var/spool/virtual_mailboxes
virtual_mailbox_domains = vmailbox
virtual_mailbox_maps = hash:/etc/postfix/vmailbox_maps
virtual_uid_maps = static:2000

Thanks

---

