---
title: "Adding Mail Users? (Dovecot/Postfix/SASL)"
date: 2011-02-07
forum: Server Platforms
---

### Post by NessDan on 2011-02-07
I'm currently trying to setup a mail server. Dovecot, Postfix, and SASL are all running on it and I can currently connect to my main Ubuntu user (nessdan). The problem is that I don't want to be using

1) my main server account as a mail address, especially since it's what I use to login via SSH, and

2) it's redundant to have [email]nessdan@nessdan.net[/email] (I was going for something more creative/simple like [email]me@nessdan.net[/email] or [email]dan@nessdan.net[/email])

I'm also planning on having more than one email account (different emails for different web apps I make)

My question is how should I do this? I don't want to create new Ubuntu accounts for each mail user - I feel as if it's overkill. Is there a way to add users strictly for mailing purposes using SASL? (That's why I installed it to begin with.)

---

### Post by HermanAB on 2011-02-07
Hmm, it always strikes me as weird when people use Postfix and then jump through a whole lot of hoops to set up a database only for the user accounts.  To my mind it is much more important to put the email in a database, so that when you send mail to multiple users, it doesn't chew up disk space with duplications.

Anyhoo, if you want a mail system where everything - user accounts and mail - resides in a proper database, use Citadel.  It is very easy to set up using the Easy Install script and does every mail protocol ever invented.

---

### Post by NessDan on 2011-02-07
To be honest I'm very new to the server-side of things. I simply threw in the Ubuntu Server CD and installed everything I wanted on my server (Postfix just installed since I had selected "Mail Server" during installation.)

I'll check out Citadel though. But just so I understand you, is Postfix not meant to be database-driven?Are you supposed to create Ubuntu user accounts for every mail account you want with Postfix?

---

