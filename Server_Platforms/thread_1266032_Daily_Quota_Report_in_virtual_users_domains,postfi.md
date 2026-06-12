---
title: "Daily Quota Report in virtual users domains,postfix, dovecot, mysql"
date: 2009-09-14
forum: Server Platforms
---

### Post by vl72 on 2009-09-14
I have used this HOWTO 
[http://howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04-p3](http://howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04-p3)
and now I’ve received email notification with empty “Daily Quota Report” that 
is in file [http://puuhis.net/vhcs/quota.txt](http://puuhis.net/vhcs/quota.txt). See chapter “11 Quota Exceedance Notifications”.
I have next line in /etc/postfix/main.cf: 
virtual_mail_base= /home/vmail
Below is my main.cf that I received from program webmin.

main.cf
non-default parameters

alias_maps     hash:/etc/aliases
append_dot_mydomain     no
biff     no
broken_sasl_auth_clients     yes
content_filter     smtp-amavis:[127.0.0.1]:10024
html_directory     /usr/share/doc/postfix/html
mailbox_command     procmail -a "$EXTENSION"
mailbox_size_limit     0
mydestination     ubu-server2.local.ua, localhost.local.ua, localhost
myhostname     ubu-server2.local.ua
mynetworks     127.0.0.0/8
myorigin     /etc/mailname
proxy_read_maps     $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains 

$relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks 

$virtual_mailbox_limit_maps
receive_override_options     no_address_mappings
recipient_delimiter     +
relay_domains     [www.local.ua]("http://www.local.ua")
smtp_tls_session_cache_database     btree:${data_directory}/smtp_scache
smtpd_banner     $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions     permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_sasl_auth_enable     yes
smtpd_sasl_authenticated_header     yes
smtpd_sasl_path     private/auth
smtpd_sasl_type     dovecot
smtpd_tls_auth_only     yes
smtpd_tls_cert_file     /etc/ssl/certs/postfix.pem
smtpd_tls_key_file     /etc/ssl/private/postfix.pem
smtpd_tls_session_cache_database     btree:${data_directory}/smtpd_scache
smtpd_use_tls     yes
transport_maps     mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains     
virtual_alias_maps     mysql:/etc/postfix/mysql-virtual-alias-maps.cf,mysql:/etc/postfix/mysql-email2email.cf
virtual_gid_maps     static:5000
virtual_mailbox_base     /home/vmail
virtual_mailbox_domains     mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_limit_maps     mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override     yes
virtual_mailbox_maps     mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_maildir_extended     yes
virtual_maildir_limit_message     "The user you are trying to reach is over quota."
virtual_overquota_bounce     yes
virtual_transport     dovecot
virtual_uid_maps     static:5000
---------------------------------------
main.cf
parameters defined as per defaults

alias_database     hash:/etc/aliases
config_directory     /etc/postfix
inet_interfaces     all
readme_directory     /usr/share/doc/postfix 


Does anyone can help me?

---

