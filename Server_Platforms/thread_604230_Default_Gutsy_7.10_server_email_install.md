---
title: "Default Gutsy 7.10 server email install?"
date: 2007-11-05
forum: Server Platforms
---

### Post by Chip on 2007-11-05
Is there a document somewhere that states what ACTUALLY gets installed if you just pick email along with LAMP in the Gutsy 7.10 server CD install? The doc on server stuff seems to be at 6.06LTS and all these HOWTOs seem to be talking about packages that didn't get installed on my machine. Postfix seems to be there, as well as dovecot. Half of the SSAL stuff seemed to be there.

I had a email in my var/mail/ directory so I guess it setup an mbox format. I tried going through the postfix setup as outlined in:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
It looks like it works but when I go to log in it just keeps asking for passwords over and over. Then at the bottom of [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
it implies that perhaps Cyrus SASL was what this was targeted for and not Dovecot.

The document says that it has been tested on Gutsy.

I'd blow the whole hard disk away and start over with the CD but I still don't know what you get by default? Where might that information be?

Thanks. - Chip

---

