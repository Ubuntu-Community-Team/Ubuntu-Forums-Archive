---
title: "Why no /etc/inittab in my ubuntu server?"
date: 2007-01-17
forum: Server Platforms
---

### Post by deejaylinux on 2007-01-17
Hi again forum?

I'm very suprised for not to see the /etc/initttab in my system. Is this normal in the ubuntu server release? It's the first time I see this in a Linux box... incredible!!!

Then, what runlevel is my box configured? I need to know this because I need to set some scripts for starting.

Thanks in advanced

Regards

---

### Post by jtc on 2007-01-17
It has do to with the fact that Ubuntu is replacing *sysvinit* with something new and shiny called *upstart*. 

[http://upstart.ubuntu.com/]("http://upstart.ubuntu.com/")

---

