---
title: "[SOLVED] &amp;quot;Sender Address Rejected&amp;quot; error sending mail with postfix"
date: 2008-09-13
forum: Server Platforms
---

### Post by Rounan on 2008-09-13
I am running a server with a RAID5 using mdadm, and I want it to email me a notification to my gmail if one of the disks drops. mdadm uses /bin/mail to send its message, and it is not getting through my ISP's SMTP server- my isp is cogeco.ca. I have a typical home user internet service- I do not own a domain, and my IP and the specific subdomain I am on changes (hama4.on.cogeco.ca, today).

I have postfix installed, but my only usage is sending mail in this one specific case - I have read a couple postfix tutorials and they are all way, way more complicated than I can follow.

When I do:
```
$mail -s test user@gmail.com
```

I get this in /var/log/mail.info:

```
Sep 13 12:22:41 server postfix/smtp[20214]: D255697C0F: to=<user@gmail.com>, 
relay=mail.cogeco.ca[216.221.81.25]:25, delay=0.13, delays=0.04/0.01/0.06/0.03, 
dsn=4.0.0, status=deferred (host mail.cogeco.ca[216.221.81.25] said: 
450 <user@server.hama4.on.cogeco.ca>: Sender address rejected: Domain not found (in reply to RCPT TO command))
```

The problem persists if I use:
```
mail -s test -a From:user@gmail.com user@gmail.com
```

I need to be able to change the sender address in the email header to a valid email - I can use my user@gmail address, or I have a user@cogeco address if my ISP doesn't like relaying gmail addies.

My /etc/postfix/main.cf:
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = cogeco.ca
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = cogeco.ca, localhost
relayhost = smtp.cogeco.ca
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only

smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
relay_domains =
```

and the contents of /etc/aliases, which was set up to try to get the mdadm email (from root) to use a valid addie:
```
# Added by installer for initial user
postmaster: root
root:   user@cogeco.ca
```

---

### Post by windependence on 2008-09-13
Yes, it doesn't like the fact that you have no PTR (reverse DNS) record. It can't verify who you are from your IP address.

-Tim

---

### Post by gombadi on 2008-09-14
Not sure if this is the correct method but :-)

In /etc/postfix/main.cf there is -

> myorigin = /etc/mailname

As root edit this file so it says cogeco.ca

This is the file that tells postfix what name to call the server and if you set it to cogeco.ca then your ISP machines should accept it. Of course they may complain that sender is using their domain name but if you are a client of the cogeco.ca ISP then they should accept it without problems.

---

### Post by Rounan on 2008-09-14
Thank you, gombadi!

changing the contents of /etc/mailname from "server.hama4.on.cogeco.ca" to "cogeco.ca" did the trick. Mail now gets through.

---

