---
title: "Ubuntu MailServer -&gt; How to set-up/configure a default maildir / POSTMASTER?"
date: 2008-10-21
forum: Server Platforms
---

### Post by amaturepro on 2008-10-21
Hi All,

I've followed the Ubuntu Community Guide on how to install/configure a mailserver ([LINK]("https://help.ubuntu.com/community/MailServer"))

I've got it working as detailed with currently just 2 users, one of these is the system admin (aka POSTMASTER) and I want to be able to send all mail that dosn't directly match a specified user, to this defualt mailbox...

Please can any tell me: **Where this needs to be configured? **better still **How to do it?**


Regards
aP

---

### Post by MJN on 2008-10-21
Simply add a [luser_relay]("http://www.postfix.org/postconf.5.html#luser_relay") directive in Postfix's main.cf to say who gets the catch-all (non-matched) mail e.g** luser_relay = ****postmaster**
 
Any help?
 
Mathew

---

### Post by amaturepro on 2008-10-22
Perfect - Thank you!



```
luser_relay = amaturepro
```

---

