---
title: "Postfix spam from my server, please help"
date: 2016-01-13
forum: Server Platforms
---

### Post by yoram2 on 2016-01-13
Hi guys,
my postfix mail server is sending spam.
My provider blocked my IP adress for sending mail and I'm trying to understand and find the problem, please help me.
My domain mail is managed by google apps, I already put a SPF domain record to prevent sending from my domain.

Here are the 20 last lines of my mail.log file

```
Jan 13 17:57:48 #myservername# postfix/smtp[13799]: connect to kimail01.capitalone.com[199.244.214.199]:25: Connection timed outJan 13 17:58:16 #myservername# postfix/smtp[13800]: connect to mx3.hotmail.com[65.55.33.135]:25: Connection timed out
Jan 13 17:58:16 #myservername# postfix/smtp[13794]: connect to uidappmx04.nottingham.ac.uk[128.243.43.127]:25: Connection timed out
Jan 13 17:58:17 #myservername# postfix/smtp[13796]: connect to imailv2.emirates.net.ae[86.96.229.27]:25: Connection timed out
Jan 13 17:58:17 #myservername# postfix/smtp[13796]: 541FB249A8: to=<declan@shp.ae>, relay=none, delay=4422, delays=4301/0.02/121/0, dsn=4.4.1, status=deferred (connect to imailv2.emirates.net.ae[86.96.229.27]:25: Connection timed out)
Jan 13 17:58:17 #myservername# postfix/smtp[13795]: connect to owa.indyzoo.com[207.67.84.147]:25: Connection timed out
Jan 13 17:58:18 #myservername# postfix/smtp[13799]: connect to kimail05.capitalone.com[199.244.214.203]:25: Connection timed out
Jan 13 17:58:46 #myservername# postfix/smtp[13800]: connect to mx2.hotmail.com[65.54.188.126]:25: Connection timed out
Jan 13 17:58:46 #myservername# postfix/smtp[13800]: 43C7824AA7: to=<karenmackenzieharris@hotmail.com>, relay=none, delay=4122, delays=3972/0.04/150/0, dsn=4.4.1, status=deferred (connect to mx2.hotmail.com[65.54.188.126]:25: Connection timed out)
Jan 13 17:58:46 #myservername# postfix/smtp[13794]: connect to uidappmx03.nottingham.ac.uk[128.243.43.126]:25: Connection timed out
Jan 13 17:58:46 #myservername# postfix/smtp[13794]: A81C1249A6: to=<nigel.kendall@nottingham.ac.uk>, relay=none, delay=4457, delays=4307/0.01/150/0, dsn=4.4.1, status=deferred (connect to uidappmx03.nottingham.ac.uk[128.243.43.126]:25: Connection timed out)
Jan 13 17:58:47 #myservername# postfix/smtp[13795]: connect to mx1.mail.twtelecom.net[2001:4870:8000:1::68]:25: Connection timed out
Jan 13 17:58:47 #myservername# postfix/smtp[13795]: 2184624929: to=<nfletchall@indyzoo.com>, relay=none, delay=4466, delays=4315/0.01/151/0, dsn=4.4.1, status=deferred (connect to mx1.mail.twtelecom.net[2001:4870:8000:1::68]:25: Connection timed out)
Jan 13 17:58:48 #myservername# postfix/smtp[13799]: connect to kimail02.capitalone.com[199.244.214.200]:25: Connection timed out
Jan 13 17:58:48 #myservername# postfix/smtp[13799]: 4F15D2205B: to=<CustomerAccounts@capitaloneonline.co.uk>, relay=none, delay=17496, delays=17344/0.03/152/0, dsn=4.4.1, status=deferred (connect to kimail02.capitalone.com[199.244.214.200]:25: Connection timed out)
Jan 13 18:01:16 #myservername# postfix/qmgr[27949]: CF1B7249A4: from=<acinonyxkat@typia.fr>, size=677, nrcpt=1 (queue active)
Jan 13 18:01:16 #myservername# postfix/qmgr[27949]: 06E3524AB6: from=<the.forrests@typia.fr>, size=721, nrcpt=1 (queue active)
Jan 13 18:01:16 #myservername# postfix/qmgr[27949]: 069C624927: from=<sam.bayley@typia.fr>, size=689, nrcpt=1 (queue active)
Jan 13 18:01:16 #myservername# postfix/qmgr[27949]: A605724A57: from=<resmguarniere@typia.fr>, size=726, nrcpt=1 (queue active)
Jan 13 18:01:16 #myservername# postfix/qmgr[27949]: 922D224A78: from=<the.forrests@typia.fr>, size=724, nrcpt=1 (queue active)
```

