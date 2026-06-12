---
title: "where to ask"
date: 2013-02-14
forum: Server Platforms
---

### Post by tinsleyrd on 2013-02-14
I'm somewhat new to linux / ubuntu and am trying to do a proof of concept.

I have installed a ubuntu server and installed postfix on it.  The intent is to operate as a local (no internet) mail service.

I can successfully send and receive emails as long as I log onto the server.

I'm trying to use Thunderbird on a windows machine on the same local network to retrieve mail, but I am unsuccessful.

My searches have not come up with this exact configuration, and I'm afraid the example differences are causing me confusion.

My question is this:  Where would I look for an answer?  Ubuntu, postfix, or Thunderbird.  I think I've tried them all.

Thank you for any direction.

---

### Post by howefield on 2013-02-14
Thread moved to the "*Server Platforms*" forum.

---

### Post by spynappels on 2013-02-14
Look at installing a POP/IMAP server too. Courier is a good place to start looking.

Thunderbird will connect to the POP/IMAP server (IMAP is my preferred option) and the POP/IMAP server will get the mail from Postfix.

I found the following site to be very helpful when I was doing this a few months ago:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
Adjust to suit your use-case.

---

### Post by tinsleyrd on 2013-02-18
Thanks for the help.

fwiw:

I replaced mbox with Maildir

I replaced dovecot with courier

Thunderbird had its own configuration issues, but finally got it all to work.

I'm sure a small step for the wise, but for me - a big success

---

### Post by spynappels on 2013-02-19
Great, glad you got it working. Very satisfying, isn't it?

---

### Post by tinsleyrd on 2013-02-21
> **spynappels said:**
> Great, glad you got it working. Very satisfying, isn't it?

Now if I can only get MantisBT to play. :)

---

