---
title: "FireHOL not working!"
date: 2007-05-09
forum: Server Platforms
---

### Post by ayro on 2007-05-09
Hi,

I am trying to get fireHOL working on Kubuntu Feisty.  Each time I try to start the service, it gives this error. 

.......@AMD-Linux:/etc/firehol$ sudo /etc/init.d/firehol restart
Restarting iptables firewall: FireHOL ...Cannot find an executables iptables command.
done.

iptables is installed to /sbin/iptables and it runs from the command line.

Any ideas?

thanks
ayro

---

### Post by EdinburghRob on 2007-05-12
Hi ayro,

I have the same problem.

I found this:

[http://sourceforge.net/forum/forum.php?thread_id=1722274&forum_id=196547](http://sourceforge.net/forum/forum.php?thread_id=1722274&forum_id=196547)

Might be what's causing the problem. Will give it a try.

--Rob

---

### Post by EdinburghRob on 2007-05-12
ignore my previous post.

The 'Restarting iptables firewall: FireHOL ...Cannot find an executables iptables command.' error might be caused by the FireHOL library not loading. This will fail silently.

Check to see if the library is executable. For some reason when /sbin/firehol was trying to call the library it got an 'permission denied', but the error got lost.

eg. try "chmod o+x /lib/firehol/firehol"

That fixed it for me.

--Rob

---

### Post by ayro on 2007-05-24
thank you very much for your help....it is working now.

btw...does this mean that all that time I was unprotected from my firewall?

Have a great day!
Ayro

---

