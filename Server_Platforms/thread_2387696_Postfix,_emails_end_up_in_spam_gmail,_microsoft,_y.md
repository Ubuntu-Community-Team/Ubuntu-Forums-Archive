---
title: "Postfix, emails end up in spam gmail, microsoft, yahoo ..."
date: 2018-03-22
forum: Server Platforms
---

### Post by danny942 on 2018-03-22
Hi, for a good while (more then a month) im trying to get my vps machine(Ubuntu 16.04) ready for postfix to sent mails. Im using Plesk on it. 
But no matter how i configure my postfix my mails never wont get through spamfilter on several providers. 

So i provided a lot of stuff, trying to send a mail from my mail "xxxx@domain.tdl" to my gmail mail:

Mail log vom Server:

```
Mar 21 102911 vps postfixsmtpd[29657] connect from [host1-xx-static.xx-xx.business.telecomitalia.it]("http://host1-xx-static.xx-xx.business.telecomitalia.it/")[xx.xx.xx.x]
Mar 21 102911 vps postfixsmtpd[29657] 823BB8604C3 client=[host1-xx-static.xx-xx.business.telecomitalia.it]("http://host1-xx-static.xx-xx.business.telecomitalia.it/")[xx.xx.xx.x], sasl_method=PLAIN, sasl_username=xxxx...@xxxxh.it
Mar 21 102911 vps greylisting filter[29663] Starting greylisting filter...
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] _mh_fork() unrecognized status code '5'
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] Error during 'grey' handler
Mar 21 102911 vps postfixcleanup[29662] 823BB8604C3 message-id=4553b78d-f57a-99db-48ab-cfa036ff20f4@example.com
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] handlers_stderr PASS
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] PASS during call 'limit-out' handler
Mar 21 102911 vps check-quota[29665] Starting the check-quota filter...
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] handlers_stderr SKIP
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] SKIP during call 'check-quota' handler
Mar 21 102911 vps spf[29667] Starting the spf filter...
Mar 21 102911 vps spf[29667] SPF status PASS
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] handlers_stderr PASS
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] PASS during call 'spf' handler
Mar 21 102911 vps drweb[29668] Starting the drweb filter...
Mar 21 102911 vps qmail-queue[29668] dwlib fd connect() failed - Connection refused
Mar 21 102911 vps qmail-queue[29668] dwlib tcp connecting to 127.0.0.13000 - failed
Mar 21 102911 vps qmail-queue[29668] dwlib cannot create connection with a DrWeb daemon
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] handlers_stderr SKIP
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] SKIP during call 'drweb' handler
Mar 21 102911 vps dk_sign[29669] Starting the dk_sign filter...
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] handlers_stderr PASS
Mar 21 102911 vps usrlibplesk-9.0psa-pc-remote[13591] PASS during call 'dd51-domainkeys' handler
Mar 21 102911 vps postfixqmgr[29243] 823BB8604C3 from=in...@example.com, size=706, nrcpt=1 (queue active)
Mar 21 102911 vps postfixsmtpd[29657] disconnect from [host1-xx-static.xx-xx.business.telecomitalia.it]("http://host1-xx-static.xx-xx.business.telecomitalia.it/")[xx.xx.xx.x] ehlo=2 starttls=1 auth=1 mail=1 rcpt=1 data=1 quit=1 commands=8
Mar 21 102912 vps postfixsmtp[29670] 823BB8604C3 to=testpo...@gmail.com, relay=[gmail-smtp-in.l.google.com]("http://gmail-smtp-in.l.google.com/")[66.102.1.27]25, delay=1, delays=0.310.010.140.57, dsn=2.0.0, status=sent (250 2.0.0 OK 1521624552 y21si2895522wra.1 - gsmtp)
Mar 21 102912 vps postfixqmgr[29243] 823BB8604C3 removed

```


