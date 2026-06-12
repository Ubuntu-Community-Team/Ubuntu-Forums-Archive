---
title: "Spam from my hotmail account"
date: 2009-03-25
forum: Security
---

### Post by ogger on 2009-03-25
I am sending out spam from my hotmail account. I run firestarter, and tested from viruses with Avast and AVG, but nothing. 

How can I stop this?

---

### Post by bodhi.zazen on 2009-03-25
Did you contact hotmail ?

---

### Post by mdebusk on 2009-03-25
> **ogger said:**
> I am sending out spam from my hotmail account.

Probably not. Far more likely is a spammer who is putting your hotmail.com e-mail address in his From: line.

> How can I stop this?

Short of hunting the spammer down and beating him to death with a baseball bat, you can't.

---

### Post by kpatz on 2009-03-25
If you have a copy of one of the spam messages, look at the Received: headers.  Chances are you'll see an IP address that has nothing to do with you.

Spammers steal addresses not only to send spam to, but to send spam FROM as well.

Actually, just the first two words of the above sentence are all that's needed to be said.  "Spammers steal".

That said, a baseball bat is way too kind a method of killing a spammer.  I'd use something a bit more, should I say, vicious?

---

### Post by mdebusk on 2009-03-25
> **kpatz said:**
> That said, a baseball bat is way too kind a method of killing a spammer.  I'd use something a bit more, should I say, vicious?

A couple or so years ago, I noticed a sudden and dramatic drop in the amount of spam I was receiving. About a week later, I saw a news article about a spammer in (IIRC) Europe who had been found dead in his home... beaten to death with a bat.

In other words, it's a known-good solution.

---

### Post by lswartz on 2009-03-25
We had a similar problem on 3/9/09 at 8:30 AM. It sent emails to everyone in our online address book a shopping site link. It looked like it was sent from us but there was no record left in sent mail. There were so many sent out that it locked our email account. When we were able to get in that evening we found a lot had been returned as mail daemons. I spent the day checking  5 computers & found nothing. Looks like they got in to the hotmail server to me.

We received no answer from hotmail.

---

### Post by albandy on 2009-03-25
if you used services like tell me who is banning me and **** like that, they may have your password, change it, but this not will ensure nothing only your security.

A simply telnet to port 25 of an smtp server can be enoguht to demonstrate how easy is to make fake mails

for example:
telnet myismpmail 25
Helo myip
smtp from: [email]thisisspam@hotmail.com[/email]
rcpt to: user@myispdomain
data
subject: this is spam
.
quit

---

