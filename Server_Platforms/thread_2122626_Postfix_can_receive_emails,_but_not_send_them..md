---
title: "Postfix can receive emails, but not send them."
date: 2013-03-05
forum: Server Platforms
---

### Post by cthugha on 2013-03-05
Hi,

I recently used this guide: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
to set up a postfix mail server. I've got it to receive emails at my domain from gmail, but I can't send them from my domain to gmail.

Does anyone have any ideas what could be causing this issue?

Here are some things in the mail queue:
```

B02802A024E      446 Tue Mar  5 16:09:50  [EMAIL="me@mydomain.com"]me@mydomain.com[/EMAIL]
(connect to alt2.gmail-smtp-in.l.google.com[74.125.131.26]:25: Connection timed out)
                                         [EMAIL="me@gmail.com"]me@gmail.com[/EMAIL]


999D42A03AF      373 Tue Mar  5 16:56:07  [EMAIL="me@mydomain.com"]me@mydomain.com[/EMAIL]
    (connect to mta5.am0.yahoodns.net[66.196.118.34]:25: Connection timed out)
                                         [EMAIL="me@yahoo.com"]me@yahoo.com[/EMAIL]

```

---

### Post by SeijiSensei on 2013-03-05
Is this a server on a residential connection?  If so, the most likely explanation is that your ISP is blocking outbound SMTP connections in an effort to control spambots.  Ask your ISP.  If that's not the reason, we'll move on to other possibilities.

It's also possible that your Terms of Service forbid running servers which is a pretty common policy in most residential Internet contracts.  Read your ToS before calling the ISP.

---

### Post by cthugha on 2013-03-05
Damn, it is blocked outbound. Gorram spammers.

---

### Post by GordThompson on 2013-03-06
You may not be completely stymied. Many residential ISPs will block outbound connections on port 25 to any SMTP server *other than their own*. So, you might still be able to use your mail server once you've told it to route all outbound mail through your ISP's SMTP server (Postfix apparently calls this a "remotehost", other folks call it a "smarthost").

---

### Post by cthugha on 2013-03-07
That did it. Thanks, man.

---

