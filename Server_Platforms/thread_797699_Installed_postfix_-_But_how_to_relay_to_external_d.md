---
title: "Installed postfix - But how to relay to external domains via outlook?"
date: 2008-05-17
forum: Server Platforms
---

### Post by Georgecooldude on 2008-05-17
I've installed postfix and its setup according to the below documentation

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

I can relay from the server console to hotmail fine. From outlook I can relay to mydomain.com without any issues. From outlook though as soon as I try and relay to an external address eg, hotmail, gmail etc I get a message bounce back saying "Relay access denied".

Googleing it looks as though I need to enable SMTP AUTH but I haven't come accross a decent guide that works with my virtual user setup. Can anyone suggest a good guide or list the steps I need to take so that I can relay via my server using username/password authentication? Anonymous open relay has to be disabled to stop spammers abusing my server. I'm using ubuntu server cli 6.

---

### Post by solcott on 2008-05-17
I acutally just posted this link in another post about five seconds ago.  Follow it and it will work :-)
[http://gaming.gwos.org/doku.php/udsf:serverguide#postfix](http://gaming.gwos.org/doku.php/udsf:serverguide#postfix)

---

