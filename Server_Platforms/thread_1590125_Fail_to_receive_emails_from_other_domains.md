---
title: "Fail to receive emails from other domains"
date: 2010-10-07
forum: Server Platforms
---

### Post by Emilio González Montaña on 2010-10-07
My email server (Postfix + Courier + virtual dropboxes) can receive internal emails, but if the email is sent from the exterior (like Gmail or Hotmail) this email is returned to the 3º provider (like Gmail):
[INDENT][FONT=Courier New]Delivery to the following recipient failed permanently:

     _xxxx@xxxxxxx.xxx_

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the  recipient domain. We recommend contacting the other email provider for  further information about the cause of this error. The error that the  other server returned was: 550 550 sorry, no mailbox here by that name  (#5.1.1) (state 14).

----- Original message -----

MIME-Version: 1.0

[/FONT][/INDENT][FONT=Verdana]I've tried a lot of things, I've used this guide:
[/FONT][INDENT][FONT=Verdana]http://flurdy.com/docs/postfix/[/FONT]
[/INDENT][FONT=Verdana]My Ubuntu Server is 10.4 (Lucid), I had the same configuration with a previous Ubuntu version and everything was right.

[/FONT]

---

### Post by SeijiSensei on 2010-10-07
Does your ISP allow you to run servers?  Have they blocked port 25 by default?

---

