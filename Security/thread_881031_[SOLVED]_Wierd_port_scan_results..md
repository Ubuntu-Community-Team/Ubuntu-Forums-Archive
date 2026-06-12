---
title: "[SOLVED] Wierd port scan results."
date: 2008-08-05
forum: Security
---

### Post by mczonie on 2008-08-05
Yesterday I did a port scan on shields up, and it showed all stealth ports. Today I ran a scan and it showed mostly closed ports with a few stealth ports (still no open ports.)

Any idea what's going on here and why there was such a big change in only a day? 

TIA.

---

### Post by Qchan on 2008-08-05
> **mczonie said:**
> Yesterday I did a port scan on shields up, and it showed all stealth ports. Today I ran a scan and it showed mostly closed ports with a few stealth ports (still no open ports.)

Any idea what's going on here and why there was such a big change in only a day? 

TIA.

[b][color=darkred]
Using a router?
Well, that's why.
[/b][/color]

---

### Post by mczonie on 2008-08-05
> **Qchan said:**
> [b][color=darkred]
Using a router?
Well, that's why.
[/b][/color]

What's a router?

---

### Post by Qchan on 2008-08-05
> **mczonie said:**
> What's a router?

[b][color=darkred]It could be part of your modem designed to give you access to the Internet. Its designed to protect you from hackers and predators of the Internet.
[/b][/color]

---

### Post by mczonie on 2008-08-05
> **Qchan said:**
> [b][color=darkred]It could be part of your modem designed to give you access to the Internet. Its designed to protect you from hackers and predators of the Internet.
[/b][/color]

I know open ports are bad, but what's the difference between a stealth port and a closed port? Are they both safe?

---

### Post by cdenley on 2008-08-05
I think "stealthed" means traffic for that port is being dropped, or your computer doesn't send any response at all. Then "closed" would mean that the traffic on that port is being rejected, or your system/network sends a reply that it will not do anything with it. Not really much of a difference between the two. It could mean your firewall started rejecting traffic instead of dropping it for some reason, or that there is no firewall anymore or the firewall is disabled for those ports and your computer is rejecting the traffic since you have no processes listening on those ports.

stealth = dropped
closed = rejected

If you want to see for yourself...
```

cdenley@ubuntu:~$ sudo iptables -I INPUT -p tcp --dport 12345 -j REJECT
cdenley@ubuntu:~$ telnet localhost 12345
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
cdenley@ubuntu:~$ sudo iptables -I INPUT -p tcp --dport 12345 -j DROP
cdenley@ubuntu:~$ telnet localhost 12345
Trying 127.0.0.1...

cdenley@ubuntu:~$ sudo iptables -D INPUT 1
cdenley@ubuntu:~$ sudo iptables -D INPUT 1

```
The second telnet connection never gets rejected, so it just keeps waiting for a response (I had to kill it using ctrl+c).

---

