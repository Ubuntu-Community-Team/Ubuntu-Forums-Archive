---
title: "DNS record problem"
date: 2008-06-23
forum: Server Platforms
---

### Post by sDoky on 2008-06-23
Hi guys, I have an email server running on my machine. I have been using free DNS record from no-ip (sdoky.sytes.net) and it worked just fine. Now I have bought a DNS record dokoupil.biz and the mail does not work anymore, not because of settings of the server but I believe it's because of The DNS record. Here's sample of mailer daemon report:
```
You message for <[jirka@dokoupil.biz]("http://email.seznam.cz/newMessageScreen?sessionId=&to=mailto:jirka@dokoupil.biz")> from 2008/06/23 could not be delivered.
 It's attached below.
 Reason:
 ---------------
 
** 5.4.3 smtp; no valid MX record**
 
Could not resolve recipient's email server.
 
original message:
 ------------------------
 
 To: [jirka@dokoupil.biz]("http://email.seznam.cz/newMessageScreen?sessionId=&to=mailto:jirka@dokoupil.biz")
 Date: Mon, 23 Jun 2008 20:22:04 +0200 (CEST)
 From: =?iso-8859-2?Q?Dokoupil=20Ji=F8=ED?= <[Dokoupil.Jirka@seznam.cz]("http://email.seznam.cz/newMessageScreen?sessionId=&to=mailto:Dokoupil.Jirka@seznam.cz")>
 Received: from ( [193.179.167.161])
     by email.seznam.cz (Email.Seznam.cz) with HTTP
     for [Dokoupil.Jirka@seznam.cz]("http://email.seznam.cz/newMessageScreen?sessionId=&to=mailto:Dokoupil.Jirka@seznam.cz");
     Mon, 23 Jun 2008 20:22:03 +0200 (CEST)
 Subject: =?us-ascii?Q?kkkkjfjfnnnv=2Cf=2Egnljrgoijowihgosighowighorihg?=
 Content-Type: multipart/alternative;
     boundary="MessagePart:1508386686.0-11601-1420777856-1214245324"
 Mime-Version: 1.0
 Message-Id: <[123.435-11601-334244426-1214245324@seznam.cz]("http://email.seznam.cz/newMessageScreen?sessionId=&to=mailto:123.435-11601-334244426-1214245324@seznam.cz")>
 X-Abuse: [abuse@seznam.cz]("http://email.seznam.cz/newMessageScreen?sessionId=&to=mailto:abuse@seznam.cz")
 X-Seznam-User: [Dokoupil.Jirka@seznam.cz]("http://email.seznam.cz/newMessageScreen?sessionId=&to=mailto:Dokoupil.Jirka@seznam.cz")
 X-QM-Mark: email-qm3<125876794>
 
 
 
 --MessagePart:1508386686.0-11601-1420777856-1214245324
 Content-Transfer-Encoding: quoted-printable
 Content-Type: text/plain;
     charset="iso-8859-2"
 
 ldfjlkjlk=A7
 
 
 --MessagePart:1508386686.0-11601-1420777856-1214245324
 Content-Transfer-Encoding: quoted-printable
 Content-Type: text/html;
     charset="iso-8859-2"
 
 ldfjlkjlk=A7<br>
 <br>
 
 --MessagePart:1508386686.0-11601-1420777856-1214245324--
```My DNS record:
[[IMG]http://img67.imageshack.us/img67/6845/examplelb5.th.jpg[/IMG]]("http://img67.imageshack.us/my.php?image=examplelb5.jpg")

I do not understand the syntax of the MX record. Can you help me please?
Thanks

---

### Post by artesvida on 2008-06-23
I'm not sure how you set this up with your DNS provider, but your MX record tells the world the IP address of your mail server.  This needs to be a publicly accessible IP address.

---

### Post by sDoky on 2008-06-23
of course I know that. I just do not know what to write there. The type-in control script is literally bullying me, do not wrire comma, there must be an @...
> **artesvida said:**
> I'm not sure how you set this up with your DNS provider, but your MX record tells the world the IP address of your mail server.  This needs to be a publicly accessible IP address.

---

### Post by aos101 on 2008-06-23
It seems to me the DNS for your domain is OK.  How long ago did you change the DNS in your control panel?  It might be that when you sent the above message, the MX record hadn't been added to the authoritative DNS servers for your domain yet.  

I just tried sending an email to the address mentioned in the above email and got this back from your server, so the email is reaching your server fine:
```
This is the mail system at host dokoupil.biz.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                  The mail system

<email@address>: maildir delivery failed: create maildir file
   /home/jirka/Maildir/tmp/1214251603.P24795.dokoupil.biz: Permission denied

Final-Recipient: rfc822; email@address
Original-Recipient: rfc822;email@address
Action: failed
Status: 5.2.0
Diagnostic-Code: X-Postfix; maildir delivery failed: create maildir file
   /home/jirka/Maildir/tmp/1214251603.P24795.dokoupil.biz: Permission denied
```

---

### Post by sDoky on 2008-06-23
Hey! It works!!! I just had to change permissions to the Maildir folder! Thanks for your report!
EDIT: I was using sdoky account at first but when I registered my domain as my surname I wanted to have the username my birth name... I created new account and did not worry about the permissions...
> **aos101 said:**
> It seems to me the DNS for your domain is OK.  How long ago did you change the DNS in your control panel?  It might be that when you sent the above message, the MX record hadn't been added to the authoritative DNS servers for your domain yet.  

I just tried sending an email to the address mentioned in the above email and got this back from your server, so the email is reaching your server fine:
```
This is the mail system at host dokoupil.biz.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                  The mail system

<email@address>: maildir delivery failed: create maildir file
   /home/jirka/Maildir/tmp/1214251603.P24795.dokoupil.biz: Permission denied

Final-Recipient: rfc822; email@address
Original-Recipient: rfc822;email@address
Action: failed
Status: 5.2.0
Diagnostic-Code: X-Postfix; maildir delivery failed: create maildir file
   /home/jirka/Maildir/tmp/1214251603.P24795.dokoupil.biz: Permission denied
```

---

### Post by aos101 on 2008-06-23
Cool.  Glad it's working :)

---

