---
title: "[SOLVED] Postfix keeps sending mail after it times out."
date: 2008-10-26
forum: Server Platforms
---

### Post by bbmatrix on 2008-10-26
I sent an email via the command line to gmail to test postfix smtp. I forgot my isp blocks port 25. Postfix keeps trying again and again to send it. How do I stop it?](*,)

---

### Post by MJN on 2008-10-26
It'll eventually time out of its own accord, however to put it out of its misery...

Run the following to show the queue contents:

```
sudo postqueue -p
```...followed by:

```
sudo postsuper -d <ID of message>
```...to remove the offending message(s).

Mathew

---

### Post by bbmatrix on 2008-10-26
Thanks MJN! One more question. What part of this read out in /var/log/mail.log is the message ID?

Oct 26 09:42:15 server1 postfix/smtp[8402]: DA3B019E2D7: to=<bbmatrix@gmail.com>, relay=none, delay=64211, delays=64060/0.01/151/0, dsn=4.4.1, status=deferred (connect to alt1.gmail-smtp-in.l.google.com[209.85.143.114]:25: Connection timed out)
Oct 26 09:42:15 server1 postfix/smtp[8403]: DDA8B19E2E3: to=<bbmatrix@gmail.com>, relay=none, delay=63955, delays=63804/0.01/151/0, dsn=4.4.1, status=deferred (connect to alt1.gmail-smtp-in.l.google.com[209.85.143.27]:25: Connection timed out)

---

### Post by MJN on 2008-10-27
DA3B019E2D7 and DDA8B19E2E3.
 
They should be showing up in the queue contents output, no?
 
Mathew

---

### Post by bbmatrix on 2008-11-01
Thanks for all your help MJN. Solved it. :D

---

