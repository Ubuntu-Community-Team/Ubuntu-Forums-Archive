---
title: "Mail Sever"
date: 2008-04-10
forum: Server Platforms
---

### Post by justinwhite on 2008-04-10
What email server do you suggest I install, and how do I approach it?

---

### Post by Koybe on 2008-04-10
I think postfix is a powerful and simple one. But it highly depends on what you intend to do with it.

---

### Post by HermanAB on 2008-04-10
[http://citadel.org](http://citadel.org)

Nuff sed.

---

### Post by Dr Small on 2008-04-10
What exactly do you plan to do with it?
I use Postfix.

---

### Post by hyper_ch on 2008-04-11
postfix +1

---

### Post by songshu on 2008-04-11
i have nothing bad to say about any other mailing solution

but on my part its:
postfix for the smtp part
dovecot for the imap mailboxes
roundcube as the webmail

---

### Post by justinwhite on 2008-04-11
I just need something to receive and send emails.

---

### Post by hyper_ch on 2008-04-11
receiving / sending emails:  postfix

local filtering and distributing into maildirs: procmail

pop3/imap server: courier

webmail: squirrelmail ^^

---

### Post by justinwhite on 2008-04-11
Would happen to have any guides/tutorials for successfully setting these up?

---

### Post by songshu on 2008-04-12
there are plenty of guidelines available, but none is perfect or definite,
because its just what you want to make of it,

what do you intend to do? do you want pop3 or imap, or both?
do you want shared calendar, addressbook  and stuff?

---

### Post by hyper_ch on 2008-04-12
there's a guide for setting up an isp-like server over at [http://www.howtoforge.com](http://www.howtoforge.com) (Perfect Ubuntu/Debian Server Howto)

---

