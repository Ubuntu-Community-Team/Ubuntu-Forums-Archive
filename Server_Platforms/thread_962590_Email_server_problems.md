---
title: "Email server problems"
date: 2008-10-29
forum: Server Platforms
---

### Post by Cowzor on 2008-10-29
Hey,

I'm still very new at setting up an e-mail server, but I wanted to give it a go anyway. I installed Ubuntu server edition on the pc I want to use as the server. I also installed apache2, php and mysql on there before I started on the email server.

So first I followed this guide as closely as I could: [https://help.ubuntu.com/8.04/serverguide/C/postfix.html](https://help.ubuntu.com/8.04/serverguide/C/postfix.html) and everything seemed to be working.

Next, I installed openwebmail for the actual interface using this guide:  [https://help.ubuntu.com/community/OpenWebMail](https://help.ubuntu.com/community/OpenWebMail) and there were no errors there either.

I havn't done anything else besides what those guides said, no extra email related programs or any extra configuration file tinkering.

So to test the whole set up, I tried to send an email to my hotmail but nothing got delivered. I opened /var/log/mail.log and among some other stuff this is what I found:

```

Oct 29 17:06:01 server postfix/smtp[6234]: connect to mx4.hotmail.com[65.54.245.104]:25: Connection timed out
Oct 29 17:06:31 server postfix/smtp[6234]: connect to mx1.hotmail.com[65.54.244.8]:25: Connection timed out
Oct 29 17:07:01 server postfix/smtp[6234]: connect to mx2.hotmail.com[65.54.244.40]:25: Connection timed out
Oct 29 17:07:31 server postfix/smtp[6234]: connect to mx3.hotmail.com[65.54.245.72]:25: Connection timed out
Oct 29 17:08:01 server postfix/smtp[6234]: connect to mx3.hotmail.com[65.54.244.200]:25: Connection timed out
Oct 29 17:08:01 server postfix/smtp[6234]: 7041CBF627: to=<xxxx@hotmail.com>, relay=none, delay=151, delays=0.1/0.04/151/0, dsn=4.4.1, status=deferred (connect to mx3.hotmail.com[65.54.244.200]:25: Connection timed out)
Oct 29 17:10:29 server postfix/qmgr[5740]: 80AE7BF621: from=<root@server.unknown>, size=622, nrcpt=1 (queue active)
Oct 29 17:10:59 server postfix/smtp[6248]: connect to openwebmail.acatysmoof.com[24.205.141.134]:25: Connection timed out
Oct 29 17:10:59 server postfix/smtp[6248]: 80AE7BF621: to=<stats@openwebmail.acatysmoof.com>, relay=none, delay=468, delays=438/0.04/30/0, dsn=4.4.1, status=deferred (connect to openwebmail.acatysmoof.com[24.205.141.134]:25: Connection timed out)
Oct 29 17:15:29 server postfix/qmgr[5740]: 7041CBF627: from=<--linuxusername--@server.unknown>, size=595, nrcpt=1 (queue active)
Oct 29 17:16:00 server postfix/smtp[6251]: connect to mx3.hotmail.com[65.54.244.72]:25: Connection timed out
Oct 29 17:16:30 server postfix/smtp[6251]: connect to mx3.hotmail.com[65.54.244.200]:25: Connection timed out
Oct 29 17:17:00 server postfix/smtp[6251]: connect to mx1.hotmail.com[65.54.245.8]:25: Connection timed out
Oct 29 17:17:30 server postfix/smtp[6251]: connect to mx2.hotmail.com[65.54.244.40]:25: Connection timed out
Oct 29 17:18:00 server postfix/smtp[6251]: connect to mx2.hotmail.com[65.54.245.40]:25: Connection timed out
Oct 29 17:18:00 server postfix/smtp[6251]: 7041CBF627: to=<xxxx@hotmail.com>, relay=none, delay=750, delays=599/0.04/150/0, dsn=4.4.1, status=deferred (connect to mx2.hotmail.com[65.54.245.40]:25: Connection timed out)

```

Where xxxx is my hotmail adress and --linuxusername-- is the username I use on my server.

Does anyone know what I have done wrong or should change?

---

### Post by MJN on 2008-10-29
It could be that your ISP blocks outgoing port 25, or you have a firewall issue between you and your Internet connection.
 
Mathew

---

### Post by Cowzor on 2008-10-29
Actually I do remember reading something about my ISP blocking port 25... I'll test Gmail first, if that doesn't work I'll also test the email I got with my ISP.

---

### Post by Cowzor on 2008-10-29
Yeah I'm pretty sure port 25 is blocked. How can I check for sure? Also, if that is the case, are there any workarounds?

---

### Post by MJN on 2008-10-29
You could try setting Postfix to relay outgoing mail via your ISP's mail server using the directive **relahost = [your.isp.mail.server]** (note the brackets - these are required). Indeed if they do block port 25 then this is going to be your only practical solution anyway.

Mathew

---

### Post by Cowzor on 2008-10-29
I tried the relayhost thing, and now in the logs I am getting a response, so I'm assuming the smpt server adress is valid but it is rejecting my emails.

Then I found this thread where MJN posted a long time ago:

[http://ubuntuforums.org/showthread.php?t=196039]("http://ubuntuforums.org/showthread.php?t=196039")

And I think I may have found my problem, because the log says: 
```
550-Verification failed for <username@server.unknown> 550-Unrouteable address 550 Sender verify failed (in reply to MAIL FROM command))
```

The problem must be the @server.unknown bit. I followed what MJN said, setting myorigin in main.cf but that had no effect (yes, I restarted postfix, even rebooted... no effect). Furthermore, the @server.unknown also shows up in the page title when I log into openwebmail with my account.

---

### Post by MJN on 2008-10-30
Defining the From: address is really the responsibility of the mail client. Postfix only contains options to complete this as it cannot function properly with incomplete addresses.

Hence you need to configure your From: address in Openwebmail. I've not used it so cannot pinpoint where this done but it shouldn't be too difficult to find (check your options page(s), particular any that sound like they relate to identities).

The receiving MTA is complaining because it can tell the From: address is invalid hence if it later finds it cannot deliver the message then it knows it is not going to be able to send a non-delivery report back. Furthermore, it looks like spam given 'genuine' e-mails tend to have genuine From: addresses.

Mathew

---

### Post by Cowzor on 2008-10-30
When logged in to openwebmail and going into my prefs, there is a "from" dropdown list, but the email adress in there still has @server.unknown appended to it.

---

### Post by MJN on 2008-10-30
You need to read the documentation.

Specifically, the FAQ at [http://openwebmail.org/openwebmail/doc/faq.txt](http://openwebmail.org/openwebmail/doc/faq.txt) gives:

```
Q: The domainname detected by openwebmail is not what I want,
   how can I specified the outgoing mail domain for all my users?
A: Please set the domainnames option in openwebmail.conf from 'auto' to
   the domainname you want. Multiple domainnames can be specified only
   if separated by comma
```Mathew

---

### Post by Cowzor on 2008-10-30
Thanks! I had already looked in the FAQ but obviously missed that part :P

Anyway, outgoing email is working fine now, but sending an email back isn't working (I kinda expected that would happen anyway...). Anything in particular I should look into? Certain configurations or an extra programs?

In case it helps: The server is on my home network, behind a router (Port 25 has been forwarded on it). And the domain name is through dyndns.

Thanks again for all your patience and help so far. In the meantime I'll keep on looking mysqlf for a solution.

---

### Post by MJN on 2008-10-30
If you tell us your domain name we can at least eliminate the DNS, routing, incoming port 25 and outward-facing Postfix configuration from being possible causes.

Also copy the non-delivery report that external senders receive when delivery fails.

Mathew

---

### Post by Cowzor on 2008-10-30
[http://cowzorftw.game-host.org](http://cowzorftw.game-host.org)

Also, where exactly can I find the non-delivery report you are talking about? Because both hotmail and gmail don't give any errors when I send, no email saying it couldn't be delivered either but my openwebmail isn't showing anything in the inbox either.

---

### Post by MJN on 2008-10-30
Firstly, you ought to fully configure the DNS for cowzorftw.game-host.org with some MX records. This will tell mail servers who and where the mail server is for your domain. In the absence of such records most will fallback to using the A record (which you have got) but it is wise not to rely on this (and in many cases might not be appropriate).

Secondly, there is no service listening on port 25 at 94.209.224.68. You need to find out why - Postfix not running, ISP blocking incoming port 25, a firewall in place or the wrong port forwarding in your router.

The non-delivery reports will be generated by Hotmail/Gmail and sent back to the sender of the failed message. In this case as it cannot get through they could well be queuing the mail for a later attempt at delivery hence an NDR may be generated later on.

Mathew

---

### Post by Cowzor on 2008-10-30
> Firstly, you ought to fully configure the DNS for cowzorftw.game-host.org with some MX records. This will tell mail servers who and where the mail server is for your domain. In the absence of such records most will fallback to using the A record (which you have got) but it is wise not to rely on this (and in many cases might not be appropriate).

Yeah I did see something about an MX record in the dyndns configuration panel, but I'm not quite sure how they work, do you  maybe know a guide that you could link me to that shows what exactly is supposed to go into an MX record?

> Secondly, there is no service listening on port 25 at 94.209.224.68. You need to find out why - Postfix not running, ISP blocking incoming port 25, a firewall in place or the wrong port forwarding in your router.

I'm pretty sure my ISP blocks port 25 in borth directions, postfix is running and I don't think there is a firewall in place, I will double check that later.

> The non-delivery reports will be generated by Hotmail/Gmail and sent back to the sender of the failed message. In this case as it cannot get through they could well be queuing the mail for a later attempt at delivery hence an NDR may be generated later on.

I'll be keeping a look out for those.

I have some other stuff to do right now so I'll be checking back in a few hours.

---

### Post by MJN on 2008-10-30
If your ISP blocks incoming 25 then you're out of luck. There is a workaround available, although it's a poor one at that, and that is to use something like no-ip's [Mail Reflector](http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html) service.

Mathew

---

### Post by Cowzor on 2008-11-02
Sorry it has taken me so long to get back, I do have some non delivery reports though:

Gmail:

```

Technical details of temporary failure:
The recipient server did not accept our requests to connect. Learn more at http://mail.google.com/support/bin/answer.py?answer=7720
[cowzorftw.game-host.org (1): Connection timed out]

  ----- Message header follows -----

Received: by 10.142.254.8 with SMTP id b8mr4743340wfi.58.1225379492023;
       Thu, 30 Oct 2008 08:11:32 -0700 (PDT)
Received: by 10.142.254.15 with HTTP; Thu, 30 Oct 2008 08:11:31 -0700 (PDT)
Message-ID: <d0bd73290810300811g158f8b58w35070813ffb90fa8@mail.gmail.com>
Date: Thu, 30 Oct 2008 16:11:31 +0100
From: "???" <???@gmail.com>
To: ???@cowzorftw.game-host.org
Subject: send test
MIME-Version: 1.0
Content-Type: multipart/alternative;
       boundary="----=_Part_11142_5353065.1225379492003"

  ----- Message body suppressed -----

```

Hotmail:

```

Reporting-MTA: dns;col0-omc2-s11.col0.hotmail.com
Received-From-MTA: dns;COL103-DS24
Arrival-Date: Thu, 30 Oct 2008 07:55:23 -0700

Final-Recipient: rfc822;???@cowzorftw.game-host.org
Action: failed
Status: 4.4.7

```

---

### Post by MJN on 2008-11-02
Yes, it's almost certainly your ISP blocking port 25 in both directions.

Mathew

---

### Post by HermanAB on 2008-11-02
If you want to run your own mail server, then you need a server account.  This typically only costs about $10 more than a regular account and you usually get more bandwidth too.

---

### Post by Cowzor on 2008-11-02
I don't think my ISP has a special server option, but I'll contact them to see if there is anything I can do about the whole port 25 problem.

---

