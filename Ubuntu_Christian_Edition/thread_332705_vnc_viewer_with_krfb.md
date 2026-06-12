---
title: "vnc viewer with krfb?"
date: 2007-01-06
forum: Ubuntu Christian Edition
---

### Post by runkidrun on 2007-01-06
My friend has set up a server through krfb and given me the ip (which is incorrect) the password and nothing else. So on Terminal Server Client I can't fill in the required information. Then in the terminal when I type "vncviewer xxx.xxx.xxx.xxx" It just takes forever and then says "connection timed out"

What's going on here?](*,)

---

### Post by runkidrun on 2007-01-06
O.K. I received the correct ip address....Same problem.:-k

---

### Post by hyper_ch on 2007-01-06
why don't you use krdc? That's the vnc viewer for KDE and counterpart to krfb...

---

### Post by runkidrun on 2007-01-06
I am running GNOME won't that create some issues?

---

### Post by hirak99 on 2007-11-01
Try x11vnc or vino. kRfb is badly coded, for example for everyone I know who could use it, it uses 100% of the CPU while serving rendering it completely useless (in comparison vino or x11vnc will use about 1% of the CPU).

---