Bounce mail:
```
Delivered-To: testpo...@gmail.com
Received: by 2002:a9d:61d9:0:0:0:0:0 with SMTP id h25-v6csp2270266otk;
        Wed, 21 Mar 2018 02:29:12 -0700 (PDT)
X-Google-Smtp-Source: AG47ELs1aP431K+OMW1UX3y+x/qCCV9QJLCQ2yUBqauM+rI1lvrGrNHXTMsIPSS9ha8/CpDdB0pO
X-Received: by 10.223.166.171 with SMTP id t40mr16649691wrc.49.1521624552502;
        Wed, 21 Mar 2018 02:29:12 -0700 (PDT)
ARC-Seal: i=1; a=rsa-sha256; t=1521624552; cv=none;
        d=[google.com]("http://google.com/"); s=arc-20160816;
        b=bp8oV0Pah3L5E66B+msgfyGG/j6tHIK1/BPPtFJwTT/Iv5MsaDniUaJr+H+knMU5ij
         rydq2JnSqaEfTUYCH3YVkH6zUaFGJ9MdzSMV6AhPlUKe8k3dulMc17Kmt0AZS1TWSTCv
         GU0vCh2wJXMNmnYbm24mdNtLxtsYKmkAE3tRf21LbN4zXxUrrPfORGLU8CvQBNaKWnkL
         rytisCdl1EXvebGe2vhFrsQNmKHy1+y7rcwYextmlW58BETaxi4KiHrwSso5vdDHe1L4
         utEEg0qvK+oOwkYHwApbWNpFrHgoF1pMSlgst5oZmQLgeG03oFcx5N5LalBvQPlGiRkB
         dF6Q==
ARC-Message-Signature: i=1; a=rsa-sha256; c=relaxed/relaxed; d=[google.com]("http://google.com/"); s=arc-20160816;
        h=content-transfer-encoding:mime-version:user-agent:date:message-id
         :subject:from:to:dkim-signature:arc-authentication-results;
        bh=2u0Su+wTCVEUvQJ8p1VdjaKqUszbF5AFs2kKKcveqc8=;
        b=YT4FZnDNij/83iASCnItxluYZub9hhtjI9okV37FPy9mL5Pc0hihyqIi7FFzuQ7cGq
         /zlBLeEXltZg6FxRP2B3CEhmnvGIh4lDyJIgPOI0HbFM/xlT4Y5F2lLv72l+y+S40dAh
         VSuIaLKjO+rSwXfFHXSJEoHtJ3vGejD0I5ImD/6Y3zoco6T9q3Y3jLUclbB6THzCGmU+
         42qmQ7P1DNy6mm7luYoHCWdu+D+BcMP8269iEnd28OXrV50Gw3ACLpk1A7kuIaRAOvqu
         +uUzcrG9qgcmdaAEyp+MQD2pLNHDamrMa9Gvsgq6KxmfGi68KigsHbYLipwAPK22QYZh
         jFdw==
ARC-Authentication-Results: i=1; [mx.google.com]("http://mx.google.com/");
       dkim=pass header.i=@[example.com]("http://example.com/") header.s=default header.b=pfReBhFr;
       spf=pass ([google.com]("http://google.com/"): domain of in...@example.com designates SERVERIP as permitted sender) smtp.mailfrom=in...@example.com;
       dmarc=pass (p=NONE sp=NONE dis=NONE) header.from=[example.com]("http://example.com/")
Return-Path: <in...@example.com>
Received: from [vps.example.it]("http://vps.example.it/") ([vps.example.it]("http://vps.example.it/"). [SERVERIP])
        by [mx.google.com]("http://mx.google.com/") with ESMTPS id y21si2895522wra.1.2018.03.21.02.29.11
        for <testpo...@gmail.com>
        (version=TLS1_2 cipher=ECDHE-RSA-AES128-GCM-SHA256 bits=128/128);
        Wed, 21 Mar 2018 02:29:12 -0700 (PDT)
Received-SPF: pass ([google.com]("http://google.com/"): domain of in...@example.com designates SERVERIP as permitted sender) client-ip=SERVERIP;
Authentication-Results: [mx.google.com]("http://mx.google.com/");
       dkim=pass header.i=@[example.com]("http://example.com/") header.s=default header.b=pfReBhFr;
       spf=pass ([google.com]("http://google.com/"): domain of in...@example.com designates SERVERIP as permitted sender) smtp.mailfrom=in...@example.com;
       dmarc=pass (p=NONE sp=NONE dis=NONE) header.from=[example.com]("http://example.com/")
Received: from [192.168.1.31] ([host1-xx-static.xx-xx-b.business.telecomitalia.it]("http://host1-xx-static.xx-xx-b.business.telecomitalia.it/") [xx.xx.xx.x])
    by [vps.example.it]("http://vps.example.it/") (Postfix) with ESMTPSA id 823BB8604C3
    for <testpo...@gmail.com>; Wed, 21 Mar 2018 10:29:11 +0100 (CET)
DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed; d=[example.com]("http://example.com/");
    s=default; t=1521624551;
    bh=2u0Su+wTCVEUvQJ8p1VdjaKqUszbF5AFs2kKKcveqc8=; l=59;
    h=To:From:Subject;
    b=pfReBhFr45Exgs3M4n3tYLnTYz7SxmeEzp4c2k4LJ8801KSSJMxXycEDMmj3qJJof
     gVCgeeZvVu0WGGRdbCuMJJ69CTTl5gEMe1GW0iheHSkip0xEzbxPzd+TVwYz2Zm+QR
     rB8incNh1ng/bMmFbPPpbgN6KJM2mkPZxplQs4zc=
Authentication-Results: vps;
        spf=pass (sender IP is xx.xx.xx.x) smtp.mailfrom=in...@example.com smtp.helo=[192.168.1.31]
Received-SPF: pass (vps: connection is authenticated)
To: testpo...@gmail.com
From: Info SITENAME <in...@example.com>
Subject: Registration complete
Message-ID: <4553b78d-f57a-99db-48ab-cfa036ff20f4@example.com>
Date: Wed, 21 Mar 2018 10:29:10 +0100
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:52.0) Gecko/20100101
 Thunderbird/52.6.0
MIME-Version: 1.0
Content-Type: text/plain; charset=utf-8; format=flowed
Content-Transfer-Encoding: 7bit
X-PPP-Message-ID: <152162455170.29664.18368554563019337391@vps.example.it>
X-PPP-Vhost: [example.it]("http://example.it/")
Hi thanks for your registration on our site...

```

