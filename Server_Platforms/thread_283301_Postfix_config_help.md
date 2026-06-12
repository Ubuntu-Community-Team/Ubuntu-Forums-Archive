---
title: "Postfix config help"
date: 2006-10-24
forum: Server Platforms
---

### Post by peanut butter on 2006-10-24
hi,
im tring to use my webserver to process forms. i need to know how to configure postfix to just send mail and not try to recieve it.

i have also been looking for a formmail php script that just works and is configured by hidden form feilds.

---

### Post by peanut butter on 2006-10-24
bump?

---

### Post by MJN on 2006-10-25
Just thinking aloud for a moment (and I'm sure there's a far more elegant way of achieving this within the Postfix config) you could just block incoming port 25 connections with your firewall. Local and outward mail delivery would remain unaffected (open).
 
Mathew

---

### Post by peanut butter on 2006-10-25
i dont have the ability to use a hardware firewall, but what would you use for a software firewall?

---

### Post by MJN on 2006-10-25
IPChains springs to mind, but as I use a hardware firewall someone else will have to jump in with the config (or alternative suggestion).
 
There must be a suitable Postfix config arrangement to accomplish what you're after though.
 
Mathew

---

