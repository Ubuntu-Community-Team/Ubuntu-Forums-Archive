---
title: "UFW is blocking connections even though it's set to allow for In/Out"
date: 2011-08-01
forum: Security
---

### Post by MechaMechanism on 2011-08-01
I might be misunderstanding the log but it looks like UFW is blocking connections.  I want to allow all incoming and outgoing.  I guess what I'm saying is that the servers on my computer will open ports but all other ports should respond with closed just like a default Ubuntu install.  Trying to use UFW to monitor connections without really doing any firewalling.

```
Aug  1 07:14:07 universal-mechanism kernel: [311111.963762] [UFW BLOCK] IN=eth0 OUT= MAC=00:1f:c6:8a:e9:66:00:01:5c:32:f4:c1:08:00 SRC=72.21.203.146 DST=174.44.178.56 LEN=40 TOS=0x00 PREC=0x00 TTL=233 ID=51984 DF PROTO=TCP SPT=80 DPT=54466 WINDOW=8201 RES=0x00 RST URGP=0 
```

---

### Post by ajgreeny on 2011-08-01
> **MechaMechanism said:**
> I might be misunderstanding the log but it looks like UFW is blocking connections.  I want to allow all incoming and outgoing.  I guess what I'm saying is that the servers on my computer will open ports but all other ports should respond with closed just like a default Ubuntu install.  Trying to use UFW to monitor connections without really doing any firewalling.

```
Aug  1 07:14:07 universal-mechanism kernel: [311111.963762] [UFW BLOCK] IN=eth0 OUT= MAC=00:1f:c6:8a:e9:66:00:01:5c:32:f4:c1:08:00 SRC=72.21.203.146 DST=174.44.178.56 LEN=40 TOS=0x00 PREC=0x00 TTL=233 ID=51984 DF PROTO=TCP SPT=80 DPT=54466 WINDOW=8201 RES=0x00 RST URGP=0 
```
I don't know how to answer your monitoring problem but you can reset iptables to the default with the terminal command ```
sudo iptables -F 
```then you can look a bit further into the problem.

---

### Post by bodhi.zazen on 2011-08-01
> **MechaMechanism said:**
> I might be misunderstanding the log but it looks like UFW is blocking connections.  I want to allow all incoming and outgoing.  I guess what I'm saying is that the servers on my computer will open ports but all other ports should respond with closed just like a default Ubuntu install.  Trying to use UFW to monitor connections without really doing any firewalling.

```
Aug  1 07:14:07 universal-mechanism kernel: [311111.963762] [UFW BLOCK] IN=eth0 OUT= MAC=00:1f:c6:8a:e9:66:00:01:5c:32:f4:c1:08:00 SRC=72.21.203.146 DST=174.44.178.56 LEN=40 TOS=0x00 PREC=0x00 TTL=233 ID=51984 DF PROTO=TCP SPT=80 DPT=54466 WINDOW=8201 RES=0x00 RST URGP=0 
```

Well, turn ufw off and use iptables =)

iptables -A INPUT -j LOG

see man iptables for logging options.

You will soon find the sheer number of packets overwhelming, so, better to either monitor your server logs or use snort.

For example, see:

[http://blog.bodhizazen.net/linux/ssh-logs-as-a-honeypot/](http://blog.bodhizazen.net/linux/ssh-logs-as-a-honeypot/)

grep / awk and your logs will generate useful information as well, probably more useful then ufw/iptables.

Typically one logs iptables for debugging a set of rules.

---

