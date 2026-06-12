---
title: "can't access local emails using pop3 or imap"
date: 2011-03-01
forum: Server Platforms
---

### Post by freak4pc on 2011-03-01
Hey all :)

I used to have this setup on an old server and i'm trying to move it to a new server

I have a new box installed with Ubuntu 10.10, sendmail, courier-imap and courier-pop 

I've configured virtusertable/local-host-names/virtual-domains/sendmail.cf and such...

Everything is set up to take any mail arriving to @mydomain.com and move it to a user called "mobileinbox".

When i log in as mobileinbox (su mobileinbox) and check my inbox using mutt, i see all the e-mails , but when i login from the outside using pop3 or imap , it says i have no new emails.

This is what i get in mail.log when an email arrived:
```

Mar  1 14:12:51 ip-10-127-29-101 sm-mta[15549]: p21ECoYU015549: from=<test@gmail.com>, size=1745, class=0, nrcpts=1, msgid=<AANLkTimiJ6Szhx0DEkFqJRaJfk0inMp+Et51=ROP6zR3@mail.gmail.com>, proto=ESMTP, daemon=MTA, relay=mail-fx0-f44.google.com [209.85.161.44]

```

I'm sorry if its too scrambled, i'm just trying to get this solved for the past two hours and it really starts to get on my nerves :lolflag:

Would appreciate any help! :)
Thank you 

Shai.

---

### Post by freak4pc on 2011-03-01
Ok i just noticed that it is kinda scrambled to ill try to simplify

On the local machine when i login as "mobileinbox" and type mutt, i see the user's emails

When i login with an external pop3 client (such as mail2web.com) with the server and mobileinbox user, it says "no new messages" for some reason.

Could you assist, perhaps?

Thanks.

---

### Post by freak4pc on 2011-03-01
Solved by soft-linking /var/mail to the user's Maildir/cur

---

