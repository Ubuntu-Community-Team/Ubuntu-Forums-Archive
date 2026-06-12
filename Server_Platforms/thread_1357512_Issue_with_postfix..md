---
title: "Issue with postfix."
date: 2009-12-17
forum: Server Platforms
---

### Post by kusumoto on 2009-12-17
I have a system set up with 9.10 and have configured dovecot-postfix on it. It is functioning properly as a POP3 server for the users I added in MySQL, but is unable to send via SMTP with any of those users. This is the bounceback message I got on an outlook client trying to reply to an email it had received.
------------------------------------------------------------

Your message did not reach some or all of the intended recipients.

      Subject:	Test
      Sent:	12/16/2009 16:19

The following recipient(s) could not be reached:

      '{email address removed}' on 12/16/2009 16:19
            451 4.3.5 Server configuration error
---------------------------------------------------------------
I had previously been getting a message that said there was an issue with relay domains or something like that. I don't know why it changed to this. The server is able to receive messages from local and external addresses, but send to none.

Here is my postfix main.cf 

[I]# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = baldwin-desktop
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = baldtel.com, baldwin-desktop, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 100000000000
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sender_restrictions = permit_unknown_sender_domain
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}"
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom[/I]


If anyone has any ideas they are much appreciated. Thank you.

---

### Post by kusumoto on 2009-12-17
Ok it seems that users are unable to receive now also. Either that or a major delay is in effect for some reason. Receiving had been working fine before I started looking into the issue with sending.

edit-> here's my dovecot -n output if that helps

[I]dovecot.conf  dovecot.conf.bak  dovecot-db-example.conf  dovecot-ldap.conf  dovecot-postfix.conf  dovecot-sql.conf
root@baldtel:/etc/dovecot# dovecot -n
# 1.1.11: /etc/dovecot/dovecot.conf
# OS: Linux 2.6.31-16-generic i686 Ubuntu 9.10
log_timestamp: %Y-%m-%d %H:%M:%S
protocols: imap imaps pop3 pop3s
ssl_disable: yes
disable_plaintext_auth: no
login_dir: /var/run/dovecot/login
login_executable(default): /usr/lib/dovecot/imap-login
login_executable(imap): /usr/lib/dovecot/imap-login
login_executable(pop3): /usr/lib/dovecot/pop3-login
mail_privileged_group: mail
mail_location: mbox:~/mail:INBOX=/var/mail/%u
mail_executable(default): /usr/lib/dovecot/imap
mail_executable(imap): /usr/lib/dovecot/imap
mail_executable(pop3): /usr/lib/dovecot/pop3
mail_plugin_dir(default): /usr/lib/dovecot/modules/imap
mail_plugin_dir(imap): /usr/lib/dovecot/modules/imap
mail_plugin_dir(pop3): /usr/lib/dovecot/modules/pop3
auth default:
  passdb:
    driver: pam
  passdb:
    driver: sql
    args: /etc/dovecot/dovecot-sql.conf
  userdb:
    driver: passwd
  userdb:
    driver: sql
    args: /etc/dovecot/dovecot-sql.conf[/I]

---

### Post by chipper_farley on 2009-12-17
for the sending problem, try adding:

relay_domains=$mydestination

---

