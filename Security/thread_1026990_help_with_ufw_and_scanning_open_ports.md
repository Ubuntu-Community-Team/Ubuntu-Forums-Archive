---
title: "help with ufw and scanning open ports"
date: 2008-12-31
forum: Security
---

### Post by nausicaavow on 2008-12-31
Hello,
I have enabled the iptables front-end ufw, and am doing some poking around. Can someone help me with some questions? Here is what I am looking at...

[FONT="Lucida Console"]root@ubuntu:~# ufw status[/FONT]
[SIZE="1"]Status: loaded

To Action From
-- ------ ----
22/tcp ALLOW Anywhere
5353/udp ALLOW Anywhere[/SIZE]

[FONT="Lucida Console"]root@ubuntu:~# netstat -an --program | egrep 0.0.0.0[/FONT]
[SIZE="1"]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      9030/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4879/cupsd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      5139/exim4
udp        0      0 0.0.0.0:42766           0.0.0.0:*                           4802/avahi-daemon:
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           4802/avahi-daemon:[/SIZE]

[FONT="Lucida Console"]root@ubuntu:~# nmap -sS -sU -p U:5353,42766,T:22 192.168.1.200[/FONT]
[SIZE="1"]
Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2008-12-31 18:10 EST
Interesting ports on 192.168.1.200:
PORT STATE SERVICE
22/tcp open ssh
5353/udp open|filtered zeroconf
42766/udp open|filtered unknown[/SIZE]

So on to the questions...
1) Is the netstat command I used guaranteed to identify ALL the listening udp/tcp ports? ( 0.0.0.0 is the external internet? )

2) By using the host IP address (not localhost), nmap is scanning from the perspective of the network? ( like the scan is being run from a different machine on the local network? )

3) So if my firewall is accepting traffic for port 22/tcp and 5353/udp, why isn't nmap reporting port 5353 as open? And, why is it reporting port 42766 at all?

Thanks!

---

### Post by brandon88tube on 2008-12-31
Well my first question is, why have you enabled the root account on your machine? Its not the best practice, but your entitled to do what you want.

Now to answer your questions.
I'm skipping 1 as I'm not sure

2. nmap does not scan the computer you are running nmap on. It scans the router instead. To scan your actual computer you need to run nmap from another computer on the network.
3. nmap might be reporting that they are not open because you are scanning the router instead.

---

### Post by nausicaavow on 2009-01-01
> **brandon88tube said:**
> Well my first question is, why have you enabled the root account on your machine? Its not the best practice, but your entitled to do what you want.

Now to answer your questions.
I'm skipping 1 as I'm not sure

2. nmap does not scan the computer you are running nmap on. It scans the router instead. To scan your actual computer you need to run nmap from another computer on the network.
3. nmap might be reporting that they are not open because you are scanning the router instead.

I believe nmap will scan anything you tell it to. So if 192.168.1.200 is the IP for the local machine, it will scan it.

My router is 192.168.1.1, so I am definitely not scanning the router.

Questions still stand. Anyone else?

---

### Post by Nepherte on 2009-01-01
You will have to run nmap from a different computer than the one you are scanning to get correct results.

---

### Post by Rob_H on 2009-01-01
> **nausicaavow said:**
> 1) Is the netstat command I used guaranteed to identify ALL the listening udp/tcp ports? ( 0.0.0.0 is the external internet? )


Yes, if you run it as sudo. If you want a second opinion, try:
```
sudo lsof -i
```
Regarding nmap, Nepherte is right. Make sure you run nmap on a different computer on the same network to get the best result.

---

### Post by The Cog on 2009-01-03
> nmap does not scan the computer you are running nmap on. It scans the router instead.This is wrong. nmap will scan the address you ask it to. I think you are confusing it with the situation where people behind a NAT router ask a public service to scan them. In such cases, the public service of course has to scan the IP address that the user appears to come from which is the IP address of the NAT router. Whether the NAT router responds directly, passes the scan packets to the users machine, or a different machine, or just drops them depends on how the NAT router is configured.

> You will have to run nmap from a different computer than the one you are scanning to get correct results.Correct. This is because the local firewall almost always allows any packets from itself to itself. Blocking packets from the computer to itself can break lots of normal processes in unexpected ways. I discovered that I couldn't spool any print jobs unless my PC can connect to itself, for instance. So scanning a machine fromn itself doesn't give an accurate picture of what the machine looks like to any other machine in the network.

---

