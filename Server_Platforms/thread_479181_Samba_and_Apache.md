---
title: "Samba and Apache"
date: 2007-06-20
forum: Server Platforms
---

### Post by PopcornEaterMan on 2007-06-20
Will there be at higher risk if I have samba installed on my linux server?  currently, I have Apache set to only server requests from localhost, but I hope to, at some point, begin to open this up and eventually point this out to the outside world.  Will samba somehow open up my computer to so that hackers will have access to resources they wouldn't ordinarily have?

My network has a router protecting my internal network, one windows xp computer, and one ubuntu box.    Sorry, but I am a newbie, and I'm just getting my feet wet with Apache and web development.

---

### Post by Mr. C. on 2007-06-20
The strictest answer is yes, but read on...

The stock response is that every service you enable provides additional opportunities for exploitation.  Configure your services as securely as you are able, and ask lots of questions.  Samba is a means for sharing Windows shares, and generally doesn't interact with apache, unless you've mounted a smbfs/cifs share that apache accesses.  Unless someone finds a way to exploit these two systems and their interactions, samba will present little additional risk to your apache server.

Worry more about correctly configuring and securing your system.

...so, the practical answer is no.

MrC

---

