---
title: "removing services"
date: 2005-01-20
forum: Server Platforms
---

### Post by molvistan on 2005-01-20
i just found out that my linux is running services which allow ppl to connect to my computer how can i shut down these services.

thank you

---

### Post by jdong on 2005-01-20
You need to be more specific. What services? what ports? Who told you? A port scan?

---

### Post by molvistan on 2005-01-21
i did a port scan and found the following.

**Port	State	Service**
25	open	smtp
111	open	sunrpc
631	open	ipp
842	open	unknown

---

### Post by mendicant on 2005-01-23
If you did the port scan from localhost (that is, the machine on which you did the scan was the same machine you were scanning), this doesn't tell you much.  You need to see if external hosts can access those ports.  It is somewhat likely that these can only be seen locally.  If you can see these externally, you should probably install a firewall if you don't want them to be seen.  You probably want these services on your machine.

FYI:
25 is your email server (postfix by default), 631 is cups (probably) and 111 is the RPC portmapper.  This is a dependency of a number of packages.  To check which is causing it, use aptitude, and check the reverse dependencies for the package portmap.  It is also needed if you have any nfs mounts.

842 is not an IANA assigned number, from what I can see:
[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

To check what is listening on it, you can try lsof | grep 842
You can also add | grep TCP or | grep UDP to that pipe to check for TCP or UDP listeners.

---

### Post by Kopf on 2005-01-26
The package rcconf will allow you to see what daemons are starting up at boot time, and easily add or remove them.  Hope this helps.

Kopf

---

