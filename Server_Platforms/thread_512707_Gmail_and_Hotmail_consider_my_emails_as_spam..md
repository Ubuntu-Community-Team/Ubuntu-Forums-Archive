---
title: "Gmail and Hotmail consider my emails as spam."
date: 2007-07-29
forum: Server Platforms
---

### Post by zephid on 2007-07-29
For some reason Gmail and Hotmail flags every e-mail I send from my postfix server as spam, which they are not.

The headers from Gmail says the server passed the SPF test, so from I know it should be fine, but they still see it as spam, anyone got some suggestions to fix this? I have searched google and found out it was not my PHP script that was the problem, but Postfix.

I have checked my IP address against every known spam list, and it's not listed any where.
And it's static, so it's not because of the dynamic ip thing.

Headers from Gmail:
```
Delivered-To: removed@gmail.com
Received: by 10.114.120.19 with SMTP id s19cs207019wac;
        Sun, 29 Jul 2007 12:59:23 -0700 (PDT)
Received: by 10.66.232.9 with SMTP id e9mr4667607ugh.1185739163258;
        Sun, 29 Jul 2007 12:59:23 -0700 (PDT)
Return-Path: <removed@oldstudents.dk>
Received: from xencon.zephid.dk (gotweb.dk [83.246.72.102])
        by mx.google.com with ESMTP id 32si1981081ugf.2007.07.29.12.59.22;
        Sun, 29 Jul 2007 12:59:23 -0700 (PDT)
Received-SPF: pass (google.com: domain of removed@oldstudents.dk designates 83.246.72.102 as permitted sender)
Received: by xencon.zephid.dk (Postfix, from userid 10004)
	id 51C0286E2; Sun, 29 Jul 2007 21:59:22 +0200 (CEST)
To: removed@gmail.com
Subject: Invitation til Old|Students
Date: Sun, 29 Jul 2007 21:59:22 +0200
From: Old|Students Robot <noreply@oldstudents.dk>
Message-ID: <b9e205fd7ae037ccbc77ad13bdd6f1c7@oldstudents.dk>
X-Priority: 3
X-Mailer: PHPMailer [version 1.73]
MIME-Version: 1.0
Content-Transfer-Encoding: 8bit
Content-Type: text/plain; charset="utf-8"

Mads Vestergaard Madsen har inviteret dig til Old|Students, for at du kan holde dig opdateret med hvad der sker i din studenterklasse efter du er gået ud.
Klasse: h04a årgang 2007. Skole: Skive Handelsskole
Din personlige adgangskode: 8ibt4vem

For at komme igang skal du gå ind på http://oldstudents.dk og logge ind med din e-mail adresse og den adgangskode du har fået tildelt.

Hvis du ikke ønsker at være en del af din klasses sammenhold skal du blot ignore denne mail, og din konto vil blive slettet efter 21 dage.
--
Dette er en automatiseret e-mail du har ikke mulighed for at besvare den.
```

Postfix main.cf:
```
#########################
#/etc/postfix/main.cf:
command_directory = /usr/sbin
daemon_directory = /usr/lib/postfix
program_directory = /usr/lib/postfix
queue_directory = /var/spool/postfix

transport_maps = mysql:/etc/postfix/mysql_transport.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uids.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gids.cf

virtual_mailbox_base = /var/spool/postfix/virtual/

virtual_maps = mysql:/etc/postfix/mysql_virtual.cf
virtual_mailbox_limit = 102400000
virtual_minimum_uid = 1000

inet_interfaces = all
home_mailbox = Maildir/

myhostname = xencon.zephid.dk
mydestination = $transport_maps

relay_domains = $mydestination, $virtual_maps

mynetworks = 127.0.0.0/8, 83.246.72.102

mynetworks_style = $myhostname

smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous

unknown_local_recipient_reject_code = 550
smtpd_sasl_local_domain = $myhostname

smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unknown_sender_domain, reject_unauth_pipelining, reject_unknown_recipient_domain, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_non_fqdn_hostname, reject_unauth_destination, reject_rbl_client cbl.abuseat.org, reject_rbl_client dynablock.njabl.org, reject_rbl_client list.dsbl.org, reject_rbl_client dnsbl.njabl.org, reject_rbl_client sbl-xbl.spamhaus.org

smtpd_helo_required = yes

broken_sasl_auth_clients = yes

content_filter=smtp-amavis:[127.0.0.1]:10024
```

---

### Post by jtc on 2007-07-29
This part of the header doesn't look very good.

> Received: from xencon.zephid.dk (gotweb.dk [83.246.72.102])

Some mailservers get suspicious when your HELO doesn't match the PTR-record of your ip-address. Still, I don't think it is considered that bad, so perhaps it is in combination with some other factors.

---

### Post by zephid on 2007-07-29
> **jtc said:**
> This part of the header doesn't look very good.



Some mailservers get suspicious when your HELO doesn't match the PTR-record of your ip-address. Still, I don't think it is considered that bad, so perhaps it is in combination with some other factors.

I have tried to change the it to gotweb.dk, still same result, flaged as spam :(

---

### Post by leftcase on 2007-07-30
I see you're hosting with [www.server-service.de/](www.server-service.de/)

The only thing I can think of is that somehow, somewhere, the IP address is blacklisted ? 

edit: But checking here shows you in the clear [http://www.robtex.com/rbl/83.246.72.102.html](http://www.robtex.com/rbl/83.246.72.102.html)

Chris

---

### Post by zephid on 2007-07-30
The problem has been solved. I found out that Gmail and Hotmail uses Sender-ID and DKIM to verify emails, I setup DKIM on Postfix and Sender-ID in my TXT record on my domain, and now it works as planned.

---

### Post by esaym on 2007-10-05
> **zephid said:**
> The problem has been solved. I found out that Gmail and Hotmail uses Sender-ID and DKIM to verify emails, I setup DKIM on Postfix and Sender-ID in my TXT record on my domain, and now it works as planned.

Can you give us some details on how you did this? :)

---

### Post by zephid on 2007-10-06
in general all you need to know is on [http://openspf.org](http://openspf.org)

---

