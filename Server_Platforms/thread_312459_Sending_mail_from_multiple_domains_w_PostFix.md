---
title: "Sending mail from multiple domains w/ PostFix?"
date: 2006-12-04
forum: Server Platforms
---

### Post by tkambler on 2006-12-04
I have two domains hosted on my server:

domain1.com

domain2.com

Currently, I have postfix's "myorigin" variable set to: domain1.com

Both domains use PHP scripts to send outgoing mail. The only problem is, when I send e-mail from domain2.com, the headers for that e-mail indicate that it comes from "domain1.com". That's fine, but it's causing some spam problems. Not everyone is able to receive those messages.

Is there a way I can setup PostFix to send e-mail from multiple domains that would fix this issue?

Thanks!

Tim

---

### Post by tkambler on 2006-12-04
OK, apparently I'm a dope. I believe I've figured out my problem...

The problem was really more of a client problem instead of a server problem. The PHP script I was using (phpmailer) allows you to designate the originating server, like this:

$mail->Host = domain1.com;

Thanks.

---

