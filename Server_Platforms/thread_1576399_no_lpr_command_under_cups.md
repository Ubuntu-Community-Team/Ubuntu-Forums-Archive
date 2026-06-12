---
title: "no lpr command under cups?"
date: 2010-09-17
forum: Server Platforms
---

### Post by spipe on 2010-09-17
Setting up a new 64-bit lucid server.  I installed cups and cups-client, and expected to have the "lpr", "lpq" etc. commands available; we have old scripts that rely on them.  But I don't see them anywhere.

Are they still provided in some package I don't know about?  Otherwise I'll probably have to come up with wrappers around lp and lpstat, to avoid having to revise a lot of old code.

---

### Post by HermanAB on 2010-09-17
cupsys-bsd

---

### Post by spipe on 2010-09-17
> **HermanAB said:**
> cupsys-bsd

You da man. ):P

---

