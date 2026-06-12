---
title: "VNC suddenly returns gray screen with terminal nothing else"
date: 2013-05-17
forum: Server Platforms
---

### Post by unbuntunewb on 2013-05-17
I am unsure what happened but my vncserver on my ubuntu 12 server stopped working right. I can still connect but I am greeted with a solid gray screen with a terminal box and a mouse pointer, not an x. If I close the box nothing happens. The strange part is it suddenly happened. Any ideas?

---

### Post by chrisguk on 2013-05-18
To get the right kind of help here it would be helpful to tell us the following, and in fact ask yourself the same questions when trying to debug something:

1.  What have you done to the machine prior to it not working?
2.  Did you perform any upgrades using apt-get?
3.  If you did upgrade did you upgrade using dist-upgrade or upgrade the kernel?
4.  What do the error logs show (sudo tail -f path/to/error/log)?

---

