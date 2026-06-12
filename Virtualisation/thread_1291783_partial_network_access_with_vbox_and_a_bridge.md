---
title: "partial network access with vbox and a bridge"
date: 2009-10-15
forum: Virtualisation
---

### Post by ugh_bough on 2009-10-15
hey there,

i have a rather messy problem with my vbox 1.5.6 running xp guest on a kubuntu 8.04 host bridged networking. the network is set up like:

sudo tunctl -t tap1 -u besser
sudo brctl addbr br0
sudo brctl addbr br0sudo ifconfig eth0 0.0.0.0 promisc
sudo brctl addif br0 eth0
sudo dhclient br0
sudo ifconfig br0 192.168.1.255 #unused ip
sudo brctl addif br0 tap1
sudo ifconfig tap1 up
sudo chmod 0666 /dev/net/tun
sudo dhclient br0
(got that from [http://www.google.de/search?q=virtualbox+set+system+time&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.de/search?q=virtualbox+set+system+time&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a))

the problem is like:
- from guest i can access internet
- from guest i can ping lan (router, printer, etc.)
- from guest i cannot ping host (the host's lan ip)
- from host i can access internet
- from host i cannot ping lan (router, printer, etc.)
- from host i cannot ping guest (the guests's lan ip)

can you tell what's wrong? strange is that people seem to have either full or no network access while i am having "partial" access?

thx for any pointers.
ugh_bough

---

### Post by ugh_bough on 2009-10-15
doh.
after fixing these lines:

sudo brctl addbr br0
sudo brctl addbr br0sudo ifconfig eth0 0.0.0.0 promisc

to

sudo brctl addbr br0
sudo ifconfig eth0 0.0.0.0 promisc

its now like:
- can ping from within guest: self (lan ip), host, printer, router, internet
- can ping from host: self (lan ip), printer, router, internet
- cannot ping from host: guest

and now check this out:
after telling winxp's firewall to let in icmp echo requests i can ping the guest from the host.  :shock:

so who's gonna kick my a** now for bothering people with this stupid question...
thx anyway for not teaching me about the thread being  such a stupid question...

ugh_bough

---

