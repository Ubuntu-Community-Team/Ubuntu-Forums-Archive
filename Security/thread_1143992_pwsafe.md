---
title: "pwsafe"
date: 2009-04-30
forum: Security
---

### Post by dr_pressure on 2009-04-30
Hi guys,

Just discovered pwsafe, and I really like the fact that it's commandline (will work over ssh). But before I start using it for real I have a question.

If I don't run it as root, I get these warnings:
WARNING: pwsafe unable to seed rng from /home/pressure/.rnd
WARNING: pwsafe unable to use secure ram (need to be setuid root)

Now my laptop is a trusted environment, so I figure I don't care about secure ram. Besides, if there's a malicious program on my pc it can always monitor the clipboard.

But what is this thing about not being able to seed the random number generator? Is that just for generating new passwords or something more important? Do I need to --createdb as root?

Any suggestions would be appreciated,
Pressure :)

---

### Post by dr_pressure on 2009-05-01
Ah nvm problem solved.

You always get that message on the first run. If you --createdb as root then you also get it every time you run pwsafe as a nonroot user. So bad idea to --createdb as root.

---

