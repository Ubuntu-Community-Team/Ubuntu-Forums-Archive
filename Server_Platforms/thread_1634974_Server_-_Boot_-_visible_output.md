---
title: "Server - Boot - visible output"
date: 2010-12-01
forum: Server Platforms
---

### Post by Alex1983 on 2010-12-01
Hi everybody,

we just migrate with our Linux Server to Ubuntu 10.04.1 LTS.

Everythink is fine, except the visible output during boot.

We removed the quiet and splash option in /etc/default/grub, so that we can see some output.
The annoying thing is, that just when login prompt should appear, the whole screen gets black and all output is removed.

This is maybe a nice visual effect, but for productive use very bad.
I have searched a lot in the internet, and in my opinion this behaviour is caused by plymouth.
We have removed all plymouth* scripts from /etc/init/, but have still the same behaviour.

We just want to have the boot messages shown on monitor and then in the last line the login prompt.

Is it possible to configurate this behaviour with Ubuntu? 

Hopefully
Alex

---

### Post by CharlesA on 2010-12-01
That's part of the splash screen (plymouth). You should be able to see the output by going to tty7.

---

