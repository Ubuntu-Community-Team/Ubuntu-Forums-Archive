---
title: "Need a software that can send X email's per hour"
date: 2009-07-29
forum: The Cafe
---

### Post by BOBSONATOR on 2009-07-29
Hey guys, long time no talk, but I need a software (preferably windows yea i know shoot me)That can send many emails (over 2000) yet send an amount of emails per hour. & it needs to be able to BCC (blind carbon copy)

Anyone know of a quick fix? 

Thanks in Advance.
:D

---

### Post by Tristam Green on 2009-07-29
a...spam....program?

:-k

---

### Post by BOBSONATOR on 2009-07-29
Its for work, a client list in particular. Thanks

---

### Post by wojox on 2009-07-29
PHP and a nice for loop.

---

### Post by MaxIBoy on 2009-07-29
One might hack that together in Python in a half hour, depending on what kind of email address you'd be sending from, plus a few other variables.

Do you have your own mail server? If so (or especially if not so) could the mailserver handle this kind of traffic? Would these emails be plaintext or formatted, with attachments or without?

---

### Post by BOBSONATOR on 2009-07-29
> **MaxIBoy said:**
> One might hack that together in Python in a half hour, depending on what kind of email address you'd be sending from, plus a few other variables.

Do you have your own mail server? If so (or especially if not so) could the mailserver handle this kind of traffic? Would these emails be plaintext or formatted, with attachments or without?

Yes we have our own mail server, yet our host has a 150 email per hour limit. 

& Its just plain HTML no attachments,

Thanks.

---

### Post by JT9161 on 2009-07-29
Sounds scriptable

---

### Post by MaxIBoy on 2009-07-29
> **BOBSONATOR said:**
> Yes we have our own mail server, yet our host has a 150 email per hour limit. 

& Its just plain HTML no attachments,

Thanks.
If you're capped at 150 per hour, I don't know that there's much you can do about it.

But Python (the programming language) has built-in utilities for connecting to mailservers via POP3 and so on, so you'd just need an elegant way of keeping track of your "send to" list in a file, and you're looking at maybe twenty lines of code.

---

### Post by Crunchy the Headcrab on 2009-07-29
> **MaxIBoy said:**
> If you're capped at 150 per hour, I don't know that there's much you can do about it.


That's obviously why he only wants to send a certain amount per hour.

---

### Post by koenn on 2009-07-29
> **JT9161 said:**
> Sounds scriptable
it is

[http://users.telenet.be/mydotcom/program/vbs/massmail.htm](http://users.telenet.be/mydotcom/program/vbs/massmail.htm)



+ for the hour limit, just add a counter and keep track of the time

---

### Post by MaxIBoy on 2009-07-29
> **Crunchy the Headcrab said:**
> That's obviously why he only wants to send a certain amount per hour.
*Reviews original post*

Whoops, I thought he meant that he wanted to send over 2000 emails per hour, honest misunderstanding.

---

### Post by thisllub on 2009-07-30
I had a RedHat 6 Hylafax server that could send up to 600 faxes per hour through an 8 port fax card.

A proper mail server (e.g. Zimbra) should work fine.
Alternatively any number of scripting alternatives exist.

---