postfix/main.cf

```
smtpd_banner = $myhostname ESMTP


biff = no


append_dot_mydomain = no


readme_directory = no


# TLS parameters
smtpd_tls_cert_file = /etc/postfix/postfix.pem
smtpd_tls_key_file = $smtpd_tls_cert_file
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache




smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = vps.example.it
alias_maps = hash:/etc/aliases, hash:/var/spool/postfix/plesk/aliases
alias_database = hash:/etc/aliases
myorigin = localhost
mydestination = localhost.example.it, localhost, localhost.localdomain
relayhost = 
mynetworks = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
virtual_mailbox_domains = $virtual_mailbox_maps, hash:/var/spool/postfix/plesk/virtual_domains
virtual_alias_maps = $virtual_maps, hash:/var/spool/postfix/plesk/virtual
virtual_mailbox_maps = , hash:/var/spool/postfix/plesk/vmailbox
#virtual_alias_domains = hash:/etc/postfix/domains
transport_maps = , hash:/var/spool/postfix/plesk/transport
smtpd_tls_security_level = may
smtp_tls_security_level = may
smtp_use_tls = no
smtpd_timeout = 3600s
smtpd_proxy_timeout = 3600s
disable_vrfy_command = yes
smtpd_sender_restrictions = check_sender_access hash:/var/spool/postfix/plesk/blacklists, permit_sasl_authenticated
smtpd_client_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_rbl_client zen.spamhaus.org, reject_rbl_client bl.spamcop.net, reject_rbl_client b.barracudacentral.org
smtp_send_xforward_command = yes
smtpd_authorized_xforward_hosts = 127.0.0.0/8 [::1]/128
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
virtual_mailbox_base = /var/qmail/mailnames
virtual_uid_maps = static:30
virtual_gid_maps = static:31
smtpd_milters = , inet:127.0.0.1:12768 inet:127.0.0.1:12345
sender_dependent_default_transport_maps = hash:/var/spool/postfix/plesk/sdd_transport_maps
virtual_transport = plesk_virtual
plesk_virtual_destination_recipient_limit = 1
mailman_destination_recipient_limit = 1
virtual_mailbox_limit = 0
smtpd_tls_ciphers = medium
smtpd_tls_mandatory_ciphers = medium
tls_medium_cipherlist = HIGH:!aNULL:!MD5
smtpd_tls_mandatory_protocols = TLSv1 TLSv1.1 TLSv1.2
smtpd_tls_protocols = TLSv1 TLSv1.1 TLSv1.2
milter_connect_macros = j {daemon_name} {client_connections} {client_addr} {client_ptr} v
milter_default_action = accept
message_size_limit = 10240000

```
In my master.cf i changed the HELO to the server hostname vps.example.it.

