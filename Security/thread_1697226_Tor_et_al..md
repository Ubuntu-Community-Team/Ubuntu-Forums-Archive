---
title: "Tor et al."
date: 2011-02-28
forum: Security
---

### Post by 3602 on 2011-02-28
So I got Tor working, Polipo and whatnot. Because why not.
At first everything seems to be correct, I'd enable Torbutton, the test site is good and browsing works albeit slow. So I got Vidalia to contribute a bit as a relay.
Vidalia cannot start Tor, saying cannot bind 127.0.0.1:9050. Searched a bit, installed rc-something, disabled the boot levels and OK, no more errors.
Thing is, Vidalia would load right, but it stuck at a stage. I opened the advanced logs and saw it stuck at:
```
[notice] Bootstrapped 100%: Done.

```
So what's going on? There aren't any errors or anything.
Thank you very much.

---

### Post by 3602 on 2011-02-28
Solved itself after a reboot.

---

