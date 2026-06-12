---
title: "Email Gateway with OpenPGP/SMIME encryption/decryption?"
date: 2006-07-18
forum: Server Platforms
---

### Post by GrammatonCleric on 2006-07-18
[FONT=Verdana][SIZE=2]Is there an Open Source Email encryption/decryption gateway out there?  Working in the Banking Industry (a small Banking Company in the US) we are now mandated to start encrypting email.   We've started  looking at some the "recommended" options, which I'm sure are great if you are HUGE bank, [/SIZE][/FONT][FONT=Verdana][SIZE=2] but  we [/SIZE][/FONT][FONT=Verdana][SIZE=2]can't  justify the costs.   It's not the appliances pre say that expensive it the yearly services fees  (i.e. P[/SIZE][/FONT][FONT=Verdana][SIZE=2]ostini $20,000/year for basic one way service) that are  hard pills to swallow.   We currently use a linux based email gateway to filter all in and outbound email for viruses, spam, etc. which works great!  It would nice to add the encryption/decryption option on top of our current gateway.

I know someone out there will say just use PGP on the desktops.  I'd love to!  But...it's hard enough to get most users to quit refering to their PC Desktop backgrounds as Screensavers let alone trying to get them to use PGP for mail and trust that they will use it and correctly as well.

Well any information about open source solutions would be greatly welcome....

Thanks!

[/SIZE][/FONT]

---

### Post by nkr1ptd on 2006-09-27
I am working on a post right now of how to setup your very own email gateway.  The one piece I am still working on is the ecrypted email part.  While tihs really should be no big deal as I am using postfix and you can easily send via TLS.  As far as PGP or GPG I am not sure, but hopefully once I post the article someone will add the additional features.  

Good luck,

-brandon


> **GrammatonCleric said:**
> [FONT=Verdana][SIZE=2]Is there an Open Source Email encryption/decryption gateway out there?  Working in the Banking Industry (a small Banking Company in the US) we are now mandated to start encrypting email.   We've started  looking at some the "recommended" options, which I'm sure are great if you are HUGE bank, [/SIZE][/FONT][FONT=Verdana][SIZE=2] but  we [/SIZE][/FONT][FONT=Verdana][SIZE=2]can't  justify the costs.   It's not the appliances pre say that expensive it the yearly services fees  (i.e. P[/SIZE][/FONT][FONT=Verdana][SIZE=2]ostini $20,000/year for basic one way service) that are  hard pills to swallow.   We currently use a linux based email gateway to filter all in and outbound email for viruses, spam, etc. which works great!  It would nice to add the encryption/decryption option on top of our current gateway.

I know someone out there will say just use PGP on the desktops.  I'd love to!  But...it's hard enough to get most users to quit refering to their PC Desktop backgrounds as Screensavers let alone trying to get them to use PGP for mail and trust that they will use it and correctly as well.

Well any information about open source solutions would be greatly welcome....

Thanks!

[/SIZE][/FONT]

---

### Post by jallen13 on 2008-05-06
I have an identical scenario.  A bank we service has been using Linux based email server (exim) for years, and an Exchange/Lotus solution just to have encryped email is not a good fit for us.

Have you found anything out?

---

