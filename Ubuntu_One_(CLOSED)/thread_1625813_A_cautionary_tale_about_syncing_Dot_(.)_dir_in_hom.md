---
title: "A cautionary tale about syncing Dot (.) dir in home dir across multiple computers"
date: 2010-11-19
forum: Ubuntu One (CLOSED)
---

### Post by MechaMechanism on 2010-11-19
Don't sync dot (.) dir in your home dir across multiple computers.  You will experience U1 conflicts galore.  There should be some kind of stern warning before U1 starts sync.  Now I have data loss and a long brutal slog to fix everything.  A cautionary tale indeed.

---

### Post by tgalati4 on 2010-11-19
That is what is called an "Edge Case".  UbuntuOne is designed to sync with one unique computer at a time--you direct multiple computers to use the UbuntuOne server.  Meanwhile config files get sync'd locally (that's what 90% of .* files are) and chaos ensues.

I bet the UbuntuOne developers hadn't thought of that scenario.

That is the benefit of using Linux.  If you break it, you get to keep both pieces.  In this case the pieces are identical because you sync'd them.

---