I have more domains in my Plesk panel. I have one domain where i created a subdomain "vps.example.it" this is my server hostname and this im using for the delivery of mails (Reverse PTR is set to this). The mx entry "mail.domain.tld", i did not used in main.cf or for ingoing (for them i only have created a subdomain wich i have secured with a lets encrypt certificat). 

Maybe i should change the mx for my domains into vps.example.it like outgoing ?

Im using TLS/SSL for ingoing und outgoing. The mail server is secured with the "vps.example.it" certificat. 

In attachment you can find also a mail-tester.com result with 10/10, dns configuration, plesk email settings.
Im not listet in any Blacklist, checked a lot of tools and checked domain health, smtp diagnostics with mxtoolbox.com and checked dns stuff ... im passing everywhere.

I listet my domains hostname there:
[https://postmaster.google.com/](https://postmaster.google.com/)

I joint the jmrp and snds program on microsoft.
I asked shortly for delistning there:
[https://support.microsoft.com/en-us/getsupport?oaspworkflow=start_1.0.0.0&wfname=capsub&productkey=edfsmsbl3&forceorigin=esmc&ccsid=636573282753654996](https://support.microsoft.com/en-us/getsupport?oaspworkflow=start_1.0.0.0&wfname=capsub&productkey=edfsmsbl3&forceorigin=esmc&ccsid=636573282753654996)
[https://io.help.yahoo.com/contact/index?y=PROD_POST&page=contactform&locale=en_US&token=Zh/BBVqXzLHlIbokbUqVWTUbuuQeXGkGnZzhKR2JQ4O6mMQdy9JSWdtWFXvjthcYCRj9bUIFfycOfG+4GOHPHoOGa8HwDO2+0kYRtTcdR8NsLD0dGURpc1B0MBKcI2o/o/mRH4O42kz3lgqmGuc8ri0k6+CMt1UY&selectedChannel=email-icon&yid=](https://io.help.yahoo.com/contact/index?y=PROD_POST&page=contactform&locale=en_US&token=Zh/BBVqXzLHlIbokbUqVWTUbuuQeXGkGnZzhKR2JQ4O6mMQdy9JSWdtWFXvjthcYCRj9bUIFfycOfG+4GOHPHoOGa8HwDO2+0kYRtTcdR8NsLD0dGURpc1B0MBKcI2o/o/mRH4O42kz3lgqmGuc8ri0k6+CMt1UY&selectedChannel=email-icon&yid=)
[https://support.google.com/mail/contact/msgdelivery](https://support.google.com/mail/contact/msgdelivery)

From microsoft support i recieved:
We have completed reviewing the IP(s) you submitted. The following table contains the results of our investigation. 
Not qualified for mitigation
173.xxx.xxx.xxx
Our investigation has determined that the above IP(s) do not qualify for mitigation.


with some tips.


From Yahoo i get some standard mail with tips similar to Microsoft.

...

I really don't know how to fix this problem :(.

---

### Post by lisati on 2018-03-22
Do you have a "proper" [rDNS]("https://en.wikipedia.org/wiki/Reverse_DNS_lookup") (reverse DNS) set up for the public IP address that your server uses? Some spam filters object if there is a generic rDNS or one which does not match the email domain name.

---

### Post by danny942 on 2018-03-23
Hi lisati,
thanks for your answer.
Yes i have an rDNS (PTR i have written above) , see attachment.:

It's the same like "myhostname" in the main.cf configuration vps.example.it. 
[COLOR=#000000][FONT=&amp]In case of my second domain its not the same domain name. I can set up only one rDNS.

Like that it's my serverhostname vps.example.it.  (example.it is my first domain i bought)

If my second domain is named "domain.it"
The rDNS is still "vps.example.it"

Only the ingoing "mailserver" MX has the correct name "mail.INSERTDOMAIN.TLD" but like said before, i did not add those in any way in my settings. It's just named different because i heard they should be, else i had used the same like outgoing (in my email program i even use the same for ingoing "vps.example.it").



I have a single Ip Adress only. This is used for server, ingoing mails and outgoing. So it would doesnt make sense to add a subdomain with imap and one with smtp if all reverse to the same IP and like said before i can set only one reverse.



I got the answer from Yahoo now too.... Always the same answers from those providers:
[/FONT][/COLOR]"While we can't guarantee consistent Inbox delivery for your mail, the following best practices should help prevent delivery issues:"


Edit:
Well i changed the mx again into vps.example.it, everyhing is pointing now to the serverhostname... (i tried this setting already ~ 100 times.)
... still spam.

---

### Post by volkswagner on 2018-03-23
It's a little difficult for me to understand your sanitized log.

You shouldn't be authenticating with outside mail servers using a local LAN address.

```
  spf=pass (sender IP is xx.xx.xx.x) smtp.mailfrom=in...@example.com smtp.helo=[192.168.1.31]
```


Are you sure you have a static ip address on your VPS?
Finding out why your ip doesn't qualify for mitigation may be a good start:
```
From Microsoft support i received:
We have completed reviewing the IP(s) you submitted. The following table contains the results of our investigation. 
Not qualified for mitigation
173.xxx.xxx.xxx
Our investigation has determined that the above IP(s) do not qualify for mitigation.
```

---

### Post by danny942 on 2018-03-23
Hi.

> **volkswagner said:**
> 
It's a little difficult for me to understand your sanitized log.
You shouldn't be authenticating with outside mail servers using a local LAN address.


I can send you all logs over pm if you like. I won't puplish ips etc because of security reasons.
I has sent the mail over thunderbird where (imap vps.example.it ssl/tls 933 and smtp vps.example.it ssl/tls 465).


> **volkswagner said:**
> 
Are you sure you have a static ip address on your VPS?
Finding out why your ip doesn't qualify for mitigation may be a good start:

Yes i have a static ip, dedicated on my server.

Yeah it's hard to find out if mail providers won't tell me whats the problem :(.

EDIT:
master.cf (ip config):
added this behind "smtp_helo_name" (has the same value):
 ```
-o myhostname=vps.example.it
```

I added some lines in main.cf:
```
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtpd_sasl_security_options = noanonymous
smtpd_sasl_tls_security_options = noanonymoussmtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
```

And im trying to implement this (but got smtp errors)

```
localhost:smtps   inet n - - - - smtpd    -o smtpd_tls_wrappermode=yes
    -o smtpd_sasl_auth_enable=yes
    -o smtpd_client_restrictions=permit_sasl_authenticated,reject
    -o smtpd_sender_restrictions=check_sender_access hash:/var/spool/postfix/plesk/blacklists, permit_sasl_authenticated, check_client_access pcre:/var/spool/postfix/plesk/non_auth.re
    -o smtpd_tls_key_file=/path/to/your/certificate/private-key/for/host.YOUR-HOST-DOMAIN.ir
    -o smtpd_tls_cert_file=/path/to/your/certificate/cert-file/for/host.YOUR-HOST-DOMAIN.ir
    -o smtp_helo_name=YOUR-HOST-DOMAIN.ir
    -o myhostname=host.YOUR-HOST-DOMAIN.ir
   
85.XXX.XXX.XXX:smtps   inet n - - - - smtpd 
    -o smtpd_tls_wrappermode=yes
    -o smtpd_sasl_auth_enable=yes
    -o smtpd_client_restrictions=permit_sasl_authenticated,reject
    -o smtpd_sender_restrictions=check_sender_access hash:/var/spool/postfix/plesk/blacklists, permit_sasl_authenticated, check_client_access pcre:/var/spool/postfix/plesk/non_auth.re
    -o smtpd_tls_key_file=/path/to/your/certificate/private-key/for/mail.YOUR-DOMAIN.net
    -o smtpd_tls_cert_file=/path/to/your/certificate/cert-file/for/mail.YOUR-DOMAIN.net
    -o smtp_helo_name=YOUR-DOMAIN.net
    -o myhostname=mail.YOUR-DOMAIN.net
```

found here [https://talk.plesk.com/threads/problem-with-fake-email-address.338150/](https://talk.plesk.com/threads/problem-with-fake-email-address.338150/) #11

yeah im frustrated... and trying for more weeks things i dont understand.

---

### Post by SeijiSensei on 2018-03-23
Run the tests at mxtoolbox.com and see what it reports.  Is your IP on a blacklist?  It's possible someone else had your IP address before you and sent spam.  I had to remove myself from a couple of lists because of that problem with a Linode server I have.

---

### Post by lisati on 2018-03-23
There are several sites I'm aware of which can check if your IP address is blacklisted somewhere. The [multirbl.valli.org]("http://multirbl.valli.org/") site not only checks blacklists, but checks rDNS as well.

---

### Post by SeijiSensei on 2018-03-23
mxtoolbox has a wide range of tools including checks for open relays, rDNS, and the like

[https://mxtoolbox.com/SuperTool.aspx?action=smtp%3agmail-smtp-in.l.google.com&run=toolpage](https://mxtoolbox.com/SuperTool.aspx?action=smtp%3agmail-smtp-in.l.google.com&run=toolpage)

along with blacklists

[https://mxtoolbox.com/SuperTool.aspx?action=blacklist%3agmail-smtp-in.l.google.com&run=toolpage](https://mxtoolbox.com/SuperTool.aspx?action=blacklist%3agmail-smtp-in.l.google.com&run=toolpage)

---

### Post by SeijiSensei on 2018-03-23
mxtoolbox has a wide range of tools including checks for open relays, rDNS, and the like

[https://mxtoolbox.com/SuperTool.aspx?action=smtp%3agmail-smtp-in.l.google.com&run=toolpage](https://mxtoolbox.com/SuperTool.aspx?action=smtp%3agmail-smtp-in.l.google.com&run=toolpage)

along with blacklists

[https://mxtoolbox.com/SuperTool.aspx?action=blacklist%3agmail-smtp-in.l.google.com&run=toolpage](https://mxtoolbox.com/SuperTool.aspx?action=blacklist%3agmail-smtp-in.l.google.com&run=toolpage)

That blacklist search site lisati cites has what looks to be a [more extensive]("http://multirbl.valli.org/lookup/gmail-smtp-in.l.google.com.html") report than mxtoolbox.

---

### Post by danny942 on 2018-03-25
Sorry for late answer, i didn't recieved any notifications on a answer. Im **really** thankful for your help, so many days without any success on my try hards.

> **lisati said:**
> There are several sites I'm aware of which can check if your IP address is blacklisted somewhere. The [multirbl.valli.org]("http://multirbl.valli.org/") site not only checks blacklists, but checks rDNS as well.

Aha on your linked site i finally got some error:
[COLOR=#000000][FONT=Arial]DNSBL Informationallist Test
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]542 domain.it [/FONT][/COLOR]abuse.net
[TABLE="width: 1722"]
[TR]
[TD="class: listed_info_label, bgcolor: #999999"]Failure:[/TD]
[TD="class: listed_info_data, bgcolor: #AAAAAA, colspan: 3"]DNS request failed: The name server was unable to process this query due to a problem with the name server.[/TD]
[/TR]
[/TABLE]

Everything else is ok like in all other tools i have checked.
But what is meaned by there ?
I have implented a alias map for abuse mail. And my [EMAIL="abuse@domain1.tdl"]abuse@domain1.tdl[/EMAIL] and [EMAIL="abuse@domain2.tdl"]abuse@domain2.tdl[/EMAIL] is reachable withouth problems.

> **SeijiSensei said:**
> mxtoolbox has a wide range of tools including checks for open relays, rDNS, and the like


Thanks for your input, mxtools like said in first post i have already checked and passed each test successfull and im not listed in any blacklist anymore.

EDIT 26/03:
I checked this error about abuse, so it looks like that all mailservers dont pass this test. So i dont think this will cause all of my emails to end up in spam.

Any other suggestions please ?

---

### Post by danny942 on 2018-03-26
EDIT from previous post today:
[COLOR=#000000]I checked this error about abuse, so it looks like that all mailservers dont pass this test. So i dont think this will cause all of my emails to end up in spam.[/COLOR]

[COLOR=#000000]Any other suggestions please ?
[/COLOR]EDIT END

I provided some header comparison (attachment) from sending mail:
left:   yahoo.com -> gmail.com
right: mail from domain2222 -> gmail.com

and have highlighted all different values.

**This is my current main.cf:**
```
smtpd_banner = $myhostname ESMTP


biff = no
append_dot_mydomain = no
readme_directory = no


# TLS parameters
smtpd_tls_cert_file = /etc/postfix/postfix.pem
smtpd_tls_key_file = $smtpd_tls_cert_file
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache




smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = FQDN-SERVER-HOSTNAME
alias_maps = hash:/etc/aliases, hash:/var/spool/postfix/plesk/aliases
alias_database = hash:/etc/aliases
myorigin = localhost
mydestination = localhost
relayhost = 
mynetworks = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
virtual_mailbox_domains = $virtual_mailbox_maps, hash:/var/spool/postfix/plesk/virtual_domains
virtual_alias_maps = $virtual_maps, hash:/var/spool/postfix/plesk/virtual
virtual_mailbox_maps = , hash:/var/spool/postfix/plesk/vmailbox
transport_maps = , hash:/var/spool/postfix/plesk/transport
smtpd_tls_security_level = may
smtp_tls_security_level = may
smtp_use_tls = no
smtpd_timeout = 3600s
smtpd_proxy_timeout = 3600s
disable_vrfy_command = yes
smtpd_sender_restrictions = check_sender_access hash:/var/spool/postfix/plesk/blacklists, permit_sasl_authenticated
smtpd_client_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_rbl_client zen.spamhaus.org, reject_rbl_client bl.spamcop.net, reject_rbl_client b.barracudacentral.org
smtp_send_xforward_command = yes
smtpd_authorized_xforward_hosts = 127.0.0.0/8 [::1]/128
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
virtual_mailbox_base = /var/qmail/mailnames
virtual_uid_maps = static:30
virtual_gid_maps = static:31
smtpd_milters = , inet:127.0.0.1:12768 inet:127.0.0.1:12345
sender_dependent_default_transport_maps = hash:/var/spool/postfix/plesk/sdd_transport_maps
virtual_transport = plesk_virtual
plesk_virtual_destination_recipient_limit = 1
mailman_destination_recipient_limit = 1
virtual_mailbox_limit = 0
smtpd_tls_ciphers = medium
smtpd_tls_mandatory_ciphers = medium
tls_medium_cipherlist = HIGH:!aNULL:!MD5
smtpd_tls_mandatory_protocols = TLSv1 TLSv1.1 TLSv1.2
smtpd_tls_protocols = TLSv1 TLSv1.1 TLSv1.2
milter_connect_macros = j {daemon_name} {client_connections} {client_addr} {client_ptr} v
milter_default_action = accept
message_size_limit = 10240000
```


**/etc/aliases:**
Everything is removed there. 

somehow /var/spool/postfix/plesk/virtual_domains and /var/spool/postfix/plesk/virtual is empty now, else i had there my alias map for
**virtual:**
postmaster@domain1111 FORWARDMAIL
 abuse@domain1111  FORWARDMAIL
 
postmaster@domain2222 FORWARDMAIL
abuse@domain2222 FORWARDMAIL
... 
and 
**virtual domains**:
```
DOMAIN11111 #
DOMAIN22222 #
```



Maybe i have to make my own file, so atm localhost for myorigin and mydestination would be wrong. 
Edit: i made my own file now but for the header comparison nothing changed.

**/etc/hosts:**
```
127.0.0.1    localhost.localdomain localhost    
127.0.1.1    FQDN-SERVER-HOSTNAME HOSTNAME    


# The following lines are desirable for IPv6 capable hosts
::1    localhost.localdomain localhost ip6-localhost ip6-loopback    
ff02::1    ip6-allnodes    
ff02::2    ip6-allrouters    
SERVERDOMAIN    FQDN-SERVER-HOSTNAME HOSTNAME
```

Hint: watch from right to left.

---

### Post by danny942 on 2018-03-28
No one can help me :( ?

---

