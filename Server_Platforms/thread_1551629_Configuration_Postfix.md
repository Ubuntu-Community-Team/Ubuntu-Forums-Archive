---
title: "Configuration Postfix"
date: 2010-08-12
forum: Server Platforms
---

### Post by d4ng3r92 on 2010-08-12
Hi! Sorry for my english...
I installed postfix on my server but i'm not able to send emails: they go out with user@localhost instead of [email]user@[user-no-ip].no-ip.biz[/email]

This is my configuration file:

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

myhostname = mail.d4ng3.no-ip.biz
mydomain = d4ng3.no-ip.biz
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = d4ng3r.no-ip.biz, localhost, localhost.localdomain, localhost
relayhost = out.alice.it
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
masquerade_domains = d4ng3r.no-ip.biz

```

Thanks

---

### Post by NIT006.5 on 2010-08-12
What's the content of /etc/mailname? That should contain your origin domain.

---

### Post by d4ng3r92 on 2010-08-12
/etc/mailname :

```

d4ng3r.no-ip.biz

```

is correct?

---

### Post by NIT006.5 on 2010-08-12
Yes, that should be correct.

I don't know if this would cause that kind of issue, but you seem to be a missing the "r" in the hostname and domain:

```

myhostname = mail.d4ng3.no-ip.biz
mydomain = d4ng3.no-ip.biz

```

instead of mail.d4ng3r.no-ip.biz and d4ng3r.no-ip.biz.

---

### Post by NIT006.5 on 2010-08-12
Oh, and you would also need to add your local network address to mynetworks to allow sending from other computers on the network.

---

### Post by d4ng3r92 on 2010-08-12
this is my new configuration:

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

myhostname = mail.d4ng3r.no-ip.biz
mydomain = d4ng3r.no-ip.biz
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = d4ng3r.no-ip.biz, localhost, localhost.localdomain, localhost
relayhost = out.alice.it
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.1/255
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
masquerade_domains = d4ng3r.no-ip.biz

```

but the email send with danger@localhost ---> 

```

<xxx@gmail.com>: host out.alice.it[82.57.200.132] said: 553
    <danger@localhost> Invalid mail address, must be fully qualified domain (in
    reply to MAIL FROM command)

```

---

### Post by NIT006.5 on 2010-08-13
Is there a specific reason you have masquerade_domains set? Can you try with that line commented out?

---

### Post by d4ng3r92 on 2010-08-13
I commented the line masquerade_domains:
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

myhostname = mail.d4ng3r.no-ip.biz
mydomain = d4ng3r.no-ip.biz
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = d4ng3r.no-ip.biz, localhost, localhost.localdomain, localhost
relayhost = out.alice.it
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.1/255
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
# masquerade_domains = d4ng3r.no-ip.biz

```
I choose this configuration in order to avoid to send email by user@localhost... but nothing has changed :(

---

### Post by NIT006.5 on 2010-08-13
I've just checked one of my servers' configs (which I should have done long ago)... the only real difference I can see, is that for myhostname I wouldn't have used the fully qualified domain name i.e. instead of mail.d4ng3r.no-ip.biz, just change it to "mail" without the domain name.

```

myhostname = mail

```

Try that and let me know?

You shouldn't need to masquerade anything, so you can leave that line commented out.

---

### Post by d4ng3r92 on 2010-08-13
this is my new configuration:

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

myhostname = mail
mydomain = d4ng3r.no-ip.biz
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = d4ng3r.no-ip.biz, localhost, localhost.localdomain, localhost
relayhost = out.alice.it
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.1/255
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
masquerade_domains = d4ng3r.no-ip.biz

```

I tried to send an email from my server at my account gmail and I recive an error-mail:
```

<danger@localhost> Invalid mail address, must be fully qualified domain (in
    reply to MAIL FROM command)

``` 
And I tried send an email from gmail at my server, I read the email on my server correctly but I recive on my account another error-email:
```

This is an automatically generated Delivery Status Notification

THIS IS A WARNING MESSAGE ONLY.

YOU DO NOT NEED TO RESEND YOUR MESSAGE.

Delivery to the following recipient has been delayed:

    danger@d4ng3r.no-ip.biz

Message will be retried for 1 more day(s)

Technical details of temporary failure:
The recipient server did not accept our requests to connect. Learn more at http://mail.google.com/support/bin/answer.py?answer=7720
[d4ng3r.no-ip.biz (1): Connection dropped]

----- Original message -----

MIME-Version: 1.0
Received: by 10.239.163.6 with SMTP id n6mr255412hbd.41.1281548406749; Wed, 11
       Aug 2010 10:40:06 -0700 (PDT)
Received: by 10.239.172.7 with HTTP; Wed, 11 Aug 2010 10:40:06 -0700 (PDT)
Date: Wed, 11 Aug 2010 19:40:06 +0200
Message-ID: <AANLkTimtVGiV59KhCg_PdK1upi+9TQE=k8AgHBEBdLic@mail.gmail.com>
Subject: Prova
From: xxx <xxx@gmail.com>
To: danger@d4ng3r.no-ip.biz
Content-Type: multipart/alternative; boundary=001485f272088c0533048d8fbdf9

```

