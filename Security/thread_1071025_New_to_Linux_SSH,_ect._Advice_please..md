---
title: "New to Linux SSH, ect. Advice please."
date: 2009-02-15
forum: Security
---

### Post by newto on 2009-02-15
I'm new to security and to Linux. I changed the default port for SSH and downloaded denyhosts from the packet manager. But that's it. I don't need to run any services for a network etc. on this system, just connect to the internet pretty much. Is there anything else I need to do? Advice please.

---

### Post by kevdog on 2009-02-15
I guess you are running the deamon correct?  Denyhosts is good, also putting a rate limiter with iptables is good also.  There is no one protection plan you can hang your hat on, but several different strategies do help.  Another is disallowing use of password logins and use only keys, however this comes with some inconvience.

---

### Post by madnak on 2009-02-15
I take it that you are using SSH for something otherwise there is no reason for running it.

I would recommend reading this thread as it has some cool stuff in it.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by newto on 2009-02-15
Thanks for the replys all.

---

