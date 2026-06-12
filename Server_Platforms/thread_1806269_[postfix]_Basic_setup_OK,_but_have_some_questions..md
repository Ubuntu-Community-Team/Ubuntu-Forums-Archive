---
title: "[postfix] Basic setup OK, but have some questions..."
date: 2011-07-17
forum: Server Platforms
---

### Post by blenderfox on 2011-07-17
Hi there,

I'm trying to setup postfix (or exim, I don't mind which), so I can move away my last remaining PC from Windows.

I've tinkered with Postfix for good part of a month and I can get it to accept emails using SMTP and post them to a virtual mailbox based on MySQL tables. And it rejects mail addressed to local email addresses that it can't find in the table. Great.

First question (or problem.) I've set up Postfix to relay email it cannot deliver locally such as is the case when you send out an email. My remote host requires authentication. How can I set this up?

Second question: I want to force my clients to use either AUTH, TLS or SSL, and not allow anonymous connections (to prevent an open relay server.) How do I set that up without interfering with the smarthost setting? The smarthost login is not one of my clients, it's a pre-determined login and password that is solely used for the email relaying aspect.

I hope this message is clear, but let me know if you need more information.

---

### Post by HermanAB on 2011-07-18
Uhmmm, you can tinker for another month, or you can install Citadel and have it all working in about 20 minutes, but that will take all the fun out of it...

To force use of TLS, simply drop packets on the ordinary plain text ports with iptables, leaving the SSL ports as the only options.  Look at /etc/services to see the port numbers.

---

### Post by blenderfox on 2011-07-18
Guess that shows just how much of a rookie I am :P

---

### Post by blenderfox on 2011-07-18
I've installed Citadel and it works okay for local delivery, but relaying is still a problem. I use user:pass@host for the syntax, and citadel tries to use AUTH PLAIN on the server, which it doesn't support. Is there a way I can get Citadel to use CRAM-MD5 instead?

---

### Post by blenderfox on 2011-07-18
Uh... got censored again? :P

---

### Post by blenderfox on 2011-07-18
> **momokoyukino said:**
> I've installed Citadel and it works okay for local delivery, but relaying is still a problem. I use user:pass@host for the syntax, and citadel tries to use AUTH PLAIN on the server, which it doesn't support. Is there a way I can get Citadel to use CRAM-MD5 instead?

Never mind, figured it out -- I setup postfix to be a Satellite system on loopback only, and set it to listen to a non-standard port (such as 4532), then used that in Citadel. In Postfix, I setup SASL and so when Citadel sends an email out, it actually submits to Postfix, then postfix handles the smarthost connection to the remote SMTP server, and this time, it performs authentication via CRAM-MD5.

---

