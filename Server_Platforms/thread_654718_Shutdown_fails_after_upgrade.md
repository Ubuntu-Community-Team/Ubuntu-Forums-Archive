---
title: "Shutdown fails after upgrade"
date: 2007-12-31
forum: Server Platforms
---

### Post by frodemt on 2007-12-31
Hi, I had Ubuntu 6.10 server and upgraded to Ubuntu 7.10 server. Everything work except shutdown. When using "shutdown now" I get this:

[IMG]http://tviberg.info/diverse/shutdown2.jpg[/IMG]

[IMG]http://tviberg.info/diverse/shutdown1.jpg[/IMG]

What can I do to fix this problem?

---

### Post by p_quarles on 2007-12-31
Did you mean this?:
```
shutdown -P now
```

---

### Post by frodemt on 2007-12-31
but "shutdown now" should work right?

---

### Post by p_quarles on 2007-12-31
> **frodemt said:**
> but "shutdown now" should work right?
No.

---

### Post by frodemt on 2007-12-31
What does "shutdown now" do, and what is "init: rc1 main process (4833) killed by TERM signal"?

---

### Post by p_quarles on 2007-12-31
It initiates a shutdown sequence without knowing how to complete it. The shutdown command requires two things: an instruction (e.g., P, h, r, k) and a time (e.g., "now", "+30" or "13:45").

---

### Post by frodemt on 2007-12-31
ok, I figured I used "halt" and "reboot now" before. I mixed up thouse two. Thanks for the explanation and a good new year to you! :KS

---

### Post by MJN on 2007-12-31
> **p_quarles said:**
> It initiates a shutdown sequence without knowing how to complete it. The shutdown command requires two things: an instruction (e.g., P, h, r, k) and a time (e.g., "now", "+30" or "13:45").

That's not strictly true - you can just specify the time in which case the default action is to enter run-level 1 (single-user mode).

But, yes, to perform what the OP considers a shutdown the -h option (or even -hP on some systems) must be specified in order to actually turn the machine off once 'shutdown'.

Mathew

---

