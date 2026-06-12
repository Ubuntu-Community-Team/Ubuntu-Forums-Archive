---
title: "Postfix problem in sending e-mails"
date: 2011-09-22
forum: Server Platforms
---

### Post by ModnarA on 2011-09-22
Hello, 
I've an issue with postfix and i didn't find any solution about it online so here i am, maybe someone could help me to solve it or at least point out something that would help. To install postfix, i followed this tutorial : [http://www.debiantutorials.com/installing-postfix-with-mysql-backend-and-tls/](http://www.debiantutorials.com/installing-postfix-with-mysql-backend-and-tls/)

So here is my problem : 
When i send an e-mail from my computer on the port 25 i get this error :

Sep 21 20:02:10 stock postfix/smtpd[2006]: NOQUEUE: reject: RCPT from salXXXXXXXXXX.fbxo.proxad.net[78.XXX.XXX.XX]: 554 5.7.1 <salXXXXXXXXXXXXXXX.fbxo.proxad.net[78.XXX.XXX.XX]>: Client host rejected: Access denied; from=<no-reply@mondomaine.com> to=<no-reply@mondomaine.com> proto=ESMTP helo=<antoinePC>

This is weird because when i send a mail to my domain from gmail or hotmail it works fine, so gmail servers can send mail through port 25. I guess it has something to do with the reverse DNS but i can't find any configuration in my files that would explain this behaviour. 
Sending e-mail on the port 465 with SSL works fine.

Here is my main.cf 

> 
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (xXxXxXx)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
default_destination_concurrency_failed_cohort_limit = 1
default_destination_concurrency_limit = 1
default_destination_concurrency_negative_feedback = 1
default_destination_concurrency_positive_feedback = 1
default_destination_rate_delay = 1s
myhostname = desinscription-online.com
mydomain = $myhostname
smtpd_client_restrictions =permit_mynetworks, permit
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = xxx.ovh.net, localhost.ovh.net, , localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128,78.MON.IP.XX
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
broken_sasl_auth_clients = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_security_options = noanonymous
smtpd_recipient_restrictions = permit_mynetworks, permit_auth_destination, reject_unauth_destination, permit
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps


Thanks for your help :-)

---

### Post by ModnarA on 2011-09-22
Turns out that i now can send e-mails on the port 25 but other clients that i had in the mynetworks field still can't connect. 
I have no idea why it works now for me... 
I have put the smtpd_delay_reject to no and the server deny the connexion before the HELO, i don't know if this information can help.

---

