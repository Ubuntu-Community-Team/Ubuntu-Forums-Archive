---
title: "postfix mail goes in junkmail"
date: 2010-03-15
forum: Server Platforms
---

### Post by mrwolf on 2010-03-15
Hi,

(note: sorry for my bad english)
it's been three days since I swim in this nightmare.

I use Ubuntu Server 9.10 64bit

at first, sendmail was installed and everything was working great. all the email sent from forum and webform I host as been sent correctly in the reception box of the recipient. But I want postfix as MTA to do my delivery to all my virtual domain I host.

when sendmail is uninstalled and postfix installed and all services configured(php included) and restarted(apache included), when I send a email from command line or from web form, the email goes in junk mail for some ISP email address and for gmail and the email did'nt show at all for hotmail. but email sent from forum (phpbb) still goes in reception box like normal email do.

I tried do change the headers, who was working with sendmail, of the email sent from web form without success.

so I tried to uninstall postfix and reinstall sendmail, restarted all service and every thing was back to normal... email sent goes in reception box.

I tried it twice.... sendmail, postfix, sendmail, postfix and now back to sendmail for a working solution until I get postfix working.

I tried with spf entry in my dns, I tried allowed icmp packet from outside with iptables, I tried many different headers for my email. My ip is not blacklisted anywhere.

if anyone can help me fix this issue, I'll be glad ;)

Thanks

---

### Post by dudumomo on 2010-03-15
Did you try to use your ISP relayhost ?

---

### Post by mrwolf on 2010-03-15
I can't really, it's on a dedicated server.

---

### Post by lisati on 2010-03-15
Sometimes when you're running your own server and bypassing your ISP's mail system there's the potential for problems at the recipient's end, particularly if you're using what's perceived as a dynamic IP address or if your server's address is part of a block that has been "blacklisted". Some useful resources for checking if this is the case can be found at [http://debouncer.com]("http://debouncer.com"), [http://www.blacklistalert.org/]("http://www.blacklistalert.org/"), and [http://whatismyipaddress.com/staticpages/index.php/is-my-ip-address-blacklisted]("http://whatismyipaddress.com/staticpages/index.php/is-my-ip-address-blacklisted")

There is a workaround for postfix so that it will use an ISP's system but I can't remember the details at the moment.

---

### Post by mrwolf on 2010-03-15
Thanks lisati

my dedicated server has a static ip with a matching dns and rdns.

After I checked all your link, I saw that my dedicated server is blocked from blackholes.five-ten-sg.com

but if I can't send email with postfix because of my blacklisted ip, why can I with sendmail?

---

### Post by lisati on 2010-03-15
The blacklists usually kick in at the receiver's end, not the sender's end. One problem I had to overcome for my server was that my ISP blocked port 25, which prevented me sending out email directly. Once I'd arranged a static IP, they were happy to unblock it.

---

### Post by mrwolf on 2010-03-15
I don't have problem with port, I have a dedicated server with all port unblocked, I can easily telnet my server on port 25.

with the same sender and receiver, an email sent with sendmail will pass but will be blocked when sent with postfix

---

### Post by KB1JWQ on 2010-03-15
Do you have matching forward and reverse DNS?  If that's taken care of, and JUST postfix mail ends up getting rejected, paste the contents of your maillog so we can see what's happening.

-- KB1JWQ

---

### Post by mrwolf on 2010-03-15
> **KB1JWQ said:**
> Do you have matching forward and reverse DNS?  If that's taken care of, and JUST postfix mail ends up getting rejected, paste the contents of your maillog so we can see what's happening.

-- KB1JWQ

Hi KB1JWQ,

yes as I already said, I have a matching dns and reverse dns.

this is my log:
Sendmail:
```
Mar 14 12:56:08 host sendmail[23096]: o2EJu874023096: from=www-data, size=257, class=0, nrcpts=1, msgid=<201003141956.o2EJu874023096@host.domain.com>, relay=www-data@localhost
Mar 14 12:56:09 host sendmail[23096]: o2EJu874023096: to=some_alias@hotmail.com, ctladdr=www-data (33/33), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30257, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (o2EJu8YB023097 Message accepted for delivery)
```

