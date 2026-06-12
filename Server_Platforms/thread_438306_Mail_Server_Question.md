---
title: "Mail Server Question"
date: 2007-05-09
forum: Server Platforms
---

### Post by TorchlightJay on 2007-05-09
So this is the most retarded question ever, is it possible to have two email domains run on the same server or static IP? Yes, I know, it's dumb. Also, what's the best mail server app for Ubuntu? I was thinking of Postfix or something, tie in Webmin for the administration purposes, maybe squirrlelmail and mailman. Any other suggestions? I am not an expert of Windows email so anything will help. Thanks

---

### Post by TorchlightJay on 2007-05-09
Not an expert at Linux email. Sorr

---

### Post by MJN on 2007-05-09
No such thing as a dumb question.

Running multiple mail domains on the same server is no problem at all, indeed it's quite common.

Regarding the 'best' mail server, well that's down to opinion so whilst I've got the floor I'd recommend Postfix. Squirrelmail for your webmail is good too - works very well. You would need an IMAP server (I recommend Dovecot) to support this (or any other e-mail client for that matter, although a POP3 server would suffice if you're into retro ;)).

I've never used Mailman so can't comment either way.

As a general recommendation I'd strongly suggest starting small - say just with Postfix sending/receiving mail and then add your IMAP server and connect with a 'standard' client (Kmail, Evolution etc) before moving on to adding Squirrelmail. Doing the whole lot in one is asking for major headaches (unless you're blindly following one of the many HowTo's - most of which don't actually *teach* you very much and leave you out to dry if you subsequently face problems).

Mathew

---

### Post by TorchlightJay on 2007-05-09
Sweet, so any idea how I can set up two (or maybe just one) email domain with Postfix? Thanks.

---

### Post by Enverex on 2007-05-09
> **MJN said:**
> No such thing as a dumb question.

I believe the quote is "there's no such thing as stupid question, just stupid people" ;)

Anyway, I use Exim on my server but to be honest it's a bit of a nightmare configuration wise unless you like coding. Any mail server apps should be able to support as many domains as you need.

---

### Post by riscostm on 2007-05-10
Hi Guys,

I have mail question for you.

Installation is ubuntu fiesty and mysql +dovecot + postfix.

I seem to be get a lot of mail 550 delivery errors. I followed the procedure on the below link

[http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/](http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/)

also here is may main.cf file 

Show me the light please!!

 # See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/mailserver/mail-cert.pem
smtpd_tls_key_file = /etc/ssl/mailserver/mail-key.pem
smtpd_tls_session_cache_database = btree:/var/spool/postfix/smtpd_tls_session_cache
smtpd_tls_security_level = may
smtpd_tls_received_header = no
smtpd_tls_loglevel = 0
tls_random_source = dev:/dev/urandom

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = domain.com
myorigin = /etc/mailname
mynetworks = 127.0.0.0/8, 192.168.#.#/24
mailbox_size_limit = 0
message_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
#smtpd_sender_restrictions = reject_non_fqdn_sender,reject_unknown_sender_domain
mydestination = 
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes

# SASL Authentication
smtpd_sasl_auth_enable = yes
smtpd_sasl_exceptions_networks = $mynetworks
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_helo_required = yes
#Disables NIS Lookup Code
#alias_maps = proxy:mysql:$config_directory/mysql_virtual_alias_maps.cf

#Virtual Mailboxes Settings
virtual_mailbox_domains = proxy:mysql:$config_directory/mysql_virtual_domains_maps.cf
#All mail is held in this locatation
virtual_mailbox_base = /var/vmail
virtual_mailbox_maps = proxy:mysql:$config_directory/mysql_virtual_mailbox_maps.cf
virtual_alias_maps = proxy:mysql:$config_directory/mysql_virtual_alias_maps.cf
virtual_minimum_uid = 150
virtual_uid_maps = static:150
virtual_gid_maps = static:8
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1

#Amavis New
content_filter = smtp-amavis:[127.0.0.1]:10024

#ISP Relay Host
relayhost = domain.co.uk
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
inet_protocols = all


Any help would be very greatful :D
Cheers
Riscostm

---

### Post by MJN on 2007-05-10
Show us your logs (/var/log/mail.log) as otherwise we're shooting blind...

Mathew

---

