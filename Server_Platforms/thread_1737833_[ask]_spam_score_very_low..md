---
title: "[ask] spam score very low."
date: 2011-04-23
forum: Server Platforms
---

### Post by venol on 2011-04-23
helo, does Postfix need to use Bayes and send sample email to learn by spamassassin if it combined with amavisd. because I try to send a sample spam message (in addition to gtube) score for that email spam is still low, only 1.0.

---

### Post by SeijiSensei on 2011-04-24
SA comes with a broad variety of rules by default.  In fact, I wouldn't use Bayes until you've built up a substantial corpus of "ham" and "spam" that you can use to train the Bayes system.

I'm not sure how you're sending this message to SA.  It will apply different rules to messages originating locally as compared to ones coming from outside.

The best way to see how SA will handle test messages is to run it from the command line like this:

```
spamassassin -t < example.txt
```

where example.txt is the message you wish to test. (If you want a very detailed listing of what SA is doing, add the "-D" switch to turn on debugging.)  

Make sure the test message you use includes all the headers as well.  That's where a lot of the juicy bits appear.  The very first line of the test message should contain the "Return-Path:" header.  If you don't have a Return-Path and all the Received headers, you'll need to tell your email client to display the entire message source and copy that into the test file.

---

### Post by venol on 2011-04-24
thanks for reply. I send sample spam message from outside network to my mail server, and then I test score the email with "spamaassassin -t < Maildir/cur/1300059639.V801I2808fcM169355.venom.com\:2\,S" like your instructions. But, the score still low.

what does I must to use bayes to training email spam and ham?

---

### Post by SeijiSensei on 2011-04-24
> **venol said:**
> But, the score still low.

What scores did you get back from the testing?  Did it detect all the spammy features that you think it should have?  If you get spam messages that SA doesn't detect, you'll need to write your own rules in /etc/mail/spamassassin.  I've written dozens of rules over the years; most mail admins using SA have as well.

Take a look at: [http://wiki.apache.org/spamassassin/UsingSpamAssassin](http://wiki.apache.org/spamassassin/UsingSpamAssassin)

> what does I must to use bayes to training email spam and ham?

[http://wiki.apache.org/spamassassin/BayesInSpamAssassin](http://wiki.apache.org/spamassassin/BayesInSpamAssassin)

---

