---
title: "Why is there Translation-en_ZA  appended to my apt urls??"
date: 2006-12-22
forum: Repositories &amp; Backports
---

### Post by yusufk on 2006-12-22
Hi,

When I do an apt-get update I get:

Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) edgy/main Translation-en_ZA 
...
...
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
  Connection failed

I'm trying to debug the reason why I can't update and one of the things that look suspicious since upgrading to edgy is the additional "Translation_en_ZA".

I'm behind an NT firewall and using NTLMAP to get through it. Apt is not very happy though.


tail /etc/apt/apt.conf
Acquire::http::Proxy "http://127.0.0.1:5865";

---

### Post by eXisor on 2006-12-22
This behaviour is normal and is not a problem.

You have selected ZA as your system locale. The en_ZA stuff is just synaptic/apt-get/aptitude telling the respositories that you prefer an English ZA localised version of whatever. If there is one you will get it, if there isn't, you get the bog english version.

Can you browse normally?

---

### Post by yusufk on 2006-12-22
Yes I can browse normally, and wget works fine, its just apt that doesn't work on all sites.

---

### Post by eXisor on 2006-12-23
I also live in ZA, but removed all the za. parts in my sources because of a similar problem to the one you're experiencing. I've had no problems since. If you do a search you'll find quite  a few mirror problem related posts.

This is conjecture, but perhaps it has to do with the rollout of changes to mirrors, that the dependencies arrive one by one on the mirror, and hence any update request during this period does, and perhaps should, result in the failure.

---

