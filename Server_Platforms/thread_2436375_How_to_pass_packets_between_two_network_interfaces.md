---
title: "How to pass packets between two network interfaces through manually written filter?"
date: 2020-02-05
forum: Server Platforms
---

### Post by 4ook on 2020-02-05
Hi All, 
I have two physical network adapters on the Linux machine: eth0 and eth1. eth0 is for users and eth1 has outer Network access.  Then I can do iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE and users can connect to Network behind the NAT.
  What I want to do: manually capture packets from eth0, inspect it  (may be making some changes, dump etc.) and write back to eth1.  Something like this:

user --- [eth0 ----- (tap0 - my program - tap1) ----- eth1] --- Network

I've written a program, that opens tap0 and tap1, simply read from  tap0 and write to tap1 and vice versa (no packet changes for now):
tap0 192.168.100.1
tap1 192.168.200.1
Then: 
  ip route add <outer network IP> via 192.168.100.1
iptables -t nat -A POSTROUTING -o tap0 -j MASQUERADE
  I also tried:
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
I see ARP requests incoming on tap0, and outgoing from tap1 (repeated by my program), but nothing more.

  **How to make this packets to go to eth1? How to make all  incoming packets on eth0 to go through my filter and to outer network  (not only specific address)?**

---

### Post by TheFu on 2020-02-05
There are a number of Linux Router how-to guides.   I don't see any mention of the kernel setting to allow packet forwarding.
/etc/sysctl.conf:net.ipv4.ip_forward=1

I'd think that was required.

---

### Post by 4ook on 2020-02-05
> **TheFu said:**
> There are a number of Linux Router how-to guides.   I don't see any mention of the kernel setting to allow packet forwarding.
/etc/sysctl.conf:net.ipv4.ip_forward=1
It's allowed. As I mention, router mode works fine. I need something more, then simply route packets: push the packets through my program.

---

### Post by TheFu on 2020-02-05
> **4ook said:**
> It's allowed. As I mention, router mode works fine. I need something more, then simply route packets: push the packets through my program.

Long, long, ago, I modified an ethernet driver to modify packets containing certain patterns. The guide was in a Linux Journal.  Then I forgot about my changes until a recruiter noticed that all mentions of a specific software company were misspelled. It had been enough months that it took me a day or two to remember the network driver changes.  OTOH, I did get lots of job offers that round by accidentally demonstrating my driver hacking.  ;)

Anyways, if you don't find a more portable answer, you can always modify the NIC driver code.  [https://lwn.net/Kernel/LDD2/ch00.lwn](https://lwn.net/Kernel/LDD2/ch00.lwn) has a reference to someone I bet wrote the article I followed.

---

### Post by 4ook on 2020-02-05
Thank you for an idea. 
But I need to do this from userspace. I need robast solution, not tied to specific interface driver. For example, it should work with wlan--tap0---tap1--eth an so on.

---

### Post by TheFu on 2020-02-05
> **4ook said:**
> Thank you for an idea. 
But I need to do this from userspace. I need robast solution, not tied to specific interface driver. For example, it should work with wlan--tap0---tap1--eth an so on.

As you say,  didn't think it would be the best solution.
 [https://nostarch.com/firewalls.htm](https://nostarch.com/firewalls.htm) is an IPtables book that probably has the answer.

---

### Post by Doug S on 2020-02-06
> **4ook said:**
> Hi All, 
I have two physical network adapters on the Linux machine: eth0 and eth1. eth0 is for users and eth1 has outer Network access.  Then I can do iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE and users can connect to Network behind the NAT.
  What I want to do: manually capture packets from eth0, inspect it  (may be making some changes, dump etc.) and write back to eth1.  Something like this:

user --- [eth0 ----- (tap0 - my program - tap1) ----- eth1] --- Network

I've written a program, that opens tap0 and tap1, simply read from  tap0 and write to tap1 and vice versa (no packet changes for now):
tap0 192.168.100.1
tap1 192.168.200.1
What are the sub-net masks? I am assuming those are two different sub-nets, perhaps with a 24 bit mask? What are the IP addresses of eth0 and eth1, the same or different?
> **4ook said:**
> 
Then: 
  ip route add <outer network IP> via 192.168.100.1
iptables -t nat -A POSTROUTING -o tap0 -j MASQUERADE
  I also tried:
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
I think the "-o eth1" version is the desired one, but am not sure.
> **4ook said:**
> 
I see ARP requests incoming on tap0, and outgoing from tap1 (repeated by my program), but nothing more.
Well, if 192.168.100.1 and 192.168.200.1 are indeed different sub-nets then, they shouldn't. ARP packets should not span sub-nets.
> **4ook said:**
> 
  **How to make this packets to go to eth1? How to make all  incoming packets on eth0 to go through my filter and to outer network  (not only specific address)?**
That part I do not know. While I have a similar setup, I only capture all traffic on eth0 and eth1 using tcpdump, and post process it at a later date, and only in great detail as a followup investigation into network events. I never manipulate the packets in real time outside of available iptables rules for doing so.

---

### Post by 4ook on 2020-02-10
A good solution for my problem is not using tap interface at all but using NFQUEUE.

```

iptables -t mangle -A PREROUTING -i eth0 -j NFQUEUE --queue-num 0
iptables -t mangle -A POSTROUTING -o eth0 -j NFQUEUE --queue-num 0

```

This redirects a packets to a queue that may be opened from application. Than I can accept, drop or modifiy each packet as described here: [https://www.apriorit.com/dev-blog/598-linux-mitm-nfqueue](https://www.apriorit.com/dev-blog/598-linux-mitm-nfqueue)

Thanks to all.

---

