---
title: "Done setting up postfix, how to receive mails?"
date: 2009-11-25
forum: Server Platforms
---

### Post by Zer0d on 2009-11-25
I have followed every step of this [guide]("https://help.ubuntu.com/9.10/serverguide/C/postfix.html") and my smtp server is up and going and I have tried to send mails to the mail address I made and mounted to a user account. My problem now is that I am not sure how I can check on my server if the user got the email I sent from the outside?

When running pingability.com it says:
```

Information	The mail server accepted email for 'abuse@jeant.com' email address as it should have (250 2.1.5 Ok).
Information	The mail server correctly rejected email to 'email_validation_service@domaincheckingservice.pingability.com' (554 5.7.1 <email_validation_service@domaincheckingservice.pingability.com>: Relay access denied)

```

I can use evolution to connect to the server? On the "Receiving Email" section what should I write on server type? IMAP, Exchange, Novell, POP... and so on.

I don't see IMAP running on a port when I scan myself, it should have it's own port?

---

### Post by Zer0d on 2009-11-25
I found out that I could use Local Delivery as Server Type. I am not sure which path to use though, reading some guide online says I should choose the spool path, not sure where that is?

---

### Post by Zer0d on 2009-11-25
The Maildir is in my user home folder and inside it I can find all the emails I have sent like this one:


```

Return-Path: <slashroot@hotmail.com>
X-Original-To: admin@jeant.com
Delivered-To: slashroot@mail.jeant.com
Received: from blu0-omc2-s24.blu0.hotmail.com (blu0-omc2-s24.blu0.hotmail.com [65.55.111.99])
	by mail.jeant.com (Postfix) with ESMTP id 0DFB9BE239
	for <admin@jeant.com>; Wed, 25 Nov 2009 15:32:43 +0100 (CET)
Received: from BLU129-W28 ([65.55.111.73]) by blu0-omc2-s24.blu0.hotmail.com with Microsoft SMTPSVC(6.0.3790.3959);
	 Wed, 25 Nov 2009 06:32:44 -0800
Message-ID: <BLU129-W289A314A96E7E080298F6FAC9C0@phx.gbl>
Content-Type: multipart/alternative;
	boundary="_bd70d98e-8a9c-4874-b5fd-2e6f12d01c42_"
X-Originating-IP: [85.165.149.130]
From: My Name <slashroot@hotmail.com>
To: <admin@jeant.com>
Subject: MX host setup test
Date: Wed, 25 Nov 2009 14:32:44 +0000
Importance: Normal
MIME-Version: 1.0
X-OriginalArrivalTime: 25 Nov 2009 14:32:44.0670 (UTC) FILETIME=[26EBC9E0:01CA6DDC]

--_bd70d98e-8a9c-4874-b5fd-2e6f12d01c42_
Content-Type: text/plain; charset="iso-8859-1"
Content-Transfer-Encoding: quoted-printable


MX host setup test 		 	   		 =20
_________________________________________________________________
Bing brings you maps=2C menus=2C and reviews organized in one place.
http://www.bing.com/search?q=3Drestaurants&form=3DMFESRP&publ=3DWLHMTAG&cre=
a=3DTEXT_MFESRP_Local_MapsMenu_Resturants_1x1=

--_bd70d98e-8a9c-4874-b5fd-2e6f12d01c42_
Content-Type: text/html; charset="iso-8859-1"
Content-Transfer-Encoding: quoted-printable

<html>
<head>
<style><!--
.hmmessage P
{
margin:0px=3B
padding:0px
}
body.hmmessage
{
font-size: 10pt=3B
font-family:Verdana
}
--></style>
</head>
<body class=3D'hmmessage'>
MX host setup test 		 	   		  <br /><hr />Bing brings you maps=2C menus=2C =
and reviews organized in one place. <a href=3D'http://www.bing.com/search?q=
=3Drestaurants&form=3DMFESRP&publ=3DWLHMTAG&crea=3DTEXT_MFESRP_Local_MapsMe=
nu_Resturants_1x1' target=3D'_new'>Try it now.</a></body>
</html>=

--_bd70d98e-8a9c-4874-b5fd-2e6f12d01c42_--

```

But I am not sure how to import them into an email client or receive them directly.

---

### Post by Zer0d on 2009-11-25
The files in the /home/user/Maildir/new looks like this:
1259158279.V801If20a6M215556.slashroot-server
1259159050.V801If20bbM455936.slashroot-server

I have tried setting Server Type to "Standard Unix mbox spool directory" and chose "new" as my path. Still not able to get the emails into Evolution.

---

### Post by Zer0d on 2009-11-25
Problem solved, it was pretty ridiculously obvious. I had to choose the Server Type called "Maildir-format mail directories".

---

