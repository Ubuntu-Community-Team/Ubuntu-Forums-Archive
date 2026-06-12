---
title: "VirtualBox using too much CPU on host when idle? [SOLVED]"
date: 2009-03-29
forum: Virtualisation
---

### Post by Delever on 2009-03-29
You check CPU usage on Windows Guest - it is almost zero, yet on host, it is quite high (depends on how good is your CPU), it may even be 100% making computer unusable.

Suspected guest applications which could cause this:

Google Chrome
Google Talk
Sql Server 2008 or Sql Server 2005 SP3 (including express)
May be more...

It seems that they all are using high precision timer, which involves requesting action from VirtualBox 1024 times per second. ([bug here]("http://www.virtualbox.org/ticket/3613"))

So far possible solutions are these:

Do not use these applications, simple as that, or

Start another vm with minimal RAM (it is not required to boot), and see if that helps.

---

