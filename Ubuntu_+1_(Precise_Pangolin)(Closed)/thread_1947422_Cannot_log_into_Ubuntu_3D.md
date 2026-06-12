---
title: "Cannot log into Ubuntu 3D"
date: 2012-03-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by slugicide on 2012-03-26
I've suddenly found myself unable to log into Unity 3D. When I try to do so what happens is: I enter my password, the splash/background comes up, nothing happens for a few seconds, then the cursor spins for a few seconds and then nothing.

I don't even know how to go about fixing this. And clues?

---

### Post by philinux on 2012-03-26
> **slugicide said:**
> I've suddenly found myself unable to log into Unity 3D. When I try to do so what happens is: I enter my password, the splash/background comes up, nothing happens for a few seconds, then the cursor spins for a few seconds and then nothing.

I don't even know how to go about fixing this. And clues?

Try 2d or the classic option. Most likely a graphics driver issue. Or a compiz / unity setting.

---

### Post by slugicide on 2012-03-26
Yeah. I'm silly, I forgot to mention that I can log into 2D just fine. I just don't quite know how to fix 3D. Should I just wait and see if an update fixes it?

---

### Post by Procrustes on 2012-03-26
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963633](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963633)

fix committed

---

### Post by slugicide on 2012-03-26
Thanks. According to some comments on the bug report

```
unity --reset
``` seems to do the trick for now.

---

### Post by phaed on 2012-03-26
I get this problem all the time. I've been dropping to TTY and deleting all config dot folders. Glad to know about unity --reset !

---

