---
title: "[SOLVED] iptables and apache"
date: 2008-10-19
forum: Server Platforms
---

### Post by TreeFinger on 2008-10-19
I am trying to get my apache server to be visible from the internet. I got the "It works!" page to open from inside my network, but when I ask users to try my IP address in their browser they tell me it doesn't work.

I ran a port scan from one of those websites and it shows port 80 being locked down..

```

                                      desktop computer
My LAN is set up like this:          /
                             Firewall-- desktop computer
                                     \
                                      apache server  

```

I am guessing this is a problem with my firewall and iptables. I entered this line at the command line on the firewall box.
```

iptables -t nat -A PREROUTING -p tcp --dport 80 -i ${WAN} -j DNAT --to internal.ip.of.server

```

That has not done anything though... any suggestions?

I should add that I have not touched the configuration files for apache.

---

### Post by gombadi on 2008-10-19
Have you got a rule in the forward table?
It will need a rule to allow packets or the default rule set to accept.

```

iptables -A FORWARD -p tcp --dport 80 -d internal.ip.of.server -j ACCEPT

```

---

### Post by TreeFinger on 2008-10-19
> **gombadi said:**
> Have you got a rule in the forward table?
It will need a rule to allow packets or the default rule set to accept.

```

iptables -A FORWARD -p tcp --dport 80 -d internal.ip.of.server -j ACCEPT

```

ShieldsUP! still shows port 80 as being stealth

---

### Post by kevdog on 2008-10-20
Is the kernel figured to allow forwarding?

Try:

echo 1 > /proc/sys/net/ipv4/ip_forward on the server


To make it permanent uncomment "net.ipv4.ip_forward=1" in /etc/sysctl.conf

---

### Post by TreeFinger on 2008-10-20
> **kevdog said:**
> Is the kernel figured to allow forwarding?

Try:

echo 1 > /proc/sys/net/ipv4/ip_forward on the server


To make it permanent uncomment "net.ipv4.ip_forward=1" in /etc/sysctl.conf


yea, I have it. my firewall is a router and firewall.

I solved the problem fellas, accepting connections on a different port did the trick. my ISP must block port 80, even tho the tech support person I talked to said they didn't. 

so I can never be sure if it is my fault or theirs :lolflag:

---

### Post by jgraham95 on 2011-07-27
> **TreeFinger said:**
> yea, I have it. my firewall is a router and firewall.

I solved the problem fellas, accepting connections on a different port did the trick. my ISP must block port 80, even tho the tech support person I talked to said they didn't. 

so I can never be sure if it is my fault or theirs :lolflag:

M8 its certainly down to your configuration somewhere blocking http traffic.

No ISP in their right mind would ever block port 80 as its the port used for web browsing. So if port 80 is blocked you cant browse web pages. Tho on the insanely low chance they have blocked it, change ISP's as they would be a bunch of clueless cowboys.

---

