---
title: "So I'm ready to turn my ubuntu into a router."
date: 2007-10-15
forum: Server Platforms
---

### Post by Ikith on 2007-10-15
Ubuntu is installed and I have many questions. I really want to learn but I'd like a guide if anyone would be willing to teach me a little bit and point me in the right direction. I plan on using the guide in tips and tutorials but I also have a few questions:

1. How do I monitor network traffic? Or how would I go about setting that up?

2. How do I set ports to foreward?

3. When setting this up does this include a firewall script or do I need to find/do that on my own?

4. Are there better guides out there?

Thats pretty much it. A guide would also be nice if they could talk on AIM or MSN to guide me through it and so I can ask questions as they come up.

Thanks,
Total noob willing to learn Ikith.

---

### Post by scrooge_74 on 2007-10-15
[http://www.smallworks.com/~jim/SISO/www.cybcon.com/~coert/linux/siso/index.html](http://www.smallworks.com/~jim/SISO/www.cybcon.com/~coert/linux/siso/index.html)

Remember that you need to install the server edition in any case since the kernel is optimized for that kind of work

That guide should be pretty helpfull and give you a couple of ideas

And this should be a little more straight forward [http://howtoforge.com/debian_ebox](http://howtoforge.com/debian_ebox)

but should check the first one too

---

### Post by robert_pectol on 2007-10-16
Here's a small tutorial with a NAT routing/firewall script designed specifically for Ubuntu:
[http://rob.pectol.com/content/view/5/28/](http://rob.pectol.com/content/view/5/28/)

---

### Post by elvis on 2007-10-16
> **Ikith said:**
> 1. How do I monitor network traffic? Or how would I go about setting that up?
There are dozens of ways to do this.  Some people use web-based/GUI systems like Cacti:
[http://www.cacti.net/](http://www.cacti.net/)

Me personally, I use IPTraf and TCPDump:
[http://iptraf.seul.org/](http://iptraf.seul.org/)

IPTraf and TCPDump are "realtime" scanners, and show you what's going on right now.  Cacti is more of a long-term monitor.

> **Ikith said:**
> 2. How do I set ports to foreward?

3. When setting this up does this include a firewall script or do I need to find/do that on my own?

4. Are there better guides out there?

Thats pretty much it. A guide would also be nice if they could talk on AIM or MSN to guide me through it and so I can ask questions as they come up.

Thanks,
Total noob willing to learn Ikith.

All of what you want to achieve will ultimately be handled by the Linux kernel and IPTables.

There are a mass of front-ends for IPTables.  My personal favourite is Shorewall (aka the Shoreline Firewall):
[http://www.shorewall.net/](http://www.shorewall.net/)

Shorewall is a collection of scripts and config files that allow you to build a firewall/router/portforward skeleton and then it will generate the more complex IPTables commands for you.  

Shorewall is not just for people new to IPTables and firewalling.  I've been a network administrator for some time and I love Shorewall.  It makes firewalling quickand painless, and gives you a quick overview of what your firewall does without needing to delve through pages of scripts.  That makes it great for security auditing as well.

The shorewall website is packed full of plain-english documentation.  Anyone who wants to start doing firewalling a little more complex than just a single interface box would certainly find it useful to read through some of the documents on the shorewall website.

---

