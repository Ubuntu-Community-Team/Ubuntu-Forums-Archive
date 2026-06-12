---
title: "Postfix+courier+squirrelmail"
date: 2010-01-23
forum: Server Platforms
---

### Post by LMSSML on 2010-01-23
Hi there

Since a while

I've built an e-mail server with ubuntu server 9.10 and installed the following:

Postfix
saslauth
Courier
Mysql
webmin
Squirrelmail
ISPConfig3

but the problem at the present moment goes to sent e-mails qith squirrelmail.

I've collect this on log everytime i try to sent an e-mail.
localhost.localdomain[127.0.0.1]: TLS cipher list "ALL:!EXPORT:!LOW:+RC4:@STRENGTH"
Jan 23 22:45:01 mail postfix/smtpd[17799]: SSL_accept:before/accept initialization
Jan 23 22:45:01 mail postfix/smtpd[17799]: read from 02103FE0 [0210DAA0] (11 bytes => -1 (0xFFFFFFFF))
Jan 23 22:45:01 mail postfix/smtpd[17799]: SSL_accept error from localhost.localdomain[127.0.0.1]: -1
Jan 23 22:45:01 mail postfix/smtpd[17799]: lost connection after CONNECT from localhost.localdomain[127.0.0.1]
Jan 23 22:45:01 mail postfix/smtpd[17799]: disconnect from localhost.localdomain[127.0.0.1]
Jan 23 22:45:01 mail getmail: Initializing SimplePOP3Retriever:user@mail.example.com:110:
Jan 23 22:45:01 mail pop3d: Connection, ip=[::ffff:]
Jan 23 22:45:01 mail pop3d: LOGOUT, ip=[::ffff:]
Jan 23 22:45:01 mail pop3d: Disconnected, ip=[::ffff:]

My postconf -n is like this

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
body_checks = regexp:/etc/postfix/body_checks
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
header_checks = regexp:/etc/postfix/header_checks
home_mailbox = Maildir/
mailbox_size_limit = 0
mailbox_transport = courier
message_size_limit = 0
mime_header_checks = regexp:/etc/postfix/mime_header_checks
mydestination = domain.com,localhost,localhost.localdomain
mydomain = domain.com
mynetworks = <ip>,127.0.0.0/8
myorigin = mail.example.com
nested_header_checks = regexp:/etc/postfix/nested_header_checks
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = no
receive_override_options = no_address_mappings
recipient_delimiter = +
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relayhost = mail.example.com:25
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 3
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_transport = maildrop
virtual_uid_maps = static:5000


By the way if I use telnet to do at port 25 I will get the following

root@mail:/etc# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
ehlo localhost
Connection closed by foreign host.

Using nmap -PO localhost

25/tcp    open  smtp




At the moment I can access to the mailboxes but could not sent the e-mail I even try to remove ssl auth but the problem is the same.

I'm desperated with this, can anyone help me ?

Thanks ins advanced

---

### Post by LMSSML on 2010-01-24
Hi people

Anyone who could help with this situation ?

Thanks

---

### Post by LMSSML on 2010-01-25
Anyone who could help ?

---

### Post by Roger_Smith on 2010-01-25
Remove the reject_unauth_pipelining from smtp_recipient_restrictions line.  

So make it look like this: 

```

smtpd_recipient_restrictions = 
permit_mynetworks, 
permit_sasl_authenticated, 
reject_non_fqdn_recipient, 
reject_unauth_destination, 
check_policy_service
```

If this postfix server is also receiving mail, you may want to add this to that line: 
reject_non_fqdn_sender

This will block spammers from sending from bob@192.145.2.1 etc.

One thing I've learned from postfix, is if something doesn't work, start with a basic config and add one thing at a time and go from there.  

If that doesn't work above, go back to the 

default postfix: 
```
smtpd_recipient_restrictions =
     permit_mynetworks,
     permit_sasl_authenticated,
     reject_unauth_destination
```


Hope this helps.

Edit: Are their any errors when you startup postfix in the /var/log/mail.log?

---

