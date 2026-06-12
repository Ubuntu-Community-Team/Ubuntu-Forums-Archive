---
title: "X11 forwarding not working on 6.06 server (-Y/-X)"
date: 2006-11-13
forum: Server Platforms
---

### Post by tengil on 2006-11-13
Hi,

I'm not getting X forwarding to work. Both 'ssh -X' and 'ssh -Y' ends up with an empty $DISPLAY.

I've installed the 6.06.1 server without lamp, then openssh-server and gedit. Do I need anything else to get gedit to work remotely?

-kurt.

---

### Post by tengil on 2006-11-13
Got the answer on #ubuntu-server. I needed xauth as well.
Solved.

---

