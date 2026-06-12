---
title: "Mail Server Problem: Outgoing Messages are Getting Spammed"
date: 2016-02-13
forum: Server Platforms
---

### Post by Amanda_Weysharre on 2016-02-13
Hi everyone!
I need to bulk message (or massmail) and I need a free mail server on Ubuntu to send messages. I installed Postfix and the smtp server did not work. Then I installed IredMail and after sending some emails, it failed to send more emails (probably because of sending policies which I couldn't change). Then I installed Mail-in-a-Box and again outgoing messages policy prevented me from sending more messages. Finally I went for Xeams and my outgoing messages got spammed. How can I manage this? What should I do in order for my outgoing messages not to get spammed in other mail servers?

Thank you all.

---

### Post by SeijiSensei on 2016-02-13
If you're running a server on a home connection, your messages will likely be tagged as spam because most residential machines sending mail are spambots.  Also your ISP may simply block outbound traffic on port 25 precisely to guard against those bots.

Try this test from a command prompt:
```
telnet gmail-smtp-in.l.google.com 25
```
Can you connect?

Also if you are on a residential connection, running servers is almost always banned by the Terms of Service you agreed to when signing up.  If you intend to do a lot of mailings, or if you need to guarantee delivery, you should consider renting a virtual server from someone like [Linode](http://www.linode.com/).  Not free, but at $10/month pretty affordable.

The other option is to sign up with a service like [ConstantContact]("http://www.constantcontact.com/index.jsp").

---

### Post by Amanda_Weysharre on 2016-02-14
Thank you! I've already bought a virtual server from DigitalOcean and the IP is not blacklisted. I could connect to Google with the command you suggested and ehlo-ing google worked...

---

### Post by SeijiSensei on 2016-02-14
Does the server have both forward and reverse DNS configured with identical hostnames? Do you have an SPF record for the domain pointing to the server? Did you run through the tests at mxtoolbox.com?

Maybe the messages look spammy. If you have a copy of spamassassin installed, use it to examine a message and see what it reports.

---

