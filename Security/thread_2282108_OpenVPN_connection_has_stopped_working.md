---
title: "OpenVPN connection has stopped working"
date: 2015-06-11
forum: Security
---

### Post by Kingskid on 2015-06-11
> **matija5 said:**
> This solutin also worked for me (Ubuntu 14.04 LTS)!!!

I'm running into this trouble too with little to no success (Ubuntu 14.04 LTS). I should mention, that I don't possess any knowledge of networks etc.
After long discussion on another forum the problem was solved in a different way. When I connected to the VPN I typed the following commands into terminal:

```
ip r r default via 192.168.0.1

ip r a 10.0.0.0/8 via 10.1.1.21
```

Suddenly I got the local internet connection working at same time with being connected to client's server through VPN. I need it like that as the internet connection through the VPN is terribly slow to do any online search so I need to do online search on my local computer.
However, just few weeks later this solutions doesn't work. It ends up with message "network unreachable" and both internet connections (local and VPN) get stuck.

Would there be a possibility to explain in a simple terms (as I said earlier I don't understand networks) how to set up my computer so I can have VPN running and still having local connection to the internet for online searching available?

---

### Post by cariboo on 2015-06-11
Moved to a thread of it's own, as the version used in the original thread is no longer supported.

---

### Post by SeijiSensei on 2015-06-12
Run the VPN program, then type the command "ifconfig" in a terminal.  You'll see an entry like this:

```
tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.1.1.20  P-t-P:10.1.1.1  Mask:255.255.255.255

```

This says that my end of the VPN connection has the address 10.10.1.20, and the other end has the address 10.1.1.1 (using the "point-to-point" method of routing).  What do you get?  In particular, do you see 10.1.1.21 as the remote address?  If you type "ping 10.1.1.21" do you get a response?

The commands you listed tell your machine to use 10.1.1.21 as the address for the remote server and to send any traffic for addresses beginning with 10 to that machine.  The first line tells your machine to use 192.168.0.1 as your "default gateway." This is probably the address of the router in your home or office.  Then your machine knows to send packets for anything in 10.x to the remote VPN server, and anything else outside of 192.168.0.x to the router to be forwarded along to the Internet.

---

