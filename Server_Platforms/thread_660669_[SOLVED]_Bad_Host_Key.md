---
title: "[SOLVED] Bad Host Key"
date: 2008-01-07
forum: Server Platforms
---

### Post by NateMan on 2008-01-07
I just redid my server, however now I cannot ssh into through terminal. It gives me an error message telling me that host key varification failed.  I understand this is because my new install has a different key than the old one, but I'm unsure on how to change this in my laptop so I can receive and authenticate the new key. Any help would be greatly appreciated.

---

### Post by HermanAB on 2008-01-07
Delete ~/.ssh/known-hosts

Cheers,

Herman

---

### Post by NateMan on 2008-01-07
Thanks, worked like a charm. Problem solved.

---

