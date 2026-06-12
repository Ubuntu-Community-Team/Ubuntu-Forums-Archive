---
title: "Postfix, Cyrus and SASLauthd problems"
date: 2010-02-23
forum: Server Platforms
---

### Post by Nizumzen on 2010-02-23
Right, I've read the following guides:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[https://help.ubuntu.com/community/Cyrus](https://help.ubuntu.com/community/Cyrus)

and have followed them to the letter. The problem comes in the "Mailbox creation" section of the Cyrus guide. I run the saslpasswd2 and passwd commands successfully but when I try and login using cyradm it gives the following error message:

> Login failed: generic failure at /usr/lib/perl5/Cyrus/IMAP/Admin.pm line 119
cyradm: cannot authenticate to server with login as cyrus

the mail.err file contains the following error:

> Feb 23 12:37:57 messerschmitt postfix/postalias[1664]: fatal: open /etc/aliases.db: Permission denied

the mail.info file contains the following message:

> Feb 23 14:22:56 messerschmitt cyrus/imap[1567]: badlogin: localhost [::1] plaintext cyrus SASL(-1): generic failure: checkpass failed

I've Googled for hours on this and while there are lots of posts relating to this error, none of the proposed solutions seems to work. Does anyone have any ideas at all?

Thanks.

---

### Post by luxurious on 2011-01-17
Hey,

I'm having the same problem right now. Did you figure out what the problem was?

Regards

---

