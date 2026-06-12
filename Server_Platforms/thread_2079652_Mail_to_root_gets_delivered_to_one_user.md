---
title: "Mail to root gets delivered to one user"
date: 2012-11-02
forum: Server Platforms
---

### Post by yc2 on 2012-11-02
Hello,

I am changing the config for exim4 from local mail to also send/receive from remote domains.

One user told me that local mail for root gets delivered to one user instead. (I think they had that problem even before I started changing exim4 config.)

I listed /var/mail/MYUSER below. You can see that it has received a mail intended for root!
(MYUSER is the user receiving root's mail)

All mail in the machine is local so far.

What should be changed so that root get root's mail and root's mail should not be forwarded to MYUSER

Thanks



```
root@deb7:~# cat /var/mail/MYUSER
From Joe@MYDOMAIN.COM Fri Nov 02 11:04:02 2012
Return-path: <Joe@MYDOMAIN.COM>
Envelope-to: root@MYDOMAIN.COM
Delivery-date: Fri, 02 Nov 2012 11:04:02 +0100
Received: from Joe by deb7.pchemma with local (Exim 4.80)
        (envelope-from <Joe@MYDOMAIN.COM>)
        id 1TUE6c-0006yJ-EE
        for root@MYDOMAIN.COM; Fri, 02 Nov 2012 11:04:02 +0100
Date: Fri, 2 Nov 2012 11:04:02 +0100
From: Joe Doe <Joe@MYDOMAIN.COM>
To: root <root@MYDOMAIN.COM>
Subject: test mail to root
Message-ID: <20121102100401.GA26792@MYDOMAIN.COM>
MIME-Version: 1.0
Content-Type: text/plain; charset=us-ascii
Content-Disposition: inline
User-Agent: Mutt/1.5.21 (2010-09-15)
Status: O
Content-Length: 1
Lines: 1
```

---

### Post by darkod on 2012-11-02
I don't work with mail servers and this is just a soeculation: Is MYUSER the first user that was created during the install?

Don't forget that ubuntu doesn't use the root user and instead the first user created has sudo permissions. Since root can never log in, maybe the mail to root gets delivered to the first user (or another user). Makes sense?

---

### Post by yc2 on 2012-11-03
You are right about that Darko. It was the first user created.
The system was not set up by me, I will check further with the guy who did it. Right now he used aliases to forward all root mail to me :)
Thanks.

---

