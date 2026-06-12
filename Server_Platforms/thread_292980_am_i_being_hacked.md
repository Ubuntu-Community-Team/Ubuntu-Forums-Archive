---
title: "am i being hacked?"
date: 2006-11-04
forum: Server Platforms
---

### Post by yoniman on 2006-11-04
hello all.
i have firestarter firewall in my computer (and ubuntu 6.06)
and today i have opened it
and i found in active connections
some connection to an ip, in port 12345
with the service NETBUS so i have restarted my computer.
is there any that i will stop those attacks?

thanks in advance

---

### Post by Joe_CoT on 2006-11-04
[Port 12345](http://news.zdnet.com/2100-1009_22-819807.html) is used by a number of things; [NetBus](http://en.wikipedia.org/wiki/NetBus) is an ancient windows trojan. Are you sure it wasn't just a Port Scan?

---

### Post by kidders on 2006-11-04
Hi there,

I'd tend to agree with Joe_CoT. Unless something on your end is actually listening on that port, creating an incoming connection over it between your computer and someone else's would be impossible. If the connection was an outgoing one, you can use netstat (and related tools) to identify the specific process that initiated the connection.

You will probably find that nothing is wrong :-)

---

### Post by Chayak on 2006-11-05
You'll find things like this are fairly common.  My server security logs were full of bot bruteforce attempts until I moved my SSH service to a different port that way they can throw a supercomputer to brute SSH on the default port and nothing would ever come of it.
look at [http://www.runyourownserver.org/]("http://www.runyourownserver.org/")
they have some good tips on security and they have an Ubuntu episode.

---

### Post by Joe_CoT on 2006-11-06
> You'll find things like this are fairly common. My server security logs were full of bot bruteforce attempts until I moved my SSH service to a different port that way they can throw a supercomputer to brute SSH on the default port and nothing would ever come of it.

I also noticed the same issue with my servers; however, security by obscurity isn't a very secure option; I use public key authentication only, and denyhosts or fail2ban to block brute force attacks.

---

