---
title: "Postfix, Google, relay not allowed"
date: 2009-04-29
forum: Server Platforms
---

### Post by drhiii on 2009-04-29
Help.

Postfix/TLS/SASL, Ubuntu 9.04, is sending and receiving mail.  

I am able to sent mail TO a registered user on the server.  I am able to send mail FROM the server to the outside world.

However, I am not able to send a Reply to an email that is sent FROM the server to an outside account, like Gmail, and then Reply To the email and have it received back to the origination, meaning the original server.

The log below shows relay access denied.  Help anyone?  I don't understand how mail to and from works.  But a reply to mail from the original server, like to Gmail and then back, gets bounced with a relay message.  I could add a provision for Gmail I know, but there are mobile clients who will be using all flavors of ISPs, and I can see this problem blowing up.

Ideas????



Apr 28 23:43:36 mail postfix/smtpd[12261]: NOQUEUE: reject: RCPT from rv-out-0506.google.com[209.85.198.234]: 554 5.7.1 <gumbie@mail.myserver.com>: Relay access denied; from=<pokie@gmail.com> to=<gumbie@mail.myserver.com> proto=ESMTP helo=<rv-out-0506.google.com>

---

### Post by HermanAB on 2009-04-29
Howdy,

You either have to repair your DNS so that you have working A, PTR and MX records, or you have to relay mail through your ISP mail server, using the relayhost directive in main.cf.

---

### Post by drhiii on 2009-04-29
> **HermanAB said:**
> Howdy,

You either have to repair your DNS so that you have working A, PTR and MX records, or you have to relay mail through your ISP mail server, using the relayhost directive in main.cf.

I suspect it is DNS.  Can you point me to how to 'repair' the DNS. The primary and secondary were created in Webmin.  Felt it was done properly, but apparently not.

---

