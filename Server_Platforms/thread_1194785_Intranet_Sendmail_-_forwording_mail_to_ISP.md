---
title: "Intranet Sendmail - forwording mail to ISP"
date: 2009-06-23
forum: Server Platforms
---

### Post by kselva on 2009-06-23
Hai,
I have configured a intranet mail server for a domain like **testsite.com** in my LAN and this domain is hosted in a (internet) server **testisp.com** which runs my domain **testsite.com** as a vitualhost in exim.My LAN clients are using intrantnet mail server so if mail is send for a testsite.com then mail is relayed locally.

       Now the issue is some of our office empolyees who have mailids in domain testsite.com are out side of our LAN and not able to use intranet server,so if our office employess inside LAN are sending mail to those are outside the LAN then it stored locally and not send to the main server hosted in **testisp.com**.How can i forward mail to **testisp.com** for certain mailids ?
 
   Thanks in advance...

---

### Post by windependence on 2009-06-23
Huh???

Why don't you just set up a real mail server for the domain and let them all use it. I can't even fiure out what you're trying to do.

-Tim

---

### Post by kselva on 2009-06-23
Considering the no.of mail and bandwidth we setup local maiserver....

Issue in  simplfied : In sendmail i want to forword mail for cretain mailids to another server

---

### Post by windependence on 2009-06-23
Ah, OK, now I understand :-)

Postfix would be a much better way to do this, and it's a drop in replacement for sendmail. Sendmail is nasty to configure and I can't help you there, but I may be able to help you with Postfix relaying.

-Tim

---

