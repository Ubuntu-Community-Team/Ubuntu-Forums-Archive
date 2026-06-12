---
title: "Request: Remove telnet from ubuntu-standard"
date: 2007-03-29
forum: Server Platforms
---

### Post by tomplast on 2007-03-29
Would anyone please tell me why telnet is a part of the ubuntu-standard meta-package? AFAIK telnet is very dangerous (and unwise) to use so wouldn't it be better if we a user could install it later on if he/she desperately needed it.

What do you think? Should telnet be removed from ubuntu-standard meta-package?

---

### Post by PetePete on 2007-03-29
the actual service isn't installed just client.

the client can be very useful for connecting to random ports and seeing if they are open/ what they are.

one of the main reasons its considered dangerous is due to sending passwords in plain text, which doesnt really apply if you are just using it to probe ports.

---

### Post by tomplast on 2007-03-29
> **PetePete said:**
> the actual service isn't installed just client.

the client can be very useful for connecting to random ports and seeing if they are open/ what they are.

one of the main reasons its considered dangerous is due to sending passwords in plain text, which doesnt really apply if you are just using it to probe ports.

Yeah... I do agree with you, it's just that a server I was responsbible for got hacked so now I scream aloud as soon as unsafe things like telnet comes to mind. So I understand from you that telnet may be useful but how useful is it really? Is it really useful enough to be included in ubuntu-standard?

---

### Post by EmmEff on 2007-03-29
I dunno, I use telnet (client) regularly for checking POP3/IMAP/SMTP/HTTP servers...  guess it's not 100% necessary to be in ubuntu-standard, but I imagine most admins do install it for the same reason.

---

### Post by Nikron on 2007-03-29
> **EmmEff said:**
> I dunno, I use telnet (client) regularly for checking POP3/IMAP/SMTP/HTTP servers...  guess it's not 100% necessary to be in ubuntu-standard, but I imagine most admins do install it for the same reason.

Yeah, I found it to be very useful when setting up postfix/imap.

---

