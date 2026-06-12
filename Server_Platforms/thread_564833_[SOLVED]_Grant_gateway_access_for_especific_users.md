---
title: "[SOLVED] Grant gateway access for especific users"
date: 2007-10-01
forum: Server Platforms
---

### Post by xyrer on 2007-10-01
Hi, I configured my proxy server to forward telnet from every machine on the local network to an AIX server on another subnet, and now I want to forward internet for SOME computers, I want it to serve as a gateway only for a few specified ip's.

The squid is working all right on port 8080, apache is on 80.
eth0 is my local ip.
eth1 is my public ip.
I know iptables is the answer, but I did this: ```
sudo iptables --table nat  --append POSTROUTING --out-interface eth1 -j MASQUERADE
sudo iptables --append FORWARD -s 192.168.15.1 -j ACCEPT
sudo iptables-save 
```

I don't know if apache is interrupting, but I get no connection from that ip, I'll try to stop apache anyway, but I don't think that's the problem, I can't specify the port because I want that computer to gain access to every kind of traffic.

I appreciate if someone can point my error here.
I'll keep doing some research and tests anyway.

Thanks for your time.

---

### Post by xyrer on 2007-10-01
As I said, I kept looking for info on how to do this, I did it this way:
```

sudo iptables -A FORWARD -i eth0 -s 192.168.15.10 -o eth1 -j ACCEPT
```

along with the first rule I posted before.

---

