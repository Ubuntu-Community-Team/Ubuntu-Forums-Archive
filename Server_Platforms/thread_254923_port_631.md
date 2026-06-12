---
title: "port 631"
date: 2006-09-10
forum: Server Platforms
---

### Post by nardis_Miles1 on 2006-09-10
I have two ubuntu boxes (6.06) and a Debian sarge box all on the same network. One of the ubuntu boxes and the debian box have printers running under cups. All of the boxes claim to see the ubuntu printer and the debian printer. I can actually print to the debian printer from everywhere, but when I try to print to the ubuntu printer, I get a message that connection to XXX.XXX.XXX.XXX:631 refused, where the X'd dotted quad is the IP address of the ubuntu box. I have looked at the services files on the debian and ubuntu boxes and they are identical. Specifically, they all have the 631 ports.

When I scan the ports on the ubuntu only three are open, while all of the advertised ports are open on the debian box. I have not installed any firewall software on the ubuntu boxes and I see no iptables or ipchains files in /etc. So, does ubuntu put a firewall on in the default installation?

Art Edwards

---

### Post by Kurt` on 2006-09-10
# sudo iptables --list

to see what firewall rules are in effect

---

