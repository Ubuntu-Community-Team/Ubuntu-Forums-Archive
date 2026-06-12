---
title: "PostFix + Courier, problems receiving emails from gmail"
date: 2012-02-14
forum: Server Platforms
---

### Post by steven6282 on 2012-02-14
Hello all,
I'm having problems with my email server setup.

I've installed postfix, and courier.  As well as SquirrelMail to access the mail.  I can send and receive just fine with a few other email servers I tested.  But I fail to receive any email from gmail.  I can send to gmail (and on a curious note the emails I send to my gmail account fail to automatically forward with a forwarding address I have set up for some reason), but when sending something from gmail to my email server I don't know what happens to it, it never shows up lol.

I know this isn't much information to go on, but anyone have any advice or possible can tell me where to look for more information to be able to figure this problem out?

Thanks!

---

### Post by steven6282 on 2012-02-15
Nvm.  I didn't realize the reverse dns had to be set up through my ISP.  Never had a need to worry about reverse dns before.  Got that setup and it appears to be functioning now, still seems to be slow at receiving emails but that is probably in a config somewhere that I can play with.

---

### Post by elico on 2012-02-15
> **steven6282 said:**
> Nvm.  I didn't realize the reverse dns had to be set up through my ISP.  Never had a need to worry about reverse dns before.  Got that setup and it appears to be functioning now, still seems to be slow at receiving emails but that is probably in a config somewhere that I can play with.
what is your main.cf file content?

---

### Post by steven6282 on 2012-02-15
I may have been wrong, the reverse DNS may not have fixed it.

I thought it did because as soon as my reverse dns propegated I got one email from gmail that I had sent 14 hours earlier.  But now it's been over 12 hours since the last test I sent and I still have not received it.  My emails to gmail and other places go through instantly.

And another weird occurrence, using another one of my email accounts with a domain I own hosted on bluehost, it gives me error 550 saying the user does not exist at the server, but I know it does.

This is my main.cf file:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname
myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = mail.mydomain.com, mydomain.com, localhost.mydomain.com, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

---

### Post by steven6282 on 2012-02-15
Well after doing some more digging, it's some kind of CA problem I think.  I've never had to mess with all this CA stuff so I'm kind of at a loss.  Trying to read up on it.

Looking through the mail.log though shows the TLS is disabled because it can't find some file.  Then when it has messages come in from gmail, it says the CA is untrusted and rejects the message.

---

### Post by steven6282 on 2012-02-15
Ok, I did this.  My server is actually running ESXi, so I just set up another server, loaded server 11.10 64 bit on it, and configured it for a mail server during the install.  (Previously I was trying to set it up on my webserver which is still server 10.10 atm)

Pointed my email ports to the new one and now it works flawlessly.

I'm not really sure why... ?  But I'll go with it.  I suppose it can be useful to have the servers separated virtually anyway.

---

### Post by aoitenshi on 2012-02-24
hi,

I'm having similar problem, this is my main.cf

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/lib/postfix
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 0
mydestination = mail.studiodhika.com, localhost.studiodhika.com, localhost, studiodhika.com
mydomain = studiodhika.com
myhostname = server.studiodhika.com
mynetworks_style = host
recipient_delimiter = +
setgid_group = postdrop
smtpd_banner = $myhostname ESMTP ispCP 1.0.7 OMEGA Managed
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks,reject_invalid_helo_hostname,                               reject_non_fqdn_helo_hostname
smtpd_recipient_restrictions = reject_non_fqdn_recipient,                               reject_unknown_recipient_domain,                               permit_mynetworks,                               reject_unauth_destination,                               reject_unlisted_recipient,
smtpd_sender_restrictions = reject_non_fqdn_sender,                               reject_unknown_sender_domain,                               permit_mynetworks,
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/cert.pem
smtpd_tls_key_file = /etc/postfix/privkey.pem
smtpd_tls_loglevel = 2
smtpd_tls_received_header = yes
smtpd_use_tls = yes
virtual_alias_domains = server.studiodhika.com server
virtual_alias_maps = hash:/etc/postfix/ispcp/aliases
virtual_gid_maps = static:8
virtual_mailbox_base = /var/mail/virtual
virtual_mailbox_domains = hash:/etc/postfix/ispcp/domains
virtual_mailbox_limit = 0
virtual_mailbox_maps = hash:/etc/postfix/ispcp/mailboxes
virtual_minimum_uid = 1001
virtual_uid_maps = static:1001


```

can anyone help me with my problem?
Thanks a lot

---