Postfix:
```
Mar 14 15:10:38 host postfix/pickup[3322]: 8B89120A7C: uid=33 from=<www-data>
Mar 14 15:10:38 host postfix/cleanup[3328]: 8B89120A7C: message-id=<20100312231038.8B89120A7C@host.domain.com>
Mar 14 15:10:38 host postfix/qmgr[3323]: 8B89120A7C: from=<www-data@domain.com>, size=455, nrcpt=1 (queue active)
Mar 14 15:10:38 host postfix/smtp[3330]: 8B89120A7C: to=<some_alias@hotmail.com>, relay=mx2.hotmail.com[65.55.37.104]:25, delay=0.23, delays=0.12/0.01/0.03/0.07, dsn=2.0.0, status=sent (250  <20100312231038.8B89120A7C@host.domain.com> Queued mail for delivery)
Mar 14 15:10:38 host postfix/qmgr[3323]: 8B89120A7C: removed
```

---

### Post by KB1JWQ on 2010-03-15
Heh, sorry-- must have missed that.

Can you put up the output of postconf -n?

---

### Post by mrwolf on 2010-03-15
I can't right now cause I uninstall postfix to have a working server.

but this is my main.cf
```
myhostname = host.domain.com

myorigin = domain.com

smtpd_banner = $myhostname ESMTP $mail_name
biff = no
append_dot_mydomain = no

delay_warning_time = 4h

readme_directory = no

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

mydestination =
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

unknown_local_recipient_reject_code = 450

maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s

smtp_helo_timeout = 60s

smtpd_recipient_limit = 16

smtpd_soft_error_limit = 3

smtpd_hard_error_limit = 12

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit

smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit

smtpd_data_restrictions = reject_unauth_pipelining

smtpd_helo_required = yes

smtpd_delay_reject = yes
disable_vrfy_command = yes

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
```

---

### Post by KB1JWQ on 2010-03-15
Send yourself a message from Sendmail, then send yourself a message from Postfix.  Are there any differences between the two?  If not, please post full headers from both, I want to see where this spam-binning comes from. :-)

---

### Post by mrwolf on 2010-03-15
here it is...

Postfix:
```

Delivered-To: some_alias@gmail.com
Received: by 10.90.120.17 with SMTP id s17cs227562agc;
        Sun, 14 Mar 2010 12:20:08 -0700 (PDT)
Received: by 10.114.99.5 with SMTP id w5mr4714488wab.89.1268594408011;
        Sun, 14 Mar 2010 12:20:08 -0700 (PDT)
Return-Path: <alias@domain.com>
Received: from host.domain.com (host.domain.com [m.y.i.p])
        by mx.google.com with ESMTP id 6si26486501pzk.31.2010.03.14.12.20.07;
        Sun, 14 Mar 2010 12:20:07 -0700 (PDT)
Received-SPF: pass (google.com: domain of alias@domain.com designates m.y.i.p as permitted sender) client-ip=m.y.i.p;
Authentication-Results: mx.google.com; spf=pass (google.com: domain of alias@domain.com designates m.y.i.p as permitted sender) smtp.mail=alias@domain.com
Received: by host.domain.com (Postfix, from userid 1001)
	id 4A6E620AAC; Sun, 14 Mar 2010 12:20:23 -0700 (PDT)
Message-Id: <20100314192023.4A6E620AAC@host.domain.com>
Date: Sun, 14 Mar 2010 12:20:12 -0700 (PDT)
From: alias@domain.com
To: undisclosed-recipients:;
```


Sendmail:
```

X-Message-Delivery: Vj0xLjE7dXM9MDtsPTA7YT0xO0Q9MTtTQ0w9MA==
X-Message-Status: n:0
X-SID-PRA: My Name <some_alias@gmail.com>
X-SID-Result: Neutral
X-AUTH-Result: NONE
X-Message-Info: JGTYoYF78jHgIR/d6NrePwpiRBF4HazYAT7vMPXIVugxOLEwcNK0uX/PwlGJh8iK0KmUHkp1O/02a9xq8QLtHk6s9Iojsy5v
Received: from host.domain.com ([m.y.i.p]) by bay0-mc1-f17.Bay0.hotmail.com with Microsoft SMTPSVC(6.0.3790.3959);
	 Mon, 15 Mar 2010 18:54:18 -0700
Received: from host.domain.com (localhost [127.0.0.1])
	by host.domain.com (8.14.3/8.14.3/Debian-9ubuntu1) with ESMTP id o2G1sRmb018790
	for <some_alias@hotmail.com>; Mon, 15 Mar 2010 18:54:27 -0700
Received: (from www-data@localhost)
	by host.domain.com (8.14.3/8.14.3/Submit) id o2G1sRgV018789;
	Mon, 15 Mar 2010 18:54:27 -0700
Date: Mon, 15 Mar 2010 18:54:27 -0700
Message-Id: <201003160154.o2G1sRgV018789@host.domain.com>
To: some_alias@hotmail.com
Subject: subject
From: My Name <some_alias@gmail.com>
Reply-To: My Name <some_alias@gmail.com>
X-Mailer: PHP/5.2.10-2ubuntu6.4
X-Priority: 3
Return-Path: www-data@host.domain.com
X-OriginalArrivalTime: 16 Mar 2010 01:54:19.0033 (UTC) FILETIME=[974CE090:01CAC4AB]
```

