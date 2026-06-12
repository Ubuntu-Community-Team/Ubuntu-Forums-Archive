---
title: "Postfix &amp; request tracker"
date: 2009-01-16
forum: Server Platforms
---

### Post by slacker9876 on 2009-01-16
Hello Everyone, 
I am attempting to implement postfix for my organisation to mange help desk requests. The RT and Apache pieces are working and I am able to access the help desk by IP, however, it is not sending or receiving the mail as desired into the ticketing system. I know I am missing at least one parameter, I just do not know what it is. Here is my main.cf

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.

mydomain = officesource.com
myorigin = $mydomain

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

myhostname = helpdesk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname officesource.com localhost.$mydomain localhost
relayhost = gwsmtp.usa.net
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
```What I have read here and at postfix.org is an SMTP engine, so I am not sure how the system would receive mail. I have spent the better part of the last two days try to get this automation to work without success and would truly appreciate help for anyone who is able.

Our mail is currently hosted with USA.net and I need to use their server in my configuration.

---

### Post by slacker9876 on 2009-01-16
OK so I now see rt-mailagte does the send. Is anyone able to help with my main.cf to get the mail flowing out?

---

### Post by HermanAB on 2009-01-16
There exists a couple of special programs for use with web servers and the like to forward mail to another full featured mail server.  Since these programs only implement a subset of the SMTP, they are very easy to set up.  Here is nullmailer:
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

You will have it going in no time.

Cheers,

Herman

---

### Post by slacker9876 on 2009-01-16
I appreciate the alternative method, however, RT is too tied in with perl to modify at this point. I will try this on another computer in my home office over the weekend. But I need to understand postfix and I need it to process the RT requests.

---

