---
title: "Emails taking unusually long to deliver (1-5min)"
date: 2010-04-12
forum: Server Platforms
---

### Post by auraithx on 2010-04-12
I'm running Ubuntu 9.10 on a VPS with linode.

I run around 10 sites from this vps and whenever I try to do anything thats related at all to email (such as user registration, contact form submission) the process itself can take anywhere from one to five minutes. 

I realise that this is most likely due to a misconfiguration with how my email has been set up.

Any guidance to how I would diagnose and fix this problem is appreciated
Thanks,
AuraithX

---

### Post by KB1JWQ on 2010-04-12
What are you running for an MTA?

What do your mail logs say?

If postfix, what's the output of postconf -n?

---

### Post by auraithx on 2010-04-29
Fixed this by switching my MTA.

---

### Post by Tommetje on 2010-04-29
Can you be so kind as to elaborate on what the problem was exactly on how it was fixed? That might prove usefull for other forum members.

Thanks in advance!

Tom

---

