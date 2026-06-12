---
title: "upstart does not start on &quot;x and y&quot;"
date: 2011-07-16
forum: Server Platforms
---

### Post by brumm on 2011-07-16
Hi,

I just upgraded to 10.04 LTS and ran into upstart. After inital dismay because several of my scripts did not run anymore, I now want to embrace upstart for its advantages. Problem: It does not do what it's told.

As a first step, I tried to change cron.conf to depend on mysql, so my start/stop on now reads:

start on (runlevel [2345] and started mysql)
stop on (runlevel [!2345] or stopping mysql)

Stopping works, starting does not. If I omit the runlevel part, it also starts when mysql starts. But why does it not start when used in conjunction with runlevel? I tried adding or removing parentheses with no luck.

All examples I found seem to indicate that this should work, but it does not.

Any thoughts?


Bye,
brumm

---

