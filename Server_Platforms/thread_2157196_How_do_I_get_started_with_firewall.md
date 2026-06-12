---
title: "How do I get started with firewall?"
date: 2013-06-24
forum: Server Platforms
---

### Post by trevorhanning on 2013-06-24
I've used Linux for awhile, but I'm totally new to administration. How do I get started with firewall?  Just some buzzwords and maybe the name of a book or link would be great. Thanks!

---

### Post by Lars Noodén on 2013-06-24
On Ubuntu, the default is to work with UFW. Or, if you want a GUI for that, to work with GUFW.  
[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Those are rather simple, though.  So if you are wanting to do anything advanced or work with multiple network ports in and out then you'll have to escalate to iptables.  There is material out there for iptables, but it isn't quite the freshest.  Rate limiting is something easy to learn and useful if you are running SSH.

Here is a little background reading on different settings:

[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)
[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)

---

### Post by m4nd4r on 2013-07-09
[IPTables]("http://www.yourownlinux.com/2013/05/iptables-linux-firewall.html") is Linux firewall where you can control traffic over ports by using Command Line Interface.

If you want to use Graphical User Interface, GUFW is one of the better choices.

---

