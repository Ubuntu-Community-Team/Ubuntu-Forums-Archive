---
title: "OpenVAS Emailing Using Postfix"
date: 2017-02-08
forum: Server Platforms
---

### Post by hammons2012 on 2017-02-08
So, I'm going to get right to the point, because I am going a bit crazy on this one trying out all of these different "fixes". So, the scenarios is this:

-I have a mail server that runs Exchange (mail.workdomain.com).
-I have Ubuntu 16.04 server that is running OpenVAS.
-I want to setup emailing of reports for OpenVAS, and I have installed Postfix to do just this (although I want it to send emails to my Exchange server/work email).
-I have successfully gotten the emails to send to the local user account (let's call him/her user1@localhost).
-I have created an alias to forward the emails to an external email address (hammons@personalemail.com - which works, but keeps showing in my junk folder.....but I digress).
-I want these emails to go to my work email (let's call this [email]hammons@workdomain.com[/email]).

I have no idea what else I can try to get this to work. Obviously, the emails are working (I have to set OpenVAS to send the emails to user1@localhost - which then forwards to [email]hammons@personalemail.com[/email]). Posted below is the content of /etc/postfix/main.cf.

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


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, workdomain.com, localhost, localhost.localdomain, localhost
relayhost = mail.workdomain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 X.X.X.45
mailbox_command =
mailbox_size_limit = 051200000
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =



```

Here is the list of my aliases. Just a note, I had the second line as [email]hammons@personalemail.com[/email], and that works for me.

```

postmaster:     root
root:              hammons@workdomain.com

```

And last but not least the sasl_passwd file (just in case)

```

mail.workdomain.com    domainadmin:domainadminpasswd

```

---

### Post by SeijiSensei on 2017-02-08
How are the messages addressed, in particular what's in the From field?  Is it [email]someone@somerealdomain.com[/email] or something like root@localhost?  Post the headers from the message that was successfully delivered to your personal account.

Perhaps there are spam filters at your workplace that are blocking the message.  Can you check the Exchange server to see if the message arrived and its disposition?

The fact that you can send to your personal account rules out the possibility that your ISP is blocking outbound traffic to remote port 25, so I'd talk with your workplace about the Exchange configuration.

---

### Post by hammons2012 on 2017-02-09
SeijiSensei,

Thanks for the reply! The working setup is that I  have, is that my From field in OpenVAS is user1@localhost, and my To  field as root@localhost (which is forwarded to my personal email). And  you would be correct about the spam filtering, but I don't think it's on  Exchange side, but I will double check sometime today. Note the headers below (I didn't even know you could get the headers from a  Hotmail account.....).

EDIT: I forgot to mention, that I have tried emails that we own in the To and From fields. To field was my work email, and the From was a distribution email that we use for any network outages/alerts/events. I'll try setting this back up, now that I have postfix installed and working.

```

Received: from DM5PR10CA0017.namprd10.prod.outlook.com (10.172.33.27) by
 DM2PR10MB0320.namprd10.prod.outlook.com (10.161.253.22) with Microsoft SMTP
 Server (version=TLS1_2, cipher=TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384_P384) id
 15.1.888.16 via Mailbox Transport; Tue, 7 Feb 2017 23:29:04 +0000
Received: from inbound.mail.protection.outlook.com (216.32.181.177) by
 DM5PR10CA0017.outlook.office365.com (10.172.33.27) with Microsoft SMTP Server
 (version=TLS1_2, cipher=TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384_P384) id
 15.1.888.16 via Frontend Transport; Tue, 7 Feb 2017 23:29:03 +0000
Received: from BY2NAM01FT034.eop-nam01.prod.protection.outlook.com
 (10.152.68.55) by BY2NAM01HT088.eop-nam01.prod.protection.outlook.com
 (10.152.69.63) with Microsoft SMTP Server (version=TLS1_2,
 cipher=TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384_P384) id 15.1.874.2; Tue, 7 Feb
 2017 23:29:01 +0000
Authentication-Results: spf=none (sender IP is 74.142.253.18)
 smtp.mailfrom=mail.workdomain.com; hotmail.com; dkim=none (message not
 signed) header.d=none;hotmail.com; dmarc=none action=none
 header.from=localhost;
Received-SPF: None (protection.outlook.com: mail.workdomain.com does not
 designate permitted sender hosts)
Received: from SNT004-MC10F20.hotmail.com (10.152.68.59) by
 BY2NAM01FT034.mail.protection.outlook.com (10.152.69.3) with Microsoft SMTP
 Server (version=TLS1_2, cipher=TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384_P384) id
 15.1.888.7 via Frontend Transport; Tue, 7 Feb 2017 23:29:01 +0000
X-IncomingTopHeaderMarker: OriginalChecksum:8FC3F58EB059651FDF0B90A6FA6B56CC7F7EC8BE77EADC27ABE05B672C2EA71B;UpperCasedChecksum:F65AAA03D1E86CDFDB8D42A41F34E5666B05E030850E3581D8DC98CECADEA9C6;SizeAsReceived:790;Count:13
Received: from localhost ([74.142.253.18]) by SNT004-MC10F20.hotmail.com with Microsoft SMTPSVC(7.5.7601.23143);
     Tue, 7 Feb 2017 15:28:58 -0800
Received: by localhost (Postfix)
    id B212C13ECCC; Tue,  7 Feb 2017 18:28:57 -0500 (EST)
Delivered-To: root@localhost
Received: by localhost (Postfix, from userid 0)
    id 7E8481416D7; Tue,  7 Feb 2017 18:28:57 -0500 (EST)
To: <root@localhost>
From: <user1@localhost>
Subject: [OpenVAS-Manager] Task 'XXXXXXX': Task status changed to 'Done'
Content-Type: multipart/mixed; boundary="=-=-=-=-="
Message-ID: <20170207232857.7E8481416D7@localhost>
Date: Tue, 7 Feb 2017 18:28:57 -0500
Return-Path: root@mail.workdomain.com
X-OriginalArrivalTime: 07 Feb 2017 23:28:58.0180 (UTC) FILETIME=[F4A81040:01D28199]
X-IncomingHeaderCount: 13
X-MS-Exchange-Organization-Network-Message-Id: a29b6f8c-3c1e-40a3-bae8-08d44fb1193b
X-EOPAttributedMessage: 0
X-EOPTenantAttributedMessage: 84df9e7f-e9f6-40af-b435-aaaaaaaaaaaa:0
X-MS-Exchange-Organization-MessageDirectionality: Incoming
CMM-sender-ip: 74.142.253.18
CMM-sending-ip: 74.142.253.18
CMM-Authentication-Results: hotmail.com; spf=none (sender IP is
 x.x.x.x) smtp.mailfrom=root@mail.workdomain.com; dkim=none
 header.d=localhost; x-hmca=none header.id=user1@localhost
CMM-X-SID-PRA: user1@localhost
CMM-X-AUTH-Result: NONE
CMM-X-SID-Result: NONE
CMM-X-Message-Status: n:n
CMM-X-Message-Delivery: Vj0xLjE7dXM9MDtsPTA7YT0wO0Q9MjtHRD0yO1NDTD00
CMM-X-Message-Info: 11chDOWqoTl20mRzoaosRvoKGqJ99fcz3kHuRteeIlfw44vCpGyr/tgzTlZIsv++KkG0PFskyhhPPgPn5rOG7gGh41Hq395OuVTOvXdlmmnmm/Kov2NsaVf24ZUR7kyMq996fUAVLZWwanEd793QcGdn+gL3H31hO33KMAfIJNwaxT+WBkA951NwEykibO0psnx8scz2B2xj8u8y9qz53me55mSbgQtGgubCumFbntluMTitL+p4UQ==
X-MS-Exchange-Organization-SCL: 5
X-MS-Exchange-Organization-PCL: 2
X-Microsoft-Exchange-Diagnostics: 1;BY2NAM01FT034;1:VpLp/iBT4BJqCUkkvSzA70pQ/zM6EcXTBWFEm7vurjPmuEKTzQ0rjMxdTqFXQz7vccB02DGkUVRvRTYbBuyaCLhtWqGeYQd1k2ybugyjYS/tKNQ9CWdBUC21ILFbOOdTmeSo2sXeARXx8iKcJkZksA==
X-Forefront-Antispam-Report: EFV:NLI;SFV:SPM;SFS:(28900001);DIR:INB;SFP:;SCL:5;SRVR:BY2NAM01HT088;H:SNT004-MC10F20.hotmail.com;FPR:;SPF:None;CAT:SPM;LANG:en;
X-MS-Office365-Filtering-Correlation-Id: a29b6f8c-3c1e-40a3-bae8-08d44fb1193b
X-Microsoft-Antispam: BCL:0;PCL:0;RULEID:(22001)(8291500097)(8291501071);SRVR:BY2NAM01HT088;
X-Microsoft-Exchange-Diagnostics: 1;BY2NAM01HT088;3:F0FUCeAdYcOcJR7WJhuVEt/orm+OwiLI5CuFS/yP2Il+5ufCL2BiuO6sdk/xlxKEq9T8smficOdRjxN33EfQu4p2n2hgq1V+fJwRuA5F615YWb49q9yGZYPa1dFlVFIsxX4+LQydqZAIkr8KQDSmSr4h9GEz7pLpAX9z6bQEb6VF4U6ga/gydiYGRNbglSU1xjjdOoBfMpOqpINvrGONLvZ3L2Q/4ebnMaKd14yvvt/5GvQwgis40mUwAb7DiisNoE5PIvo4CHueGMsfcbA+lN9mTOPv3Q5NS8JT8CK1c1GZJ+idzkqnpQyoi4YOtOvqH1dDKk4DXBRSlU6XLrMqY+2n3XdkYZkKsE7cThsbkRlRDIEgNJggnoAwftmOJ2H9qCED6pU5TLUtzUpfdEsNdg==
X-Microsoft-Exchange-Diagnostics: 1;BY2NAM01HT088;25:zZXg9YMsjiQOyFFziJ2To12D4TMr4Dl3WFaUhAAWGWs3SER7gRBq5L0f8226RHYmwzroObKzr1U6Pt6ZJtdsbJceB9/tOoWJI9vEUCBYfNvP7TW9xf6mtp6ZfmqZEXluayGdvJ1YGIC02j50qposnpgBa2tN+Aw2X2Uq5h5V4zMbai+paFgUBN8bGnWqmmCgN4LXfbYYxlFfbHjA5Fk3EKp+7rJBkDM27+xrUwYhu5q8+iuCIfVbXlRtpchx12VqVh8dXZDsATSWq7T6yNdL/vI6AFbwpJpkj3Z5g4P1uMN4BC5e63HTQljg9V28aoYtkZlTo9KryTJcSGyWEACYvQv3dLuuzRcAdmOXol+KIiy0vCLHU3fs+3ZtEXt0uWhFypGIDUnQhX0dC2ruCmIBPu0IGR89CBFY87kkGixpIM4c43lpJ3npDYzca46AjUwOqj+RqjX8dBoo7Wo4PqYgxe9UouwKh0LvsWi941RXX7yIEoYy9WXSEk+KOs27PvVVwXL5zHNxzGFfeRKy3Rc0Qb3S5NMHCTFhJ/tFUDz9MHIdDJTDPrstEWeyKNPsUdJQ;31:MTNEkF5q9rpcCc0ZlU+/YttBEmpUi2/0H79p/5ptqxrDK7oij8u1Y+FoqfpUJHd34WOVocmM7FvW2uO92pVijNJrEAFcHQyQbEnE3xh1q+f8QGPnYTs+2cEbtsl26+dqmvd8S3TbtXpMnUwyiJsyNDrYcObxhB6Xqa3cIbAQuE5aAIJInpx4KoehOYBbZe1StDb9hDyD7cAIb8+Y9/ckopHNGnY1MXFJJi5bOEcXkrtYmlElzy++cYzzo6KQBRfvunXhSeq1zoXU45/bdJ/IIEUIyKdCFj0ANOwuQa2dS62qnDA2LC+amHDqo7iKbUhShAls4rJRdv9Yl/yvm/53Xg==
X-MS-Exchange-Organization-AVStamp-Service: 1.0
X-Exchange-Antispam-Report-CFA-Test: BCL:0;PCL:0;RULEID:(444111334)(102415395)(82015046);SRVR:BY2NAM01HT088;BCL:0;PCL:0;RULEID:;SRVR:BY2NAM01HT088;
X-Microsoft-Exchange-Diagnostics: 1;BY2NAM01HT088;4:gFhzfYa1ihz+7r4gKWJANO/v6BJiLL1alN7PjVr2V5gt2ejOJYWghblJKwTxvJ3cF2Xq9ghHLsbYthv8ziuK3vThyaRqg8rJauk0gZQTRr/tCke3ns7W8UIOrtmSAAGcbYh606qQr5RXXHQgOwH+DHgjxxo79XLaozRctzMBg8mQ80xg8rQdA2Ut/HOiVkQJRHh6zFBiDR+xuXlo7qsHTwy93rhsE2UrXOQi2LtWI3I8Ee43CgJF6hxwilphPH32FlPBWSQw4Loi0JM/Y07btItN9w33+Udg1Mgrp4fyfiltL4EwFORzLBi4sqX7xhD84qzDUVX61c2+N4GPpxKeYw==;23:0vtHKbFCR3gnfSBrOjvvEpk/JEIrMEzhGkurVwM48Sa7sKBamivhfxjzCT1unfLZEW++mjhuuq8BEZjan4qwx8zsiFR1S9n1eie0+hxJ/8KQn8Mosa34tpC109k7UGR58qoqzr3qFLpLr7aSjobiJbV6qh+UabGZw5SmcHJ48w3nbTsSXTTGXhHDYR3QOLpbTU2jhk+0ucb/UKRJuIVV7A==
X-Microsoft-Exchange-Diagnostics: 1;BY2NAM01HT088;6:2lvMofvMF9lrPIwfnjZrIhrcQYl1snLjRG6mdISaW2/cLz/2wemOnIvTEaq3tv5y/Oee8MfKYE+CF4m6wFskDfUJYDlJAd6TX4Qfz2iBbSRSoLrGi2YsYPXLkn8cOFzSCIBQ78mPZDkHHkSAqrXh065vXjkJ178yZWKgY5LrCMHrtnOsxTFItfN1OQDSq4F9a3jBTXUXfohcThtg1Wc9qF4Y03gFOVQiV8rWMiFcMDcd4NKDCdeJ5ZV45n96xnnY9bBCNhh+Lz/Mn70Z3u7VXo8JQGIhDZW9raL4By6Y+OeUqOPK7l47ypTtz0lMGiDxTEY88jU7G91On262DI4Sosla2PpQZInTCR3udR9lM/WlU8Tqm2GpbXvWPxAqk5Z/jMxHgBaNZjPHayy5Fmd7OPr8n1khfd2/bfXJJlQRDwt0lW9FyYJj184DnyYwbkYTXaw5C0qjjBkhzsZ3f2DjKkQK2WHoh3bPl+MkScu+KiRnV5bDYCdnuHXXFewvA642;5:QoswMhZX1debwMY9pq1jkMYWlMdpsrz/hXjUy6oLf5emFgSDGIdtMyRuSwZWX5AEwUb8hxYPYh1GN5dT3+tPJBs465TBH5cn0hD0CZSvYZzs18WRyMFF2LAue4LtCwDmp0TYsz8Jbpbm+XqCVY8kHVJxBv2ueEvlRd0tHs0y2+k=;24:PmqdgIXO45oqwL3S1dId0nRKkMX3ujxvvlSVKP826GgUvnZYSRlQw3Zu4n17kb8lGistaHIfsflnWzc79ixAhw==
SpamDiagnosticOutput: 1:22
SpamDiagnosticMetadata: Default
X-Microsoft-Exchange-Diagnostics: 1;BY2NAM01HT088;7:9grCgo6t8PiIPJDlXzM3BBRX+Vvms0DDl0qttS/vnxGzaL+hzAftcFiXGNBDyo11/akn7uqL7z1yMTJeUI4NDubhADiZ3Xmk756ok1LmL+wel/lYrE6j7Gtum6tzK919E3d6yLvF9QKFxCOXPA/T96AD/zTyLtdVLrdeMav2vd+Pm4ThyaNYIBERfUGR0Xf1Ue6oovvf4UAN29hoBAf/O5MbGx1HrHECSUfxboL4nvTtzBVy4KGIZ09D4CO+FnJuxXCAVVZC6QnH0psRUaesXnepUiuFKbbBmXC78t9jb2dgThLhEO4lqwcgO0HZgWLUqVCVOh+qaplDpkHu4hS+vRtJPJGRqHVTgYD0xul85QTFqWxfz/b5biPsPe8ZxWEoIfK8O3JKzDzmCNEMmPucKO/x+qoPlhYWITwgmsjqhXHY0kJddT4GEBK+JD/cHDLmt/axj9ZXMXY/6vgmSliXxcZS1x+l7c9/FXWPHV1S/J/HKgMrfJkDwpqORzSWyY3wGLj06Om2DUTO0Icuu/viIWR+VnhbpwpXUdWvTezkvdqTehjaP1GGE8/Pe+M76D/mrX83Kk8sXH3hJzCtQlXhwriVAQCHL1Olv/qXOLvT9+NUFjWUULwMnfzOzSHkZujXry1zPQEInBKT/lOIHmS6jw==
X-MS-Exchange-CrossTenant-OriginalArrivalTime: 07 Feb 2017 23:29:01.0201
 (UTC)
X-MS-Exchange-CrossTenant-Id: 84df9e7f-e9f6-40af-b435-aaaaaaaaaaaa
X-MS-Exchange-CrossTenant-FromEntityHeader: Internet
X-MS-Exchange-Transport-CrossTenantHeadersStamped: BY2NAM01HT088
X-MS-Exchange-Organization-AuthSource: BY2NAM01FT034.eop-nam01.prod.protection.outlook.com
X-MS-Exchange-Organization-AuthAs: Anonymous
X-OriginatorOrg: outlook.com
X-MS-Exchange-Transport-EndToEndLatency: 00:00:03.2144247
X-Microsoft-Exchange-Diagnostics:
    1;DM2PR10MB0320;27:awepxbboH99FOUwnfIQtohmZKFI1X2P7sQjSm4Vb/1asZbnpZxhRqPIDZbD0YVyfCAbeh2F4t3Wvo+WAQAOyknUJhEw0xKDaKBrOdwPZvC+C2qdXnFhDchU+MM4TUKFHMyCVzdYdskx8mnbLXgAx/w==
X-Microsoft-Antispam-Mailbox-Delivery:
    abwl:0;wl:0;pcwl:0;kl:0;iwl:0;ijl:0;dwl:0;dkl:0;rwl:0;ex:0;psp:0;auth:0;dest:J;WIMS-SenderIP:74.142.253.18;WIMS-SPF:mail%2elightchange%2ecom;WIMS-DKIM:localhost;WIMS-822:lightch%40localhost;WIMS-PRA:lightch%40localhost;WIMS-AUTH:NONE;ENG:(102400140)(102420017);RF:JunkEmail;OFR:SpamFilterAuthJ;
MIME-Version: 1.0

--=-=-=-=-=
Content-Type: text/plain; charset="utf-8"
Content-Disposition: inline
Content-Transfer-Encoding: quoted-printable
X-Microsoft-Exchange-Diagnostics:

```

---

### Post by SeijiSensei on 2017-02-09
My email systems would never accept a message from someone@localhost.  

The headers suggest the Exchange server is looking for an SPF record or DKIM header:
```

CMM-Authentication-Results: hotmail.com; spf=none (sender IP is
 x.x.x.x) smtp.mailfrom=root@mail.workdomain.com; dkim=none
 header.d=localhost; x-hmca=none header.id=user1@localhost
Received-SPF: None (protection.outlook.com: mail.workdomain.com does not
 designate permitted sender hosts)

```

If your IP address is relatively static, you could try sending a message 
```
From: openvas@[74.142.253.18]
```
which is a legitimate RFC822 address, though a style used rarely these days.  I have no idea whether Microsoft would treat that address any more kindly than the one you're using now.

---

### Post by hammons2012 on 2017-02-09
SeijiSensei,

So then, would adding a SPF record in my DNS to point to OpenVAS to do the trick? I'll read up on SPF and DKIM and see what I can find, I'm not familiar with the the record type and header. The part about testing mail, there really is no need to send mail externally, both servers are internal and on the same subnet. Since we are sending sensitive information (vulnerabilities of critical servers/network equipment/etc), we don't really want to send these emails to an external account (although if we have to....).

PS, thanks for the assistance!

---

### Post by SeijiSensei on 2017-02-09
I guess I was confused by your earlier description.  I assumed the machine sending this message was connecting to the Exchange server over the public Internet.  Adding to my confusion are the headers you posted which suggest that inbound.mail.protection.outlook.com (216.32.181.177) was the receiving server.

If the OpenVAS machine is on the same local network as the email server, then can't you just send it directly there?  I'd use "openvas@companydomain.com" as the sender address and tell Postfix to use the Exchange server as a relay host.  (Use the "[relayhost]("http://www.postfix.org/postconf.5.html#relayhost")" parameter in main.cf. If your organization maintains an internal DNS server for companydomain.com with an MX record pointing to the Exchange server's internal IP address, you won't need a relay host.)

Try this experiment from the OpenVAS machine.  Run "telnet ip.of.exch.server 25" and see what happens.  You should be able to conduct an SMTP dialogue with the Exchange server like this:
```

[server displays banner and waits]
mail from: openvas@companydomain.com
[server replies]
rcpt to: recipient_mailbox@companydomain.com
[server replies]

```
Either the server will respond positively to this exchange, or it will refuse the connection.  That should give you some hints as to what the problem might be.

---

### Post by hammons2012 on 2017-02-09
SeijiSensei,

I think I might have given you the wrong impression by the headers and all that, because that is from my personal Hotmail account. My apologies. I agree, this should be working out of the box, but for some reason, Exchange isn't accepting email requests from postfix. Note the output from the Telnet tests below. The thing that is frustrating, is that I can email our alert account, and it can email me, and I get these emails in my Outlook inbox yet something is going on with postfix. I have a relay host setup in postfix main.cf file, and I have it pointed to the FQDN of the mail server (which the OpenVAS server should be able to resolve, since it's using the same DNS servers as I). The only thing I can think of is if I need to add the OpenVAS server to our DNS records (maybe a reverse lookup issue or something). If you can't tell, I'm a noob when it comes to email/Exchange/Postfix.

EDIT: I just changed my hostname to what I put it in our DNS server (openvas@workdomain.com).
EDIT2: Adding the DNS entries didn't work.

```

telnet X.X.X.43 25
Trying X.X.X.43...
Connected to X.X.X.43.
Escape character is '^]'.
220 mail.workdomain.com Microsoft ESMTP MAIL Service ready at Thu, 9 Feb 2017 1                                                                                        5:39:50 -0500
mail from: openvas@workdomain.com
503 5.5.2 Send hello first
rcpt to: hammons@workdomain.com
503 5.5.2 Send hello first
quit
221 2.0.0 Service closing transmission channel
Connection closed by foreign host.

```

```

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, workdomain.com, localhost, localhost.localdomain, localhost
relayhost = mail.workdomain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 X.X.X.45
mailbox_command = 
mailbox_size_limit = 051200000
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = 

```

---

### Post by hammons2012 on 2017-02-10
Sorry for the double post, but I felt like I just found something else out, which wouldn't belong to the previous post.

So, I put my personal email address into the To field in OpenVAS, and I never got the email. However, when I forward the email from the root account, I do get an email (meaning To is from root@localhost and From is user1@localhost with an alias for root going to my personal account). I will try to telnet to the OpenVAS/postfix server on port 25 and try to send my work email a message. I will also go back to my Kali VirtualBox VM and see if I can get it to work on it.

---

### Post by SeijiSensei on 2017-02-10
Sorry, I forgot the required first line of the SMTP transaction.  Try again with
```

$ telnet ip.addr.of.exch 25
[server banner]
ehlo name.of.local.machine
[server replies]
mail from: etc.

```

If the OpenVAS machine has a fully-qualified name with matching forward and reverse DNS use that for "name.of.local.machine".  If not, just try using its hostname.

If Exchange doesn't like "ehlo" use "helo" instead.

> So, I put my personal email address into the To field in OpenVAS, and I never got the email. However, when I forward the email from the root account, I do get an email (meaning To is from root@localhost and From is user1@localhost with an alias for root going to my personal account). 
Logs are your friends.  What do you see in /var/log/mail.log when Postfix tries to send directly to your personal account?

> ```

relayhost = mail.workdomain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 X.X.X.45

```
You might need to use [mail.workdomain.com] instead depending on whether there is an MX record specified for workdomain.com.  See the relayhost link I posted above.  You probably also want to use a subnet in mynetworks like 192.168.1.0/24 rather than a specific host address, although since the OpenVAS machine won't be accepting mail, just the localhost addresses should be sufficient.

---

### Post by hammons2012 on 2017-02-10
SeijiSensei,

I think I might not have posted some logs and stuff that I found. Thanks for reminding me about the logs, I forget about them sometimes. So, it was giving me an error about how my hostname was giving errors because I  had put an "@" in it, so I fixed that. I see these in the logs now.

EDIT: Didn't work. I'm about to just call off the emailing, and just suggest to check out the console for reports. Also, I was reading somewhere that issues can arise if you use sendmail with postfix. I don't see sendmail installed via apt list, but you think this could be an issue I am having? I'll try to get admin access to our Exchange server, but I highly doubt that will happen (at this point, I'm pretty much certain that this is due to spam filtering or some kind of filtering).

```

Feb 10 10:22:56 localhost postfix/smtpd[32197]: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: openvas@workdomain.com

```



```
Feb 10 14:32:23 localhost postfix/pickup[35127]: 3088E13F6E7: uid=0 from=<root>
Feb 10 14:32:23 localhost postfix/cleanup[62211]: 3088E13F6E7: message-id=<20170210193223.3088E13F6E7@openvas.workdomain.com>
Feb 10 14:32:23 localhost postfix/qmgr[35128]: 3088E13F6E7: from=<root@mail.workdomain.com>, size=162265, nrcpt=1 (queue active)
Feb 10 14:32:23 localhost postfix/local[62213]: 3088E13F6E7: to=<hammons@workdomain.com>, relay=local, delay=0.74, delays=0.48/0.03/0/0.22, dsn=5.1.1, status=bounced (unknown user: "hammons")
Feb 10 14:32:23 localhost postfix/cleanup[62211]: B0BCD141713: message-id=<20170210193223.B0BCD141713@openvas.workdomain.com>
Feb 10 14:32:23 localhost postfix/qmgr[35128]: B0BCD141713: from=<>, size=2463, nrcpt=1 (queue active)
Feb 10 14:32:23 localhost postfix/bounce[62214]: 3088E13F6E7: sender non-delivery notification: B0BCD141713
Feb 10 14:32:23 localhost postfix/qmgr[35128]: 3088E13F6E7: removed
Feb 10 14:32:24 localhost postfix/smtp[62216]: B0BCD141713: to=<root@mail.workdomain.com>, relay=mail.workdomain.com[X.X.X.43]:25, delay=0.83, delays=0.07/0.22/0.27/0.27, dsn=2.6.0, status=sent (250 2.6.0 <20170210193223.B0BCD141713@openvas.workdomain.com> [InternalId=110019882254363, Hostname=mail.workdomain.com] Queued mail for delivery)
Feb 10 14:32:24 localhost postfix/qmgr[35128]: B0BCD141713: removed

```

Also, the telnet mail test was successful.

```

220 mail.workdomain.com Microsoft ESMTP MAIL Service ready at Fri, 10 Feb 2017 14:41:57 -0500
ehlo mail.workdomain.com
250-mail.workdomain.com Hello [X.X.X.45]
250-SIZE 37748736
250-PIPELINING
250-DSN
250-ENHANCEDSTATUSCODES
250-STARTTLS
250-X-ANONYMOUSTLS
250-AUTH NTLM
250-X-EXPS GSSAPI NTLM
250-8BITMIME
250-BINARYMIME
250-CHUNKING
250 XRDST
mail from: openvas@workdomain.com
250 2.1.0 Sender OK
rcpt to: hammons@workdomain.com
250 2.1.5 Recipient OK
quit
221 2.0.0 Service closing transmission channel
Connection closed by foreign host.

```

I just removed the listings in my alias folder, applied them, and restarted postifx and will try another run. I also removed some of the config on my main.cf file.

```

smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =

```

---

### Post by hammons2012 on 2017-02-15
Well, I finally got the emailing to work! I found someone who used the "Satellite System" option for the initial configuration setup for postfix, so I just ran the option to reconfigure the packages (sudo dpkg-reconfigure postfix). For anyone who is interested, this is what my main.cf looks like now.

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


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = openvas.workdomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =
relayhost = X.X.X.43
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 X.X.X.45 X.X.X.0/24
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = all

```

---

