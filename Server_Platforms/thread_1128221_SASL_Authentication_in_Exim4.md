---
title: "SASL Authentication in Exim4"
date: 2009-04-17
forum: Server Platforms
---

### Post by q2dg on 2009-04-17
Hi!
First of all, sorry for my english.
I´ve a Exim4 server which I´ve configured Sasl-authentication (specifically Auth-plain and Auth-login authenticators). Besides, I´ve incorporated encryptation via Starttls. And it works OK.

The problem is that it´s also works without encryptation and without authentication!! That is to say, everyone can send a mail (even with a false sender), without the obligation of authenticate, even without using TLS! Like if I wouldn´t have configurated anything!! 

Has someone any clue about what could happen?
Thanks a lot!!

---

