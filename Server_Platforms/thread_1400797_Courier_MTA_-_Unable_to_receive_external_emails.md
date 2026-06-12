---
title: "Courier MTA - Unable to receive external emails"
date: 2010-02-07
forum: Server Platforms
---

### Post by chinnermooore on 2010-02-07
Hi,

I've recently set up Courier MTA and SpamAssasin on Ubuntu 9.04 Server as per [https://help.ubuntu.com/community/MailServerCourierSpamAssassin](https://help.ubuntu.com/community/MailServerCourierSpamAssassin).  At present I'm only using the default generated SSL cert, I'm waiting until I can receive emails before obtaining one from a CA, however..

I'm able to send emails externally via SqWebMail, but I'm not able to receive any emails sent from a different server (eg [email]user@yahoo.com[/email]).  The sender receives a failure notice:

<ipaddress> does not like recipient.
Remote host said: 513 Relaying denied.

In the mail.log I see:

Feb  7 16:00:45 <hostname> courieresmtpd: started,ip=[::ffff:<external mailserver ip address>]
Feb  7 16:00:53 <hostname> courieresmtpd: error,relay=::ffff:<external mailserver ip address>,from=<user@yahoo.com>,to=<myuser@myhost.com>: 513 Relaying denied.

I don't know if it's relevant but in the example above <hostname> is the old name of my server as I've renamed it, don't know if that has any bearing on the issue.. 

I've had a hunt around and don't seem to be able to find any clues?

Would someone be able to help me diagnose the problem?

Kind regards
Ian

---