Also, here's my mail.cf file :

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


alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = #myservername.domain.com#, localhost.#domain.com#, , localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
mailbox_size_limit = 0
recipient_delimiter = +
virtual_alias_maps = hash:/etc/postfix/virtual
sender_bcc_maps = hash:/etc/postfix/bcc
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
allow_percent_hack = no
myhostname = #myservername.domain.com#
smtpd_sasl_authenticated_header = yes
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination

```

And finally, here's a sample of a spam email header

```
Received    from #mymail.domain# (unknown [122.167.72.244])    (Authenticated sender: yoram)    by #myservername# (Postfix) with ESMTPA id 069C624927    for <acgalsworthy@btopenworld.com>; Wed, 13 Jan 2016 16:44:17 +0100 (CET)
From    "Sam Bayley" <sam.bayley@#mymail.domain#>
Content-Type    text/plain;    charset=us-ascii
Content-Transfer-Encoding    quoted-printable
Mime-Version    1.0 (1.0)
Subject    hi Tony
Message-Id    <D8109673-A0B2-4C84-FA9F-E1668F8BB757@#mymail.domain#>
Date    Wed, 13 Jan 2016 15:44:09 +0000
To    "Tony" <acgalsworthy@btopenworld.com>
X-Mailer    iPhone Mail (9B179)
```

I clearly am a beginner and I don't understand where those emails come from, how they can know my username as it is used in authenticated sender ..

Please help and explain me :)

---

### Post by lisati on 2016-01-13
You seem to have an extra comma in the "mydestination" parameter. Directly or indirectly, this *could* be contributing to the problem.

---

### Post by yoram2 on 2016-01-13
> **lisati said:**
> You seem to have an extra comma in the "mydestination" parameter. Directly or indirectly, this *could* be contributing to the problem.

Ok removed it and restarted postfix, I'm gonna monitor it a while before asking my provider to unban my address.

Could you please explain how spam servers can check my server is a mail server and find my username ?

Many thanks for your help

[edit]
spam mail continue to arrive in my queue

---

### Post by SeijiSensei on 2016-01-13
Spammers run automated programs to find exploitable servers 24/7.

You should run the tests at mxtoolbox.com to see what vulnerabilities you may have.

The message you posted used a forged From: address in your domain.  Unless you're an ISP, allowing random people to send mail as if it is coming from your domain is a really bad idea.  A more interesting question is how this mail is arriving on the server in the first place, since the mynetworks directive only allows mail from the localhost interface.  Are you running a web server on this machine as well? Is it configured to allow people to send mail from a web page?  If so, that's likely the culprit.

---

### Post by yoram2 on 2016-01-13
> **SeijiSensei said:**
> Spammers run automated programs to find exploitable servers 24/7.

You should run the tests at mxtoolbox.com to see what vulnerabilities you may have.

The message you posted used a forged From: address in your domain.  Unless you're an ISP, allowing random people to send mail as if it is coming from your domain is a really bad idea.  A more interesting question is how this mail is arriving on the server in the first place, since the mynetworks directive only allows mail from the localhost interface.  Are you running a web server on this machine as well? Is it configured to allow people to send mail from a web page?  If so, that's likely the culprit.

Hi,
thanks for your answer.
attached is the mxlookup result, which doesn't seem so bad ..


[ATTACH=CONFIG]266727[/ATTACH]

You're right, I have a webserver running also, which runs a website with wordpress up to date.
It also has several subdomains which run many sample websites (wordpress, prestashop, magento, drupal ..)
I just disabled the apache webserver for the main domain and am gonna check it.


How could I precisely track which is the culprit ?
And also, could you develop your remark about the From:address ? how can I change this ?

---

### Post by SeijiSensei on 2016-01-13
> **yoram2 said:**
> Hi,
thanks for your answer.
attached is the mxlookup result, which doesn't seem so bad ..

Except for the fact that your server is blacklisted by a number of major anti-spam services like Barracuda and SORBS!

Is it possible to send email from any of those web services?  If so, can someone specify the From: field in the form?  If the answers to these questions is yes, then that's the likely source of the problem.  

A bigger question is whether you actually need to be running all those services and making them available to the general public.  If you are just testing them out, I'd make sure to limit access to them by IP address using the Restrict directive described here: [https://httpd.apache.org/docs/2.4/howto/access.html](https://httpd.apache.org/docs/2.4/howto/access.html).  Limit access to IP addresses you can control.

Bottom line, don't let anyone use your server for any purpose until you are positive that the services you offer cannot be exploited.

---

### Post by yoram2 on 2016-01-13
> **SeijiSensei said:**
> Except for the fact that your server is blacklisted by a number of major anti-spam services like Barracuda and SORBS!

Is it possible to send email from any of those web services?  If so, can someone specify the From: field in the form?  If the answers to these questions is yes, then that's the likely source of the problem.  

A bigger question is whether you actually need to be running all those services and making them available to the general public.  If you are just testing them out, I'd make sure to limit access to them by IP address using the Restrict directive described here: [https://httpd.apache.org/docs/2.4/howto/access.html](https://httpd.apache.org/docs/2.4/howto/access.html).  Limit access to IP addresses you can control.

Bottom line, don't let anyone use your server for any purpose until you are positive that the services you offer cannot be exploited.

I'm sorry, thanks again for your help but as I told you I'm a total beginner.
My server is only used to host websites.
I didn't intentionnally ran any service.
Wordpress, I guess, is intended to send emails (to inform user, subscriptions).
What I don't get is why do you point me to an apache issue ?

My first problem is that my postfix mail server is accepting send mail from other IP as I get it in this header :

```
[TABLE="class: sub_table_container table-hardcoded, width: 100%"]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]Received[/TD]
[TD="class: col_value, bgcolor: #FFFFFF"]from #mydomain# (ppp-27-55-67-143.revip3.asianet.co.th [27.55.67.143])    (Authenticated sender: yoram)    by #myserver# (Postfix) with ESMTPA id 0A21D249A4    for <champion6@cox.net>; Wed, 13 Jan 2016 21:49:31 +0100 (CET)[/TD]
[/TR]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]From[/TD]
[TD="class: col_value, bgcolor: #FFFFFF"]"bthomson" <bthomson@#mydomain#>[/TD]
[/TR]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]Content-Type[/TD]
[TD="class: col_value, bgcolor: #FFFFFF"]text/plain;    charset=us-ascii[/TD]
[/TR]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]Content-Transfer-Encoding[/TD]
[TD="class: col_value, bgcolor: #FFFFFF"]quoted-printable[/TD]
[/TR]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]Mime-Version[/TD]
[TD="class: col_value, bgcolor: #FFFFFF"]1.0 (1.0)[/TD]
[/TR]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]Subject[/TD]
[TD="class: col_value, bgcolor: #FFFFFF"]hi[/TD]
[/TR]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]Message-Id[/TD]
[TD="class: col_value, bgcolor: #FFFFFF"]<4EC513C2-79D4-4326-DE90-DC5572ECAF17@typia.fr>[/TD]
[/TR]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]Date[/TD]
[TD="class: col_value, bgcolor: #FFFFFF"]Wed, 13 Jan 2016 20:49:44 +0000[/TD]
[/TR]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]To[/TD]
[TD="class: col_value, bgcolor: #FFFFFF"]"champion6" <champion6@cox.net>[/TD]
[/TR]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]X-Mailer[/TD]
[TD="class: col_value, bgcolor: #FFFFFF"]iPhone Mail (12H143)[/TD]
[/TR]
[/TABLE]

