---
title: "unable to ssh to client when it is running openvpn"
date: 2010-04-21
forum: Security
---

### Post by joseph.halley on 2010-04-21
Hi guys, I have a virtual private server running ubuntu server edition that I have set up as an openvpn client. The problem I have is that the moment I turn on openvpn, I am no longer able to ssh into the machine. Is there a way to enable me to connect to it even when it is tunneling?

Thanks

---

### Post by cdenley on 2010-04-21
Works fine for me. Is there a conflict with network addressing?
```

ifconfig
route -n

```

---

### Post by joseph.halley on 2010-04-22
Thanks cdenley. This is what the output for route -n looks like:

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
x.x.x.x     0.0.0.0         255.255.254.0   U     0      0        0 eth0
0.0.0.0         x.x.x.x     0.0.0.0         UG    100    0        0 eth0

> **cdenley said:**
> Works fine for me. Is there a conflict with network addressing?
```

ifconfig
route -n

```

---

### Post by joseph.halley on 2010-04-22
Hmm, I have a new problem now. Based on some googling, I added this to my routes:

ip route add x.x.x.x/24 via x.x.x.x dev eth0

now, I am able to connect to the client even when openvpn is turned on, but I am no longer able to surf the web or download pages. I get an 'unable to resolve host address' error. Is my route somehow wrong?

---

### Post by cdenley on 2010-04-22
> **joseph.halley said:**
> Hmm, I have a new problem now. Based on some googling, I added this to my routes:

ip route add x.x.x.x/24 via x.x.x.x dev eth0

now, I am able to connect to the client even when openvpn is turned on, but I am no longer able to surf the web or download pages. I get an 'unable to resolve host address' error. Is my route somehow wrong?

How should I know? All I see are a bunch of X's. What I don't see is any tun interfaces? Are you connected with OpenVPN? Also, you never posted the ifconfig output. If you're having trouble with DNS, post this output as well, after you connect with OpenVPN.
```

cat /etc/resolv.conf

```

---

