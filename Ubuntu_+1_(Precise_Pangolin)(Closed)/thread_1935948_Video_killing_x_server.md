---
title: "Video killing x server"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sonicb00m on 2012-03-05
Whenever I try to play videos it keeps returning to the login screen. I have the AMD driver installed from the RDM.

---

### Post by dtarbit on 2012-03-05
I'm getting the same problem, with ATI graphics and video on my laptop. Even tried wiping the alpha and doing a fresh install with the beta to no avail.

---

### Post by sonicb00m on 2012-03-05
I reverted to the open driver and it is ok now.

There are other issues with the AMD driver too. Not all icons are clickable when searching the dash.

---

### Post by dtarbit on 2012-03-05
Thanks, will give that a try.

---

### Post by kelpdip on 2012-03-05
It seems to be a hardware overlay driver problem. The usual setting
aticonfig --overlay-type=xv
Is unavailable in this driver.
Using --overlay-type=opengl breaks the whole system, with more than just xorg.conf being deconfigured. Make an image before messing with aticonfig, because it is more powerful than expected.

---

