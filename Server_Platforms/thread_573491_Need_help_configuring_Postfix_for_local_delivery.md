---
title: "Need help configuring Postfix for local delivery"
date: 2007-10-11
forum: Server Platforms
---

### Post by Metacarpal on 2007-10-11
Hey folks,

Browsed through the existing posts, but couldn't find an answer...

I'm trying to set up postfix on my system to handle local mail delivery.  The problem I'm having is that all my email ends up with the status:
```
delivery temporarily suspended: transport is unavailable
```

I'm trying to configure through Webmin, but it's such a nightmare confluence of settings that I don't even know where to start.

If you know how to tell postfix "just give jdoe the freaking mail for jdoe," whether it's through Webmin or manual editing of configuration files at the command line, please help me out.

TIA

---

### Post by MJN on 2007-10-11
Post your current config (/etc/postfix/main.cf and /etc/postfix/master.cf) and we can take a look.

Mathew

---

