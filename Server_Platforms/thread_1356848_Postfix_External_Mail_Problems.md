---
title: "Postfix External Mail Problems"
date: 2009-12-16
forum: Server Platforms
---

### Post by linuxus95 on 2009-12-16
Hi, and thanks for all potential replies :) I am successfully running a small home all-use server with Apache, OpenSSL, MySQL and Postfix. Everything works fine with postfix until I want to send email to external domains (gmail, yahoo etc). When i telnet into my postfix server and type in an external domain for rcpt to:, I get the message that relay access is denied. Interestingly enough, when I ssh into the actual server and i telnet to localhost port 25 on the server, postfix will let me send external email. I also tried to use webmin to enable this feature, but when I unchecked "Reject Email to External Domains," postfix would refuse to accept any incoming connections, so it would just freeze when I tried to telnet into it. I have managed to successfully set this up in the past, but I have no idea how i did it. This is driving me absolutely crazy, so I will greatly appreciate any replies  :P. Thanks.

---

### Post by Krupski on 2009-12-16
> **linuxus95 said:**
> Hi, and thanks for all potential replies :) I am successfully running a small home all-use server with Apache, OpenSSL, MySQL and Postfix. Everything works fine with postfix until I want to send email to external domains (gmail, yahoo etc). When i telnet into my postfix server and type in an external domain for rcpt to:, I get the message that relay access is denied. Interestingly enough, when I ssh into the actual server and i telnet to localhost port 25 on the server, postfix will let me send external email. I also tried to use webmin to enable this feature, but when I unchecked "Reject Email to External Domains," postfix would refuse to accept any incoming connections, so it would just freeze when I tried to telnet into it. I have managed to successfully set this up in the past, but I have no idea how i did it. This is driving me absolutely crazy, so I will greatly appreciate any replies  :P. Thanks.

I don't know if this applies... but I recently ran into a problem where my ISP stopped accepting automated emails (logs) from my Ubuntu server box.

I found that my ISP decided to no longer accept email from "root@(anything)" for security reasons.

So, forcing SENDMAIL to use my real email address for the "From:" field fixed the problem.

The ORIGINAL line (that stopped working) was like this:

```

cat log-summary.dat | sendmail -t

```

The fix was:

```

cat log-summary.dat | sendmail [COLOR="Red"]-f myname@domain.com[/COLOR] -t

```

By adding the -f option (shown in red) the "From:" field was changed from "root@..." to "myname@...".

(obviously, "myname" is an example... I used my real email address).

Hope this helps.

-- Roger

---

### Post by gombadi on 2009-12-16
In /etc/postfix/main.cf file there is a setting for mynetworks.

At the moment I would guess it only has 127.0.0.1/8. You need to add an entry for the ip address or range that you want to be able to relay email via your server. i.e.

```

mynetworks = 127.0.0.1/8,192.168.0.0/24

```

After this reload postfix and try again.

---

### Post by windependence on 2009-12-16
Gombadi has the answer. 

You will find, however, that you need reverse DNS to have your mail accepted by most servers. With mail servers, unless you set it up right, much of your mail will end up trashed as Spam. This is one reason I rely on Zimbra. Version 6 is really easy to set up and works great.

-Tim

---

### Post by linuxus95 on 2009-12-20
Hi, and many thanks to all of you guys, especially to gombaldi. After adding the 192.168.0.0/24 into the "My Networks" section, everything works just fine. Could somebody please point me towards configuring the reverse dns lookup, as I do not want all of my email to end up in people's spam folders (happens with gmail and yahoo).

---

### Post by madmacz on 2010-01-09
I have a similar problem. I can't send email to external domains. I get the following message in mail.log

Jan  8 10:45:20 mail postfix/smtpd[14911]: connect from unknown[]
Jan  8 10:45:21 mail postfix/smtpd[14911]: NOQUEUE: reject: RCPT from unknown[]: 550 5.1.1 <[EMAIL="lobomacz@gmail.com"]lobomacz@gmail.com[/EMAIL]>: **Recipient address rejected: User unknown in local recipient table**; from=<[EMAIL="user@midominio.com"]user@mydomain.com[/EMAIL]> to=<[EMAIL="lobomacz@gmail.com"]lobomacz@gmail.com[/EMAIL]> proto=ESMTP helo=<[10.24.4.230]>
 Jan  8 10:45:21 mail dovecot: pop3-login: Login: user=<user>, method=PLAIN, rip=, lip=
Jan  8 10:45:22 mail postfix/smtpd[14911]: disconnect from unknown[]


my [main.cf]("http://main.cf/") is as follows


smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no


readme_directory = no

smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

myhostname = [mail.mydomain.com]("http://mail.midominio.com/")
mydomain = [mydomain.com]("http://midominio.com/")
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = /etc/postfix/domains
relayhost = 
mynetworks = [127.0.0.0/8]("http://127.0.0.0/8"), [10.30.0.0/16]("http://10.30.0.0/16"), [192.168.0.0/24]("http://192.168.0.0/24")
mynetworks_style = class
mailbox_command = 
mailbox_size_limit = 104857600
message_size_limit = 20971520
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
relay_domains = $mydestination

---

### Post by fmmarzoa on 2010-01-21
I'm having the same problem of madmacz, Did you finally solve it?

---

### Post by lisati on 2010-01-21
**Disclaimer:** My $0.02 is not intended to hijack thread.

My ISP blocks port 25 by default, perhaps there's some filtering going on. I'm currently experiencing my own mini saga related to this: I've followed the instructions on my ISP's website for opting out of their filtering, and have confirmed that it's showing at their end. As near as I can make out, there's still *something* blocking my efforts in both directions: outgoing connections resulting in connection timeouts, and the Shields Up website can't get through to port 25.

edit: found out a likely cause: buried on their "Static IP" page there's a comment saying that I'll need a static IP. Didn't show up when I searched their site for "Port 25". Now who can I shoot?

---

