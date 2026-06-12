---
title: "Local SMTP server with Postfix"
date: 2010-10-02
forum: Server Platforms
---

### Post by manosone on 2010-10-02
Hello to everyone,

I want to setup an email client in order to send/receive emails,  but since i am experiencing some issues with my ISP, i decided to setup an SMTP server with Postfix on my machine.

The problem is that i can receive emails but i can not send.
I read almost every thread in here refering to Postfix, but i could not find the problem on my configuration.

So here it is..

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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $myhostname, localhost.$mydomain, $mydomain
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128,192.168.1.0/24

mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = localhost
default_transport = error
relay_transport = error
inet_protocols = ipv4

```


Did you find something i missed?

---

### Post by lisati on 2010-10-02
What error messages are you receiving?

Just a hunch, but the following two lines might be part of the problem (they're not present in my server's main.cf file):
> default_transport = error
relay_transport = error

If you have a domain name, you might also want to edit the line "myhostname =" line to reflect its name.

---

### Post by manosone on 2010-10-03
Thanks for the answer but it didnt helped.
Any other ideas?

---

### Post by SeijiSensei on 2010-10-04
[http://ubuntuforums.org/showpost.php?p=9895912&postcount=2](http://ubuntuforums.org/showpost.php?p=9895912&postcount=2)

If you send a test message, what do you see in /var/log/mail.log?

---

### Post by manosone on 2010-10-05
Well,i could manage to send mail(to my own account),but i could not receive it.

The server where my account is hosted,replied that some spam mails were sent and if i would like to mark the sender as a non spammer.
(Obviously the sender is me)

So,how can i send emails without mail services think that i am a spammer?

---

### Post by druhboruch on 2010-10-05
Just as a test I would try to set the line
relayhost =  your.providers.smtp.server

It may be that your provider is blocking/restricting traffic on port 25

---

### Post by manosone on 2010-10-08
> **SeijiSensei said:**
> [http://ubuntuforums.org/showpost.php?p=9895912&postcount=2](http://ubuntuforums.org/showpost.php?p=9895912&postcount=2)

If you send a test message, what do you see in /var/log/mail.log?

Oct  8 19:11:01 ourlaptop postfix/smtp[7551]: 3C4971008A8: to=<***@**>, relay=none, delay=21, delays=0.13/0.02/21/0, dsn=4.4.1, status=deferred (connect to smtp.telefonica.es[194.224.58.55]:25: Connection timed out)

> **druhboruch said:**
> Just as a test I would try to set the line
relayhost =  your.providers.smtp.server

It may be that your provider is blocking/restricting traffic on port 25

I did set the relayhost=smtp.telefonica.es but i didnt mentioned any changes.

If i set the hostname to hostname=a.dynamic.dns.service that i'll create,will it be any different?

---