---

### Post by KB1JWQ on 2010-03-15
There we go.

Note the differences.
From: My Name <some_alias@gmail.com>

was accepted, but without a realname component your provider found the message spammier and junkbinned it.

It's not an MTA issue.

---

### Post by mrwolf on 2010-03-15
so I need to change the headers of my php script from "FROM: [email]email@domain.com[/email]" to "FROM: NAME <email@domain.com>" because postfix doesn't send it properly?

both email used the same php script.

I readed on another forum that using this style: "name <email>" is wrong. finally is it the right way to do it?

---

### Post by KB1JWQ on 2010-03-15
Postfix serves as a drop-in replacement for sendmail; the From header isn't modified by anything it does.  

As far as what's accepted, it depends on the remote site.  Most clients throw that in, but it's your decision; RFCs 5321 and 5322 address this.

---

### Post by mrwolf on 2010-03-16
I did more test....

sendmail:
```

Mar 16 03:50:08 Gaia sm-mta[29489]: o2GAo8GV029489: from=<www-data@host.domain.com>, size=482, class=0, nrcpts=1, msgid=<201003161050.o2GAo8YM029487@host.domain.com>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Mar 16 03:50:10 Gaia sm-mta[29491]: o2GAo8GV029489: to=<some_alias@gmail.com>, ctladdr=<www-data@host.domain.com> (33/33), delay=00:00:02, xdelay=00:00:02, mailer=esmtp, pri=120482, relay=gmail-smtp-in.l.google.com. [74.125.113.27], dsn=2.0.0, stat=Sent (OK 1268736598 22si4432839vws.15)

Delivered-To: some_alias@gmail.com
Received: by 10.90.120.17 with SMTP id s17cs30346agc;
        Tue, 16 Mar 2010 03:49:58 -0700 (PDT)
Received: by 10.220.121.229 with SMTP id i37mr3977441vcr.114.1268736598033;
        Tue, 16 Mar 2010 03:49:58 -0700 (PDT)
Return-Path: <www-data@host.domain.com>
Received: from host.domain.com (host.domain.com [m.y.i.p])
        by mx.google.com with ESMTP id 22si4432839vws.15.2010.03.16.03.49.57;
        Tue, 16 Mar 2010 03:49:57 -0700 (PDT)
Received-SPF: pass (google.com: best guess record for domain of www-data@host.domain.com designates m.y.i.p as permitted sender) client-ip=m.y.i.p;
Authentication-Results: mx.google.com; spf=pass (google.com: best guess record for domain of www-data@host.domain.com designates m.y.i.p as permitted sender) smtp.mail=www-data@host.domain.com
Received: from host.domain.com (localhost [127.0.0.1])
	by host.domain.com (8.14.3/8.14.3/Debian-9ubuntu1) with ESMTP id o2GAo8GV029489
	for <some_alias@gmail.com>; Tue, 16 Mar 2010 03:50:08 -0700
Received: (from www-data@localhost)
	by host.domain.com (8.14.3/8.14.3/Submit) id o2GAo8YM029487;
	Tue, 16 Mar 2010 03:50:08 -0700
Date: Tue, 16 Mar 2010 03:50:08 -0700
Message-Id: <201003161050.o2GAo8YM029487@host.domain.com>
To: some_alias@gmail.com
Subject: sendmail
From: Francois <some_alias@other_domain.com>
Reply-To: Francois <some_alias@other_domain.com>
X-Mailer: PHP/5.2.10-2ubuntu6.4
X-Priority: 3

```

