---
title: "Postfix probelm"
date: 2009-07-22
forum: Server Platforms
---

### Post by Sneblot on 2009-07-22
I am trying to set up a Ubuntu Server using this tutorial HowtoForge Perfect Server I have got to step 15 with out a hitch but I am now on setting up the postfix.

it tells me to add this code

apt-get install postfix libsasl2-2 sasl2-bin libsasl2-modules procmail


It then asks me these two questions

General type of mail configuration:
System mail name:

which I answer as 

General type of mail configuration: Internet Site
System mail name: server1.example.com

then the tutorial says to put in this code

dpkg-reconfigure postfix


and that I should get these questions to answer

General type of mail configuration: <-- Internet Site
System mail name: <-- server1.example.com
Root and postmaster mail recipient: <-- [blank]
Other destinations to accept mail for (blank for none): <-- server1.example.com, localhost.example.com, localhost.localdomain, localhost
Force synchronous updates on mail queue? <-- No
Local networks: <-- 127.0.0.0/8
Use procmail for local delivery? <-- Yes
Mailbox size limit (bytes): <-- 0
Local address extension character: <-- +
Internet protocols to use: <-- all

But all I get is this line of text 

/usr/sbin/dpkg-reconfigure: postfix is broken or not fully installed.


Can anyone help me?

---

