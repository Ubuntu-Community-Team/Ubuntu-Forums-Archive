---
title: "iptables and transparent proxy! can I forward just one site past squid?"
date: 2007-08-09
forum: Server Platforms
---

### Post by czJake on 2007-08-09
I  have a squid transparent proxy up and running.
It's squid 2.6 on server 7.04.
Here is my bridge script.

ifconfig eth0 0.0.0.0 promisc up
ifconfig eth1 0.0.0.0 promisc up

brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1

ifconfig br0 10.0.75.2 netmask 255.255.255.0 up
route add default gw 10.0.75.1 dev br0

ebtables -t broute -A BROUTING -p IPv4 --ip-protocol 6 --ip-destination-port 80 -j redirect --redirect-target ACCEPT
iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 -j REDIRECT --to-port 3128


Everything works fine *BUT* one site.
[www.fnams.com](www.fnams.com) :mad:
It will not render in IE or firefox on windows. It works in Opera but I can't switch my clients over. There is no error message anywhere in the logs or in the browser.

Is it possible to just use iptables to straight pass this site without it ever touching squid??

---