```

How can I prevent it ?
when I will have it fixed, I will try make me unblacklisted, but again, my server is not a mail server with proper mailboxes, even my own company mails are managed within google apps.
The only thing I use which is mail related is the php mail() function ..

Here are 2 samples from email properly sent from my websites :

```
[TABLE="class: sub_table_container table-hardcoded, width: 100%"]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]Received[/TD]
[TD="class: col_value, bgcolor: #FFFFFF, colspan: 1"]by #myservername# (Postfix, from userid 1000)	id 78DED24ACA; Wed, 13 Jan 2016 22:57:04 +0100 (CET)[/TD]
[/TR]
[/TABLE]

```

```

[TABLE="class: sub_table_container table-hardcoded, width: 100%"]
[TR]
[TD="class: col_label, bgcolor: #FFFFFF"]Received[/TD]
[TD="class: col_value, bgcolor: #FFFFFF, colspan: 1"]by #myservername# (Postfix, from userid 1016)	id BDF92249AA; Wed, 13 Jan 2016 22:53:53 +0100 (CET)[/TD]
[/TR]
[/TABLE]

```

Many thanks

[edit] I completely disabled websites (every functions including apache, DNS, and mysql) for that domain and all its subdomains and queue is still growing so I think it's completely postfix related.

---

### Post by CharlesA on 2016-01-13
Please do not set postfix to listen on 0.0.0.0 if all you are using it for is sending mail from a contact form.

Set it to listen on 127.0.0.1 and you won't have to deal with this. Assuming the spam is from people connecting thru the postfix server itself rather than a problem with the contact form.

You need to set modify main.cf and set
```
inet_interfaces = all
```
to:
```
inet_interfaces = 127.0.0.1
```

Then restart postfix and verify it is only listening on 127.0.0.1.

---

### Post by yoram2 on 2016-01-13
> **CharlesA said:**
> Please do not set postfix to listen on 0.0.0.0 if all you are using it for is sending mail from a contact form.

Set it to listen on 127.0.0.1 and you won't have to deal with this. Assuming the spam is from people connecting thru the postfix server itself rather than a problem with the contact form.

You need to set modify main.cf and set
```
inet_interfaces = all
```
to:
```
inet_interfaces = 127.0.0.1
```

Then restart postfix and verify it is only listening on 127.0.0.1.

Hi,
are you talking the postfix main.cf file ? I don't have an inet_interfaces line, should I add it ?

The thing I don't get is that this server worked great for about 2 years until last week.
The only thing I changed, apart from usual apt-get upgrades was updating virtualmin ..

[edit] Seems like the change did it ... I'm gonna monitor it a little more to check ..

Many thanks !!

---

### Post by CharlesA on 2016-01-13
Sometimes it isn't there, and you have to add it. Hopefully you find the source of the spam and get your IP removed from the blacklists. Good luck!

---

### Post by yoram2 on 2016-01-14
> **CharlesA said:**
> Sometimes it isn't there, and you have to add it. Hopefully you find the source of the spam and get your IP removed from the blacklists. Good luck!

Hi, as stated in my last post.
It seems to have solved the issue.
But I'm trying to understand what's the source.
I disabled all websites related to that domain so it seems that the source is external.

By the way, I guess that this configuration is also preventing me to use my server as a mail server for my other domains ?

Is there any way to find the real source and tune it ?

Many thanks

---

### Post by CharlesA on 2016-01-14
> **yoram2 said:**
> Hi, as stated in my last post.
It seems to have solved the issue.
But I'm trying to understand what's the source.
I disabled all websites related to that domain so it seems that the source is external.

By the way, I guess that this configuration is also preventing me to use my server as a mail server for my other domains ?

Is there any way to find the real source and tune it ?

Many thanks

That configuration will only allow access to the server from the local machine. No external connections will be accepted because it is not listening on the external IP address.

You would have to look at the logs for postfix to see what is wrong.

---

