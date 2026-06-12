---
title: "Postfix Routing Question"
date: 2010-12-30
forum: Server Platforms
---

### Post by Dramaturg on 2010-12-30
Hey,

I use Ubuntu 10.04 LTS.  How to manage the following situation:

There is server A (192.168.1.1) with DNS domain.com. (Pointed to Internet)

Server B has the IP 192.168.1.2 with second.com as DNS (Local)

People should use server B for accessing their e-mail-boxes (Cyrus) and send mails. This server handles Spam&Virus-protection.

But the actual server for sending and receiving  mails should be server A with the IP 192.168.1.1

How to solve this situation with Postfix and Cyrus?

I assume this is done by SMTP-Relays but I would like to hear your opinion on that.

---

### Post by stmiller on 2010-12-30
That is a pickle. I don't know if you would consider another configuration?

It is somewhat common to have a spam/virus scanning box as an mx record which then passes on to a mail server.

mx1.domain.com - spamassassin / clamav
mail.domain.com - mail server users connect to for send/receive of mail

---

### Post by Dramaturg on 2010-12-31
My intention is to make the mail-boxes more secure. If the attacker compromises the Postfix installation he can't get any access to the mail-boxes because they are on another server. 

Yes this would be also a good possibility! Can you tell me how to manage that?
I know how to change MX records I am just curios about the postfix/cyrus conf.

Nevertheless if there is some way to implement my original Idea - would be great!

---

### Post by stmiller on 2010-12-31
I see - if you are just concerned about security, all of this may be overkill and not necessarily make things any more secure.

You can store mail on an internal SAN. (/var/spool/mail) So that the actual email is not on the same mail.domain.com box. But that is pretty high-end and complex. And not necessarily more or less secure.

I wouldn't really worry about someone hacking postfix.

cheers,

---

