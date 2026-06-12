---
title: "Transparent Proxy / Gateway"
date: 2006-08-24
forum: Server Platforms
---

### Post by Mithrilhall on 2006-08-24
I was wondering if anyone can help me setup a transparent proxy (Squid or Tinyproxy).

My current setup is:

Internet <--> (K)Ubuntu <--> Switch <--> Computers

My (K)Ubuntu server has two NICs (eth0 & eth1). The two NICs have static IP addresses (eth0 is 10.2.176.2 and eth1 is 10.2.176.3). My network is 10.2.176.0/24 and 10.2.176.2 - 10.2.176.10 are reserved so the computers will start pulling IP addresses beginning at 10.2.176.11.

I want all web traffic to go through my proxy server but I'm not sure how to go about doing this (iptables?).

---

### Post by mgor on 2006-08-24
"Transparent proxies via Squid." 
[http://www.debian-administration.org/articles/71](http://www.debian-administration.org/articles/71)

and if you want to spice it up a bit,
[http://www.ex-parrot.com/~pete/upside-down-ternet.html](http://www.ex-parrot.com/~pete/upside-down-ternet.html)

---

### Post by tomski on 2006-08-25
I have a port forwarding issue
here is my setup(i have added the relevant shorewall zones in():

internet<PPPoA>DSLrouter(net)<socket1<-->eth0>ubuntugateway(fw)<eth1<-->eth0>mypc(loc)

i have Amule installed on the gateway(fw) & i have added the following shorewall ACCEPT line to allow it to access the web & vice versa:

AllowEdonkey    net    fw
AllowEdonkey    fw     net

i have check the shorewall script this line calls & it is listing all ports for TCP 4661,4662 & UDP 4672
i have even added a seperate line for each port but that produced the same results so i have commented those out & just stick with the first set

I know this is a double NAT situation, but i have added the MAC address of the netcard(eth0) on the gateway(fw) to a DMZ on the dslrouter so in effect all ports are forwarded to gateway(fw)

problem is when i start up Amule i allways have a lowid even though i am sharing about 5 GB of files(set to 'Release') & i have opened the ports on gateway

any ideas

---

### Post by dia3olik on 2007-03-31
Hi tomski,
i'm in EXACTLY the SAME situation as you!
How did you solve this issue?
Thanks a lot!
Tommy

---

