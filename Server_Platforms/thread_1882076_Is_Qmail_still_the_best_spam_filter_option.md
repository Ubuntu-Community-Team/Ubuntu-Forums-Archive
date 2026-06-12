---
title: "Is Qmail still the best spam filter option?"
date: 2011-11-16
forum: Server Platforms
---

### Post by sentinelace on 2011-11-16
I have  qmail server that filters spam and then routes the mail to an exchange server.  This is all working great, however it misses a lot of spam.  I use blacklists, and John Simpsons scripts which help a ton with spamassassin.  It drops a ton but misses a ton.  Is qmail still the best option?  I like it because there are quite a few patches out there for it.  Or is there something bigger and better to configure to do a good job?

---

### Post by SeijiSensei on 2011-11-16
I use [MailScanner]("http://www.mailscanner.info/") with [ClamAV]("http://www.clamav.net/") for virus scanning and [SpamAssassin]("http://spamassassin.apache.org/") for spam tagging.  I've been scanning mail with this combination at a number of sites for at least half-a-dozen years now.

---

### Post by sentinelace on 2011-11-16
so mailscanner is the name of the mail server?  what about spf, valid recpt to addresses, and rbls?

---

### Post by SeijiSensei on 2011-11-17
MailScanner is a "wrapper" around an MTA like sendmail or Postfix.  Upon start up, it creates a listener instance of the MTA which accepts inbound messages and places them in a queue.  The MailScanner daemon periodically checks the queue, scans the message, and writes it to another outbound queue.  A second instance of the MTA delivers the messages in the outbound queue.

If you'd like to learn more about it, just visit the mailscanner.info site.  There's a lot of excellent documentation available there.

---

### Post by sentinelace on 2011-11-19
I was more curious about the patches.  I use qmail as a spam filter and then route the mail to my exchange server after it gets filtered, but it's getting out of date and missing spam.  Qmail is nice for all the custom patches it has.  Does this one have similar options?

---

### Post by SeijiSensei on 2011-11-19
MailScanner uses [SpamAssassin]("http://spamassassin.apache.org/") which is well-supported by the Apache Foundation and a lot of independent developers.  It's pretty much the gold standard for anti-spam processing.

---

### Post by sentinelace on 2011-11-19
What about spf? And validrccpto ?

---

### Post by SeijiSensei on 2011-11-19
C'mon.  Go read some documentation already.  Then come back and ask your questions.

---

### Post by sentinelace on 2011-11-24
I was reading through the docs but I don't see much mention of qmail.  Just postfix mainly.  Is qmail an option?

---

### Post by SeijiSensei on 2011-11-25
I can't answer that.  I generally use mainstream server software like sendmail and Postfix.  DJB seems like a bright guy, but his programs are less widely supported.  I also have a bit of trouble with his rather haughty attitude.

A quick Google search for "qmail mailscanner" turns up [this page]("http://qms.ausics.net/").

---

### Post by lisati on 2011-11-25
I hesitate to give all the anti-spam stuff I've done on my system, partly for security reasons but mostly because it has an element of overkill for the amount of email traffic I receieve. It's based around postfix, amavis-new, clamav, spamassassin, a couple of policy servers and some lists of restrictions populated by some home-grown scripts that analyse my system logs.

---

### Post by sentinelace on 2011-11-27
I'll do some testing with it on a VM, looks very popular

---

