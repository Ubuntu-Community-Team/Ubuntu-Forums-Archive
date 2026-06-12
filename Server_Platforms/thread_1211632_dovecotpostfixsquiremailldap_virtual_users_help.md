---
title: "dovecot/postfix/squiremail/ldap virtual users help"
date: 2009-07-12
forum: Server Platforms
---

### Post by jbollom on 2009-07-12
Hey All,

I'm attempting to setup a student mail system running on ubuntu server which needs to authenticate to a windows 2003 server box for authentication

Atm im using postfix, dovecot, and squiremail

im all new to this mail stuff and cant seem to get the virtual users working

my main.cf is as follows

```
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

readme_directory = no

# TLS parameters

#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_use_tls=no
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

#smtpd_sasl_local_domain = 
#smtpd_sasl_auth_enable = yes
#smtpd_sasl_security_options = noanonymous
#broken_sasl_auth_clients = yes
#smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

# myhostname = my2.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.example.com, my3.example.com, , my2
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all



inet_protocols = all
biff = no
mail_spool_directory = /var/spool/mail
# myhostname = my2.example.com
# mydomain = my3.example.com
# mydestination = localhost.$mydomain,localhost,$mydomain,$myhostname
mynetworks = 10.2.20.0/24 127.0.0.1
mynetworks_style = subnet




local_recipient_maps = ldap:/etc/postfix/ldap-user-auth.cf
local_transport = virtual
virtual_mailbox_domains = my2.example.com
virtual_mailbox_base = /var/spool/vmail
virtual_mailbox_maps = hash:/etc/postfix/virtual_mailboxes
virtual_minimum_uid = 500
virtual_uid_maps = static:500
virtual_gid_maps = static:12
```

and here is my ldap-user-auth.cf

```
server_host = studentserver
search_base = dc=students,dc=domain
version = 3
query_filter = (&(objectClass=Person)(uid=%s))
result_attribute = uid
bind = yes
bind_dn = students\administrator
bind_pw = password
```

if anyone has any ideas plz let me know

atm im unable to send mail to any virtual accounts on the server recieving the error Recipient address rejected: User unknown in virtual mailbox table>

and im unable to send mail from the server reciving the error in squirlmail Relay access denied
and in my mail log 
Jul 13 11:31:17 my2 postfix/smtpd[6051]: connect from localhost[::1]
Jul 13 11:31:17 my2 postfix/smtpd[6051]: NOQUEUE: reject: RCPT from localhost[::1]: 554 5.7.1 <jbollom@acap.edu.au>: Relay access denied; from=<user@my2.example.com> to=<user@mailserver.com> proto=ESMTP helo=<my2.example.com>
Jul 13 11:31:17 my2 postfix/smtpd[6051]: lost connection after RCPT from localhost[::1]
Jul 13 11:31:17 my2 postfix/smtpd[6051]: disconnect from localhost[::1]

---

