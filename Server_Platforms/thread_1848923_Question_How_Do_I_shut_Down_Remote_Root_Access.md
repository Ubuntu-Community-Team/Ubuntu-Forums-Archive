---
title: "Question: How Do I shut Down Remote Root Access?"
date: 2011-09-23
forum: Server Platforms
---

### Post by TheGuvernor on 2011-09-23
I've just spun up a new RackSpace cloud server. By default you have to ssh in with root and create a user. So I added a user and then assigned them to the sudo group. Now I want to shut down anyone accessing root via ssh. I know I read somewhere that there was an easy solution for this but I'm unable to find it. Anyone know?

---

### Post by Lars Noodén on 2011-09-23
Look at [PermitRootLogin](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) in /etc/sshd_config.  Set it to **no**.

---

### Post by TheGuvernor on 2011-09-23
That was it! You rock!

---

