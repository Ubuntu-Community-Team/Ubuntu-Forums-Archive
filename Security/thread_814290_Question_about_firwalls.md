---
title: "Question about firwalls"
date: 2008-05-31
forum: Security
---

### Post by DFord425 on 2008-05-31
I want to take an old computer and turn it into a firewall, not out of nessecity, but more for learning. My question is, is iptables a good firewall to use/experiment with. Or are there other firewalls that are better to use that are more configureable. Thanks for your help in advance.

---

### Post by kevdog on 2008-05-31
iptables is the only firewall built-into the linux kernel.  There are a lot of other programs (both GUI and command line) that allow you to alter the iptables indirectly.  

Take a look at this:
[http://wiki.debian.org/Firewalls](http://wiki.debian.org/Firewalls)

---

### Post by DFord425 on 2008-05-31
Thanks, so your saying that i can only use iptables?

---

### Post by wdaniels on 2008-05-31
Almost all firewall software for Linux is based on iptables (or ipchains) - it is essentially the base software layer for all filtering of network traffic. But because it sits at the lowest level in the stack, the configuration rules can be complex to deal with entirely by hand. There are loads of scripts around to help generate iptables rules and a couple of notable GUI applications:

[LIST]
[*][Shorewall]("http://www.shorewall.net/")
[*][Firestarter]("http://www.fs-security.com/")
[/LIST]

There are also some complete Linux/FreeBSD distributions designed specifically a firewall/routing platforms:

[LIST]
[*][IPCop]("http://ipcop.org/") (Linux)
[*][Smoothwall]("http://www.smoothwall.org/about/index.php") (Linux)
[*][Untangle]("http://www.untangle.com") (Linux)
[*][pfSense]("http://www.pfsense.com/") (FreeBSD)
[*][m0n0wall]("http://m0n0.ch/wall/") (FreeBSD)
[/LIST]

---

### Post by kevdog on 2008-05-31
iptables is part of the kernel.  I'm not familiar with another method. I've never heard such a complaint.

---

### Post by The Cog on 2008-06-01
Also guarddog. It's a KDE program, but deserver a mention as a notable iptables confiuration GUI.

Agreed, all the Linux firewall GUIs I know of end up writing iptables scripts. I see nothing wrong with that, and lots of things right with that.

---

### Post by kamaji792 on 2008-06-01
This is a nice gentle introduction to iptables:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

all the best

---

### Post by DFord425 on 2008-06-01
Thanks for all the info.

---

