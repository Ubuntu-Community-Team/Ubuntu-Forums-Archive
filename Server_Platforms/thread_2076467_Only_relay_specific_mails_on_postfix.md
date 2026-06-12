---
title: "Only relay specific mails on postfix"
date: 2012-10-26
forum: Server Platforms
---

### Post by fletschge on 2012-10-26
Hello,

I'm inside an environment of a Microsoft Exchange 2010 Server as well as a Ubuntu 12.04.1 LTS Server, which is running apache on it.
Now I need to send emails in PHP through sendmail. This is working excellent and relays all sent emails to the exchange server, which afterwards actually sends the message.

But: Ubuntu sometimes generates system emails (which are perfectly OK and necessary). For instance when something went wrong in the system or something bad happened. This happend to me in one case where a PHP library was missing and every time the php command was called it generated an email. This email was sent to the exchange server instead of being sent to the local root mailbox.

Now the question: How can I keep system emails at the ubuntu server and only send/relay the emails I "manually" sent via sendmail to the exchange server?

I'm admin of both servers, so I am able to change anything.

Thank you very much for any help!


Postfix main.cf:

```


smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost.localdomain, localhost
relayhost = myexchangeserver.local
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
default_transport = smtp
relay_transport = smtp


# enable SASL for authentication
smtp_sasl_auth_enable = yes
# force AUTH LOGIN mechanism. Else Postfix might try something else
smtp_sasl_mechanism_filter = login
# Override Postfix default disallowing of plaintext AUTH LOGIN
smtp_sasl_security_options =
# use our password database for authentication
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
# map machine email addresses to internet addresses
smtp_generic_maps = hash:/etc/postfix/generic

```

---

### Post by BatkoVanko on 2012-10-30
Hello fletschge
 
Interesting case!
 
Could please remove myorign entry and try again?
 
myorigin should be $myhostname ( default:$myhostname)
 
The domain name that locally-posted mails apears to come from and that locally posted mail is delivered to
 
Good luck!

---

### Post by smtp on 2012-10-30
Could you please list contents of /etc/mailname?

Usually myorigin=$myhostname

myorigin is the domain name that locally-posted mail appears to come from, and that locally posted mail is delivered to.

Also you could try to configure local transport local:$myhostname

---

### Post by fletschge on 2012-10-30
Hello both of you,

First of all: Thank you very much for the responses.

Content of /etc/mailname:
```
company.com
```

Interesting: The exchange server is accessible on this name. However the exchange's domain name is simply 'company'.

The reason for the exchange server being accessible is that I have a split dns environment, so I had to define an A-Record for internal reasons on "company.com".
When I setup the ubuntu server, I didn't know yet that I'll be using an exchange server. So maybe I previously set /etc/mailname to "company.com" (Can't remember though, it must have been set by a configuration wizard where I entered the string).

Maybe my problem is due to a simple coincidence that the content of /etc/mailname is a real acessible server (through A-Record) but it's not the local one?

I'll try setting it to $myhostname and then see if the alerts go away :-)

Thank you for the responses!

---

