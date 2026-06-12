---
title: "postfix outbound"
date: 2007-02-07
forum: Server Platforms
---

### Post by reckless2k2 on 2007-02-07
I set up Postfix using the following tutorial:

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

After the setup was complete, I can send and receive mail from inside webmin on that local box. Unfortunately, I can not send mail to a domain outside of my box for a mailbox inside my domain. ie. [email]user@mydomain.com[/email] to [email]user@gmail.com[/email].

Also, from another machines on my domain, I can not pop/imap the mail to that local machine ie. machine1.localdomain pop mail down from server.mydomain.com.

I'm sure the sending mail outside of my domain is a simple tweak I missed. I'm not sure about the other. I followed that tutorial to the letter replacing "yourdomain" with mine.

(my local server is named mail.mydomain.com. should it be server.mydomain.com? I don't know if that's conflicting with incoming/outgoing up to no-ip.com where my host name redriect is. i did redirect mail.mydomain.com to my IP on no-ip.com.)

Thanks.

---

### Post by reckless2k2 on 2007-02-07
Any one? Any one?

---

### Post by MJN on 2007-02-08
Post your config and logs as all the batteries from our crystal balls are flat! ;)
 
Mathew

---

