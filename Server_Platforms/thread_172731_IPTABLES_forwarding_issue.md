---
title: "IPTABLES forwarding issue"
date: 2006-05-09
forum: Server Platforms
---

### Post by honsajons on 2006-05-09
Hi all!

I hope someone can give me an answer on this, because I'm totally clueless. Here's the deal:
I've been trying to set up forwarding for FTP in iptables. Whenever someone connects to port 21/20 to machine A they'll end up at machine B, but will still see it as they're communicating with A.

IP 192.168.16.24 is machine A.
IP 192.168.16.18 is machine B.

Here's a snippet from my rule-set that's loaded on bootup:
-------- SNIP --------

/sbin/iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.16.24
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

echo "1" > /proc/sys/net/ipv4/ip_forward

/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT

/sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 21 -j DNAT --to 192.168.16.18:21
/sbin/iptables -t nat -A PREROUTING -p udp -i eth0 --dport 21 -j DNAT --to 192.168.16.18:21
/sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 20 -j DNAT --to 192.168.16.18:20
/sbin/iptables -t nat -A PREROUTING -p udp -i eth0 --dport 20 -j DNAT --to 192.168.16.18:20

-------- SNAP --------

The rest of the file is (as far as I can see) uninteresting, because it's just firewall rules...and yes, ports 21/20 are accepted. ;)

I've been scratching my head over this for two days now. I can connect to the FTP, log in, but won't get anything back. I.e. I can't list files etc.
I tried adding the following line:
/sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 8080 -j DNAT --to 192.168.16.18:8080
To see if I could get a forwarding to B's webserver, and that worked without a single problem. This leads me to believe there's something wrong with the UDP-forwarding, though that's just a guess.

Anyway, if anyone has some idea about what the problem is, please do tell me, before I go completely insane! I'm running Dapper, if that makes a difference.

---

### Post by cgjones on 2006-05-09
I haven't done too much with iptables manually, so I may be way off track here, but you could try this. I believe for FTP to work through the firewall, you need a couple kernel modules loaded. Click [here](http://www.siliconvalleyccie.com/linux-hn/iptables-intro.htm#_Toc92808873) for more information. If you type the following at the terminal, you can see which modules are currently loaded.
```
lsmod
```
I'm not at my Ubuntu machine right now, so I can't check this first hand, but I would start by seeing if the right modules are loaded.

---

### Post by honsajons on 2006-05-09
That did the trick!

Thanks! You just made my day! :D

---

### Post by cgjones on 2006-05-09
Glad I could help.

---

