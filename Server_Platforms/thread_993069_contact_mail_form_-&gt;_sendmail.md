---
title: "contact mail form -&gt; sendmail?"
date: 2008-11-25
forum: Server Platforms
---

### Post by nicem88 on 2008-11-25
hi @all

i'm looking for a mta which is able to send mails from a php mail form. i've installed sendmail and it works fine, but there are hundrets of functions, etc.
for e security reasons (spam...) i try to find a easy and small solution for ubuntu server.

any recommendations? 

just to say, i am not well schooled in mailservers, so hope anyone can help me to build up a "secure" solution.

thanks

---

### Post by Dr Small on 2008-11-25
Postfix should do what you want. As long as you don't set it up to receive connections for SMTP outside of localhost (or your network) you should be fine.

Here is the guide for Postfix:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by MJN on 2008-11-26
If all you require is outgoing mail, and your ISP provides mail servers, then have a look at Nullmailer. It's as simple as it gets and is designed purely to relay outgoing mail via a 3rd part server.
 
Search these forums for it as it is widely used for exactly your purposes.
 
Mathew

---

### Post by nicem88 on 2008-11-26
okay, thanks a lot. i'll have a look at postfix and nullmailer. now i've recognised that everything is easier than sendmail. ;)

---

### Post by nicem88 on 2008-11-26
mathew: as a secound remark: jap, just outgoing mail and also just to one single mailserver. is it also possible to use nullmailer in this case?

regards
nic

---

### Post by MJN on 2008-11-26
> **nicem88 said:**
> mathew: as a secound remark: jap, just outgoing mail and also just to one single mailserver. is it also possible to use nullmailer in this case?Can you rephrase your question? I'm not sure I fully understand the situation you're describing.
 
Nullmailer acts as a a very simple mechanism for SMTP clients to send out mail. In this sense it is effectively a binary-compatible alternative to Sendmail (and Postfix) but only providing outbound e-mail.
 
Rather than take on the task of mail delivery (e.g. performing MX lookups, connecting to the responsible mail server and submitting mail) it relays it to a 3rd party - usually this would be your ISP's mail server - and lets it take on the responsibility of onward delivery.
 
Mathew

---

