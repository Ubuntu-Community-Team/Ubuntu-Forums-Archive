---
title: "Zope on Ubuntu"
date: 2007-09-09
forum: Server Platforms
---

### Post by Osvaldo on 2007-09-09
Hi.

I've installed zope3 package but I'm having trouble using it...

How do I start the server ? where is the start/stop server commands?

The instructions on the official website didn't work... I habe a Python book with a chapter about zope, but I can't start the server...

Thanks for reading.

Osvaldo

---

### Post by arkopII on 2007-09-10
Hello, 

Have you created an instance of Zope?

Have you tried to execute ./bin/runzope from the instance's directory?

If yes, what error do you have?

Regards

---

### Post by soulresin on 2007-09-11
Run /usr/lib/zope3/bin/mkzopeinstance to create a zope instance.

Create it in a subdir of  /var/lib/zope3/instance

Run /etc/init.d/zope3 start

---

### Post by SkyyBugg on 2007-11-30
I should have looked here first..  I spent all day yesterday trying to get it running from Zope docs.  I followed your few simple steps and got it running..
Thanks!!!! Now I can go to the movies.. jk

:popcorn:

---