Postfix:
```

Mar 16 03:57:38 Gaia postfix/smtp[1833]: 265E1206F3: to=<some_alias@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.222.93]:25, delay=141, delays=140/0.02/0.31/0.5, dsn=2.0.0, status=sent (250 2.0.0 OK 1268737058 33si12843814pzk.5)
Mar 16 03:57:38 Gaia postfix/qmgr[1828]: 265E1206F3: removed

Delivered-To: some_alias@gmail.com
Received: by 10.90.120.17 with SMTP id s17cs30630agc;
        Tue, 16 Mar 2010 03:57:38 -0700 (PDT)
Received: by 10.141.4.9 with SMTP id g9mr7003459rvi.31.1268737058038;
        Tue, 16 Mar 2010 03:57:38 -0700 (PDT)
Return-Path: <www-data@domain.com>
Received: from host.domain.com (host.domain.com [m.y.i.p])
        by mx.google.com with ESMTP id 33si12843814pzk.5.2010.03.16.03.57.37;
        Tue, 16 Mar 2010 03:57:37 -0700 (PDT)
Received-SPF: pass (google.com: domain of www-data@domain.com designates m.y.i.p as permitted sender) client-ip=m.y.i.p;
Authentication-Results: mx.google.com; spf=pass (google.com: domain of www-data@domain.com designates m.y.i.p as permitted sender) smtp.mail=www-data@domain.com
Received: by host.domain.com (Postfix, from userid 33)
	id 265E1206F3; Tue, 16 Mar 2010 03:55:17 -0700 (PDT)
To: some_alias@gmail.com
Subject: postfix
From: Francois <some_alias@other_domain.com>
Reply-To: Francois <some_alias@other_domain.com>
X-Mailer: PHP/5.2.10-2ubuntu6.4
X-Priority: 3
Message-Id: <20100316105737.265E1206F3@host.domain.com>
Date: Tue, 16 Mar 2010 03:55:17 -0700 (PDT)

```

PHP Script:
```

<?
if(!empty($HTTP_POST_VARS['sender_mail']) || !empty($HTTP_POST_VARS['sender_message']) || !empty($HTTP_POST_VARS['sender_subject']) || !empty($HTTP_POST_VARS['sender_name']))
{
        $to = "some_alias@hotmail.com";
        $from = stripslashes($HTTP_POST_VARS['sender_mail']);
        list($username, $mailDomain) = split("@", $from);
        $subject = stripslashes($HTTP_POST_VARS['sender_subject']);
        $body = stripslashes($HTTP_POST_VARS['sender_message']);
        $body .= "\n\n---------------------------\n";
        $body .= "Message de: " . $HTTP_POST_VARS['sender_name'] . " <" . $from . ">\n";
        $header = "From: " . $HTTP_POST_VARS['sender_name'] . " <" . $from . ">\n";
        $header .= "Reply-To: " . $HTTP_POST_VARS['sender_name'] . " <" . $HTTP_POST_VARS['sender_mail'] . ">\n";
        $header .= "X-Mailer: PHP/" . phpversion() . "\n";
        $header .= "X-Priority: 3";
        if(!empty($username) && !empty($mailDomain) && checkdnsrr($mailDomain, 'MX'))
        {
                if(@mail($to, $subject, $body, $header))
                {
                        echo "&contact=sent&";
                } else {
                        echo "&contact=error&";
                }
        } else {
                echo "&contact=email&";
        }
} else {
        echo "&contact=field&";
}
?>

```

if the email is sent to hotmail, now it goes in the reception box with both sendmail and postfix, if the email is sent to gmail, it goes in junkmail with both postfix and sendmail.

at least postfix and sendmail now act the same...

Even if the email of the sender is invalid, for hotmail,now it goes in the reception box... wtf?

since my last test, the only thing as change is my ip was removed from the blackholes.five-ten-sg.com Blacklist

anyway... it works now so, thats' good.

Thanks everyone

---

### Post by KB1JWQ on 2010-03-16
Glad you got it sorted. If you're going to be sending a lot of volume you might look into getting a feedback loop set up with the major players.

---

### Post by mrwolf on 2010-03-16
thanks for the advice but I'll send under 100/day so I don't think I'll need anything else.

maybe in the futur.. if everything goes well for me ;)

---

