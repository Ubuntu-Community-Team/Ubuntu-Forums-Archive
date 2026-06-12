---
title: "Spamassassin Issues Heeeeelllp"
date: 2008-12-10
forum: Server Platforms
---

### Post by Mucker212 on 2008-12-10
I thought I had setup spamassassin properly. Most my emails where coming in with (Spam ****22.3*****) Ratings on them. Now I set postfix to drop anything over 15* Rating.

Ive noticed that alot of spam arnt geting marked when they come through diffeernt email address's I have on my server.

Is there any way to check if spamassassin is checking all my emails on all my domains?

I have a Dedicated Un managed server which I have total control over.

Please help

Thanks

---

### Post by Mucker212 on 2008-12-13
Ok, I now know that it is checking all the emails, just that spamassassin needs training.

Does anyone know How I can train spamassassin without webmail?

I only have pop3 coming into my Outlook account and have a lot of unmarked spam in my junk folder I want to train spamassassin with.

Any help appreciated.


Thanks

---

### Post by sergevn on 2008-12-14
To train spamassasin you can do the following:

Create a separate mailbox, put all your spam there.
Mail need to be on the server.

sa-learn --spam *emailfile(s)*        this learns spamassasin the mails as spam
sa-learn --ham  *emailfile(s)*                            this learns spamassasin that it's NOT spam.

---

### Post by Mucker212 on 2008-12-14
My problem is, where do I store the spam on server. How do I get it back on there. Wont it say came from my junk mail folder in outlook?

---

