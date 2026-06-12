---
title: "Configure Postfix as mail relay not MDA"
date: 2017-02-28
forum: Server Platforms
---

### Post by powerwolf on 2017-02-28
I am configuring a few machines that I've just obtained to use as mail servers, and would like some ideas/advice on best practices on how to proceed.  (If this isn't the right place for this post, I apologise, and would appreciate knowing where it can be better placed.)

I would like a machine in my DMZ that will accept mail by SMTP sent to my domains (user@mydomain.com, [EMAIL="user2@mydomain2.net"]user2@mydomain2.net[/EMAIL], etc).  It (or another machine) will collect mail by POP3/IMAP sent to webmail accounts (user@gmail.com, etc).  I gather using Postfix is the best option here.  This machine will then filter the mail for spam & viruses.  I have found a good guide on this [here]("https://help.ubuntu.com/lts/serverguide/mail-filtering.html").  However, rather than having mail stored on this machine, it should purely be an MTA that forwards mail to a second machine on my local network that will act as an MDA.

What I haven't been able to find is a way to configure Postfix to behave solely as an MTA that just relays mail on once it receives it.  Can this be done using Postfix?  Is there a better way?  Or am I just blind as a bat and can't see it for staring at it in the Postfix documentation? ;)

Thanks.

---

### Post by cariboo on 2017-02-28
I didn't see anything about a cloud here, so moved to server platforms.

---

