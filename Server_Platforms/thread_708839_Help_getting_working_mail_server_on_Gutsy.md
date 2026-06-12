---
title: "Help getting working mail server on Gutsy"
date: 2008-02-26
forum: Server Platforms
---

### Post by Poleh on 2008-02-26
My goal is simple: To set up a lightweight, secure public facing mail server that provides secure (read encrypted) POP3 and IMAP access to a small number of users, with a small number of domains, and present web access using the sexy looking RoundCube.

I have looked all over the forums, howtoforge and general googling and found MANY tuts on how to set up many combinations of mail server on Ubuntu ... but none of them really address a few specific questions I have, and most seem awfully complicated.

I **think** I get the whole MTA (Postfix), Connector (Courier), Domains/Virtual Domains and Authentication thing ... but I just can't seem to get it to work - **I think I have apt-get'd myself into a dark, deep, endless hole :)**

**Questions**[LIST=1]
[*]What's best for a small number of mail users, using system accounts or some sort of virtual system using stuff like mysql/virtual domains?
[*]Is it possible to host multiple mail domains using system accounts? (I presume this is a Postfix thing?
[*]I understand that once I have IMAP up and running that RoundCube should be easy enough to get working ...
[*]I got Citadel working fine (well done on the easy install process btw) but it seems quite bloated for what I want to do, and a bit of a copout really :) I wanna learn this ****!
[*]**And the million dollar question:** where can I find a nice tut to accomplish my very meagre, easy to do, not unrealistic set of requirements above :) ??
[/LIST]

Many thanks and coffee beans in advance for any responses...!

---

### Post by Mr. C. on 2008-02-27
While your goal is simple to express, the reality is that there are many steps involved, and a lot to learn.  Installing, configuring, securing, and maintaining a mail server is non-trivial; reset your expectations accordingly.

HowTo's fail you at the first sign of trouble.  I'd like to recommend a more fundamentals-based, building block approach, where you install, configure and understand one component at a time, layer by layer.

Onto your questions (we'll assume postfix since you mentioned it):

[LIST=1]
[*]There is no "best", rather pro's and con's.  System accounts are quick and easy to setup, allow trivial forwarding for users via .forward files, but obviously moves user administration into the passwd file rather than into a mail-specific database.  While the default Ubuntu installations use mysql and procmail, I think this is overly complex for simple mail servers.  Personally, I'd recommend just going with some simple flat-file-based virtual mailboxes, and virtual aliases as desired.
[*]All domains in the local address class share the same localpart namespace (eg. user [email]bob@example1.com[/email] and [email]bob@example2.com[/email] are the same).   If you are going to have multiple domains, and you want distinct localpart namespaces, use virtual domains.
[*]Ok.  Not sure what your question is here.
[*]Ok.  Not sure what your question is here.
[*]There are plenty of them that might fit your requirements - just search the forums here, esp. the stickies.  I've not followed, verified, evaluated any of them, and as mentioned, don't advise this approach.  Get yourself **The Book of Postfix** and it will take you step by step through not only installation and configuration, but *understanding*, so that you can actually troubleshoot and tailor the system to your needs.
[/LIST]

Again, they key here is learning the fundamentals step by step, and build upon your successes.

Hope this helps get you rolling.
MrC

---

### Post by kwambus on 2008-02-27
I started a similar learning curve two or three years ago and I have to agree with Mr C. Take this project in small stages, start by building and understanding Mail Transfer Agents like Postfix, then move onto delivery agents like Courier, etc.

Taking too much at once will only confuse you, this is a complex beast and if you want to maintain it effectively you need to focus on your build one step at a time.

---

### Post by Poleh on 2008-02-27
bugger, I was hoping not to get these responses but secretly realised that I would. All good advice from both of you, so thanks for taking the time to reply, I do appreciate it.

---

