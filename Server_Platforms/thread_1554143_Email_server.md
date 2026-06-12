---
title: "Email server"
date: 2010-08-16
forum: Server Platforms
---

### Post by HS-L on 2010-08-16
Hi,

I've got a mail server for myself, and a couple of other people (family & friends).

What I have now:
- postfix
- spam assassin
- dovecot
- I arrange all the addresses with postfix/virtual manually 

But it's not a very stable (and easy to maintain) solution So I'm busy starting all-over with the complete mailsystem.

I'm thinking about:
- postfix
- dovecot
- postfixadmin

But the postfixadmin interface is not really "modern" do you know if there's a better alternative?

Thanks!

---

### Post by cdenley on 2010-08-16
> **HS-L said:**
> But the postfixadmin interface is not really "modern" do you know if there's a better alternative?

Just use zimbra. Last I checked it doesn't support 10.04 yet, though, so you would have to use 8.04.

---

### Post by noway2 on 2010-08-16
If I may ask, what are you looking for in a "modern" interface?  Also, what problems are you experiencing that you say you don't have a stable solution?

How many users are you trying to support?

Postfixadmin, while not exactly a sexy program is quite easy to use and gets the job done.  If you aren't planning on having a large number of changing user accounts I would think that it would be a set it up and forget about it situation.

---

### Post by longvnit on 2010-08-17
You can try [www.**iredmail**.org]("http://ubuntuforums.org/www.iredmail.org") is opensource email server solution and free.
It's very easy install.

---

### Post by LightningCrash on 2010-08-17
I've done MySQL-based Exim / Qpopper / SpamAssassin / Clamav / Amavis combos in the past with great success.

There's even a pretty standard GUI called "mbeqwa" for account management on that combo... you'll have to edit the source a bit, as it was done in php_register_globals and your MySQL table structure might be a bit different. But all in all it only took two hours to fix everything.

Good howto here:
[http://devel.reinikainen.net/32](http://devel.reinikainen.net/32)

---