Sorry for my english xD

---

### Post by NIT006.5 on 2010-08-13
Confirm you are reloading postfix config each time it is changed? Perhaps try restarting postfix completely if you haven't been doing so. If all else fails, have you rebooted the server completely recently?

One minor point: your local network address should be 192.168.1.0/24 if you want other computers on the network to send mail - but that wouldn't have anything to do with the current problem.

I would also still recommend leaving masquerade commented out to avoid any confusion - it definitely should not be needed there.

I don't have any other ideas at the moment :(

---

### Post by d4ng3r92 on 2010-08-13
Yes I restart with /etc/init.d/postifix restart.
I tried to send email with Webmin.
I commented masquereade but the email send by danger@localhost :(

If I change the server's name? At the moment is localhost. The server's name must be equal to d4ng3r.no-ip.biz??

:( Thanks for the patient :D

---

### Post by NIT006.5 on 2010-08-13
Ah! Change the server's hostname to "mail". 

For immediate change:
```

hostname mail

```

To make change permanent after reboot, put this one hostname into /etc/hostname:
```

mail

```

Change also /etc/hosts:
```

127.0.0.1	localhost
127.0.1.1	mail.d4ng3r.no-ip.biz mail

```

There might also be other things that are necessary, depending on your number of interfaces and their configuration, and how DNS records have been set up publicly for your domain... but try this first and see.

---

### Post by d4ng3r92 on 2010-08-13
Wonderful!!!! 

At the moment I recive the email at my gmail account but by [email]danger@mail.d4ng3r.no-ip.biz[/email] and not by [email]danger@d4ng3r.no-ip.biz[/email]

:D

---

### Post by NIT006.5 on 2010-08-13
Confirm /etc/mailname is still set to d4ng3r.no-ip.biz and NOT mail.d4ng3r.no-ip.biz??

Can you also try with the masquerade line commented out again?

---

### Post by d4ng3r92 on 2010-08-13
Yes, /etc/mailname is:
```

d4ng3r.no-ip.biz

```

The main.cf is:
```

...
masquerade_domains = d4ng3r.no-ip.biz
...

```

but the email send by [email]danger@mail.d4ng3r.no-ip.biz[/email] and if I try to reply not work.

---

### Post by NIT006.5 on 2010-08-13
Please comment out the masquerade line. This would only be necessary if you wanted this server to masquerade for other servers on the network. It should not be needed.

For incoming mail:
1. Does this server have a public IP, or is port 25 being forwarded by a router? One of these should be necessary. At present there is a public IP for d4ng3r.no-ip.biz - is this for your server? Connections to port 25 on that IP are timing out so it's possible that you're behind a router/firewall that is blocking traffic.
2. Do you have access to manage DNS for your domain or not? You will need to make sure that MX records are set so that other servers know where to direct mail for your domain.

---

### Post by d4ng3r92 on 2010-08-13
The  connection will not be blocked because the email from gmail and  [email]danger@d4ng4r.no-ip.biz[/email] addressed to arrive, but not to mail.d4ng3r.biz.
I can not change the MX records.
My  public IP address is d4ng3r.no-ip.biz,
Emails should be sent with [email]danger@d4ng3r.no-ip.biz[/email] and not with [email]danger@mail.d4ng3r.no-ip.biz[/email].

---

### Post by NIT006.5 on 2010-08-14
Ok that makes sense now. I had misunderstood and thought no mail was coming in.

I'm honestly not sure why it's not sending with the right address - I haven't had this issue before myself. I will give it some thought.

---

### Post by NIT006.5 on 2010-08-14
have you removed the masquerade line??

---

### Post by d4ng3r92 on 2010-08-15
Yes I  removed the masquerade line.

I do not understand why not send from gmail. Need to change MX record?
Now I changed the hostname d4ng3r.no-ip.biz so that emails arrive with the right address.
The problem is that now I can not respond despite being the first address (danger@d4ng3r.no-ip.biz)

---

### Post by d4ng3r92 on 2010-08-17
Up

---

