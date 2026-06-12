---
title: "open source virus/spam software for ubuntu 9.04 mail server?"
date: 2009-11-20
forum: Server Platforms
---

### Post by kustomjs on 2009-11-20
Hey Guys
I just wanted to know if there was any virus/spam software out there for ubuntu 9.04 using postfix and dovecot? if so how do I configure it into my email server.

---

### Post by dca on 2009-11-20
Found this how-to for 8.04, I just realized you wrote 9.04 in your thread...  Sorry.
 
[http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu](http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu)
 
I would think any kind of combo of Spamassassin & ClamAV would do the job...

---

### Post by kustomjs on 2009-11-20
I also forgot to say that I was looking to see if there was any virus/spyware interface.

---

### Post by kustomjs on 2009-11-22
anybody?

---

### Post by Vegan on 2009-11-22
those earlier programs are the ones for a CLI, others need a desktop and are outside the server area.

---

### Post by Lars Noodén on 2009-11-22
Two worth mentioning are Spamassassin and ClamAV:

[http://spamassassin.apache.org/](http://spamassassin.apache.org/)

[http://www.clamav.net/](http://www.clamav.net/)

An additional method that will help a little with spam is known as [greylisting](http://manpages.ubuntu.com/manpages/hardy/man8/postgrey.8.html).  AFAIK, the other MTAs also support grey listing in one way or another.

Keep in mind that these are both corrective measures and subject to the shortcomings inherent in corrective acction.

e.g. Spamassassin does not address the source of spam.  To do that, a group or company or agency would need to :

1. collect contact information for products peddled via spam
2. trace through credit card or other payment information to bank account
3. trace from bank account to perpetrator's front company
4. trace from front company to perpetrators
5. prosecute perpetrators

It's a little late in the game.  A few people did that with good effect, but it did not get buy-in from governments or even decision makers.

Spamassassin does  not address the cause of spam either.  However, deploying Ubuntu or any other FOSS operating system does address that cause directly.

---

### Post by kewlrichie on 2009-11-25
I use the same method in the howtoforge link posted above. It uses amavisd-new which works very well and I also installed webmin with the clamav module and you are able to see quarantined items virus, banned, spam and bad mail headers. I followed the guide for 8.10 and but used it on a 9.04.

---

