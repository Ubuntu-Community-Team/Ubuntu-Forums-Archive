---
title: "Postfix won't authenticate unless local"
date: 2008-11-13
forum: Server Platforms
---

### Post by stelth-panther on 2008-11-13
I am having trouble with getting relaying to work with postfix.  I have setup the server using this [tutorial]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04") and I have it working fine with squirrelmail.  The problem comes in when a user tries to use evolution or outlook to send mail.  All that is returned is "relay access denied."

I have tried telneting into the server and I can't even use the ehlo command unless I telnet localhost when I am sshed in.  I can however use the helo command but it won't say that it is starting tls and still refuses relay.  I am at my wits end so any help will be appreciated. 

We are using this server for multiple sites and both sitecats.com and sitekats.com are working domains.

Here is a print out of my postconf -n:

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
home_mailbox = Maildir/
mailbox_command = 
mailbox_size_limit = 0
mydestination = localhost, localhost.localdomain
mydomain = sitecats.com
myhostname = sitekats.com
mynetworks = 76.161.252.0/24, 172.16.252.30, 127.0.0.0/8
myorigin = /etc/mailname
proxy_interfaces = 76.161.252.30
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = no
receive_override_options = no_address_mappings
recipient_delimiter = +
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_helo_required = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_uid_maps = static:5000

---

### Post by excalq on 2009-08-13
I had no luck at all with this, until I used dovecot, which worked right away! See: [http://ubuntuforums.org/showthread.php?p=7777900](http://ubuntuforums.org/showthread.php?p=7777900)

---

