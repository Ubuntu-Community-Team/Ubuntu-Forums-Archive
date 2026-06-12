---
title: "Postfix"
date: 2012-02-05
forum: Server Platforms
---

### Post by pkeeney on 2012-02-05
Im using [http://freedns.afraid.org/](http://freedns.afraid.org/) to point my domain to my home server with a dynamic ip address. Im using google apps to send mail out of my server. Here is my problem, sending mail works fine using postfix but receiving mail dose not. I register the domain with google and pointed the ns to freedns so now mail dose not go to google any more it send it to my server and the bounces the error to the google apps account.

I need to know how to set up my system to where it will receiver the emails.

Here is the postfix main.cf file

```

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = chrishomeserver.thunderboltservice.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = 
relayhost = [smtp.gmail.com]:587
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
relay_transport = smtp
inet_protocols = all

# SASL Settings
smtp_use_tls=yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
```

Here is the bounced email

```

Mail Delivery Subsystem [email]mailer-daemon@googlemail.com[/email]
11:09 PM (10 hours ago)

to me 
Delivery to the following recipient failed permanently:

    [email]root@xxxxx.xxx[/email]

Technical details of permanent failure:
DNS Error: Domain name not found

----- Original message -----

Received: by 10.236.127.145 with SMTP id d17mr18362292yhi.131.1328414943860;
       Sat, 04 Feb 2012 20:09:03 -0800 (PST)
Return-Path: <chris@thunderboltservice.com>
Received: from chrishomeserver.thunderboltservice.com (253.192.202.68.cfl.res.rr.com. [68.202.192.253])
       by mx.google.com with ESMTPS id j2sm23634076ani.19.2012.02.04.20.09.02
       (version=TLSv1/SSLv3 cipher=OTHER);
       Sat, 04 Feb 2012 20:09:03 -0800 (PST)
Received: by xxxxxxx.xxx (Postfix, from userid 0)
       id 9D2471B40D7E; Sat,  4 Feb 2012 23:09:01 -0500 (EST)
From: Cron Daemon <chris@xxxxxxx/xxx>
To: [email]root@xxxxxxxx.xxxx[/email]
Subject: Cron <root@chrishomeserver>   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <20120205040901.9D2471B40D7E@xxxxxxxx.xxxx>
Date: Sat,  4 Feb 2012 23:09:01 -0500 (EST)

PHP Warning:  Module 'mysql' already loaded in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/sqlite.so' - /usr/lib/php5/20090626/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0

```

Thanks for any help.

---

### Post by galvatron408 on 2012-02-05
you don't have an MX record. below is an example of querying for your domain and then querying for gmail.com.

> set query=mx
> chrishomeserver.thunderboltservice.com
Server:		192.168.0.1
Address:	192.168.0.1#53

** server can't find chrishomeserver.thunderboltservice.com: NXDOMAIN
> gmail.com
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
gmail.com	mail exchanger = 5 gmail-smtp-in.l.google.com.
gmail.com	mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
gmail.com	mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
gmail.com	mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
gmail.com	mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.

Authoritative answers can be found from:
alt4.gmail-smtp-in.l.google.com	internet address = 74.125.115.26
alt3.gmail-smtp-in.l.google.com	internet address = 74.125.91.27
alt2.gmail-smtp-in.l.google.com	internet address = 74.125.65.26
gmail-smtp-in.l.google.com	internet address = 74.125.127.27

---

### Post by pkeeney on 2012-02-05
I'm confused, Is that telling postfix to send all emails to [email]chris@thunderboltservice.com[/email] back to gmail with the right mx records.


How hard would it be to keep all mail sent to [email]chris@thunderboltservice.com[/email] on chrishomeserver so it can be accessed from SquirrelMail and mail sent out will use google apps gmail.

The host file just uses chrishomeserver should I change that to match postfix (chrishomeserver.thunderboltservice.com)?
Thanks

---

### Post by lisati on 2012-02-05
There is a PHP-related error message there. You might want to investigate.

---

### Post by pkeeney on 2012-02-05
I installed EHCP yesterday and it did so many changes to the system i don't even know where to start. I have about 200 bounced emails sitting in my Google account.

---

### Post by pkeeney on 2012-02-05
Thanks for your help i changed the mx records in  [http://freedns.afraid.org/](http://freedns.afraid.org/) using the Google mx records.

If any one need any help with this here is the Google mx records

10:ASPMX.L.GOOGLE.COM 
20:ALT1.ASPMX.L.GOOGLE.COM 
20:ALT2.ASPMX.L.GOOGLE.COM 
30:ASPMX2.GOOGLEMAIL.COM 
30:ASPMX3.GOOGLEMAIL.COM 

Go to [http://freedns.afraid.org/subdomain/](http://freedns.afraid.org/subdomain/) and create new mx records for your domain.

Click add

Type= Mx

Subdomain leave blank

Domain what ever you domain is

Destination google mx records

---

### Post by pkeeney on 2012-02-06
Can anybody tell me from reading the below bounced email why this is happening?

Do i need to set up a mail box for [email]root@chrishomeserver.thunderboltservice.com[/email]? Is the web server trying to send system email to the above email address?

```
Mail Delivery Subsystem mailer-daemon@googlemail.com
11:40 AM (13 minutes ago)

to me 
Delivery to the following recipient failed permanently:

    root@chrishomeserver.thunderboltservice.com

Technical details of permanent failure:
DNS Error: Domain name not found

----- Original message -----

Received: by 10.236.181.97 with SMTP id k61mr25259743yhm.108.1328546403851;
       Mon, 06 Feb 2012 08:40:03 -0800 (PST)
Return-Path: <chris@thunderboltservice.com>
Received: from chrishomeserver.thunderboltservice.com (253.192.202.68.cfl.res.rr.com. [68.202.192.253])
       by mx.google.com with ESMTPS id k15sm23614810yhf.11.2012.02.06.08.40.02
       (version=TLSv1/SSLv3 cipher=OTHER);
       Mon, 06 Feb 2012 08:40:02 -0800 (PST)
Received: by chrishomeserver.thunderboltservice.com (Postfix, from userid 121)
       id A65AF1B40D7F; Mon,  6 Feb 2012 11:40:01 -0500 (EST)
From: Cron Daemon <chris@thunderboltservice.com>
To: root@chrishomeserver.thunderboltservice.com
Subject: Cron <smmsp@chrishomeserver> test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <MAILTO=root>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/var/lib/sendmail>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=smmsp>
Message-Id: <20120206164001.A65AF1B40D7F@chrishomeserver.thunderboltservice.com>
Date: Mon,  6 Feb 2012 11:40:01 -0500 (EST)

/usr/share/sendmail/sendmail: 1267: /usr/sbin/sendmail-msp: not found
```


Thanks

---

### Post by galvatron408 on 2012-02-06
here is the wiki for mx record. read it really carefully.
[http://en.wikipedia.org/wiki/MX_record](http://en.wikipedia.org/wiki/MX_record)

after you're done with that, go read RFC 974 - Mail routing and The Domain System
[http://tools.ietf.org/html/rfc974](http://tools.ietf.org/html/rfc974)

Then, go on to read RFC 2821 and 2822.

When you're done and if you get it, you'll never have to ask another email question. You can also call yourself the POST MASTER.
---
but, you can't go to the post office and tell them that you should now receive all of Bank Of America's mail and Wells Fargo mail and Discover or chase, because the Post Man will tell you.... "DNS Error: Domain Name Not Found"

---

