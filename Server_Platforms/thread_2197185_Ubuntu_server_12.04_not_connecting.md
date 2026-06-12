---
title: "Ubuntu server 12.04 not connecting"
date: 2014-01-02
forum: Server Platforms
---

### Post by liste on 2014-01-02
I have just installed Ubuntu server 12.04 on my old computer.  I used a static IP during the setup: 192.168.0.92.

Ping that address from another device gives me "ping: sendto: Host is down".  Pinging the router from Ubuntu server gives me "connect: Network is unreachable".  

An ifconfig does not reveal my eth0, but an ifconfig -a does.  ip link also reveals "eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
link/ether 00:48:54:6e:c0:a3 brd ff:ff:ff:ff:ff:ff" as well as similar for lo and virbr0 entries.

My cables are plugged in, and lspci does show my Ethernet card.  "01:0d.0 Ethernet controller: Realtek  Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)".

I have tried the network card in another computer running XUbuntu 10.10, and it works, so my card is functional.  I have also tried several other Ethernet cards in the Ubuntu server, and none of them work.  When I was installing Ubuntu server, it did not manage to detect my internet, so I had to do a manual setup.

What other information could be useful for resolving this problem?  Thanks!

---

### Post by liste on 2014-01-02
Hi again,

After 5 hours of trying all sorts of things from Ubuntu terminal, I finally discovered that it was a BIOS setting that I had to change.  After reading this thread: [http://www.linuxquestions.org/questions/ubuntu-63/ubuntu11-10-network-autoconfiguration-failed-908709/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu11-10-network-autoconfiguration-failed-908709/) I changed "reset configuration data" to "true".  Now everything works as it should!

---

### Post by Iowan on 2014-01-02
Are we  [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

### Post by liste on 2014-01-02
Yes, it's solved. Thanks for the reply.  Did that mark it as solved?  It's not easy to tell from the mobile website.

---

### Post by Iowan on 2014-01-02
No, that's how YOU could mark it [SOLVED]. 
I'll get it, this time... ;)

---

