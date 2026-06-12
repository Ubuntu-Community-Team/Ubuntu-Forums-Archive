---
title: "Postfix hostname"
date: 2016-11-20
forum: Server Platforms
---

### Post by jonnier on 2016-11-20
Hi,

I have recently configured Ubuntu 16.04LTS to run as an email server, with Postfix and Dovecot.  Rather stupidly I didn't set the server hostname correctly when setting up Ubuntu.  I have since changed it using the hostname command, and hostname --fqdn returns the correct result.

Sending out emails to some of my contacts causes a problem as there SMTP rejects my attempt to deliver mail as it doesn't recognise a valid HELO message.  If I change the 'myhostname =' parameter in main.cf to match the new fqdn it sends ok, but then I have an issue receiving mail, as postfix reports that the user doesn't exist.  I presume I am missing changing another setting somewhere, can anyone help?

Here is the output of postconf -n

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
content_filter = amavisfeed:[127.0.0.1]:10024
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
myhostname = engomail
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost =
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_security_level = may
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf,mysql:/etc/postfix/mysql-virtual-alias-maps-self.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = lmtp:unix:private/dovecot-lmtp

Thanks,


Jon

---

### Post by TheFu on 2016-11-20
4 places need the correct hostname (if you want it to be consistent).

* edit /etc/hostname
* edit /etc/hosts
* edit /etc/mailname
* run ```
sudo hostname {newname}
```
* alter /etc/postfix/main.cf for myorigin and myhostname
```
   myorigin = /etc/mailname
   mydestination =  {newname} localhost.localdomain, localhost
   myhostname = {newname}
```

That should handle it.  Validate that 'hostname' give the correct answer. restart postfix.  Be happy.

---

### Post by jonnier on 2016-11-21
Thanks for the pointers.  All the information was correct in the relevant files and the hostname returned the correct FQDN as I had set it.  However I think the problem was that I wasn't identifying the machine as part of the domain name.  As soon as I changed everything to mail.{domain name} it seems to have cured the problem.

Thanks again for the sanity check, I'm happy :)

---

