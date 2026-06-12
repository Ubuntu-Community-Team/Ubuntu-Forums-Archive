---
title: "installing 5.3 on 8.04  - how?"
date: 2011-01-01
forum: Server Platforms
---

### Post by tomjoad on 2011-01-01
I'm running 8.04 on some VPS:es that I'd like to upgrade to php 5.3.

There seem to be no official repositories, why is that,
and what can I do to minimize fuzz.

Thankful for any help in this matter,

regards,

//teson

---

### Post by stmiller on 2011-01-01
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

That's because 8.04 is fairly ancient. You'll want to upgrade to a newer version of Ubuntu. The most current LTS is 10.04 which has php 5.3.

---

### Post by tomjoad on 2011-01-02
Yes, yes, I know, but isn't 8.04 supposed to be supported for 5 years? php5.2 is about to reach end of live.

Whats hold back updates on a dist thats still supported?

regards,
//t

---

### Post by llawwehttam on 2011-01-02
> **tomjoad said:**
> Yes, yes, I know, but isn't 8.04 supposed to be supported for 5 years? php5.2 is about to reach end of live.

Whats hold back updates on a dist thats still supported?

regards,
//t

Because upgraded packages rely on other upgraded packages that rely on newer kernels........... which require a newer OS version.

By supported, it means that it will get security updates and bugs are still being fixed. Apart from that it gets very little attention.

You could always build from the source code......... if you are willing to fix any breakage.

---

