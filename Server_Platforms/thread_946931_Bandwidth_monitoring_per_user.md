---
title: "Bandwidth monitoring per user"
date: 2008-10-13
forum: Server Platforms
---

### Post by Aeros84 on 2008-10-13
Now, I know what you're thinking. There are a million threads out there requesting bandwidth monitoring info. Yes, this is absolutely true, I know :P But this is a rather unique case; let me explain:

Our ubuntu server acts as a gateway/cache-proxy between the LAN and the Internet. It therefore obviously has 2 network interfaces, eth0 going to the Net, eth1 going to the LAN. It runs squid as a transparent proxy.

Now comes the tricky part. I need bandwidth usage logs per LAN USER. But not squid reports. Total bandwidth usage per LAN user. In other words, if PersonX browses the web, plays online games (such as CS or whatever they play these days) and uses P2P, I need a bandwidth usage log containing the total for ALL that traffic, i.e., the amount of Internet bandwidth he has used.

Therefore, squid reports won't suffice, since it only shows what he browsed.

It is important to note that, when I say "LAN user", I mean a PC on the lan. They are not users on the Ubuntu box, nor do they have logins on Squid or anything of the kind. They can only be identified by their static IP's. But here comes tricky part #2. They connect from the LAN at eth1, then go through the Ubuntu server gateway, via eth0, to the Internet. I don't know about you, but this stumps me totally. Because if you monitor eth0, can you still identify the origin/destination of the packets and trace it to a LAN IP? I have no idea how to log this information, so I can only hope there is a package out there (preferably web-based logs) that already does this.

Anyway, I'm rambling. I probably said the same thing about 5 times, and am making less and less sense. Just struggling to try explain the problem :P

---

### Post by lykwydchykyn on 2008-10-13
Does this do it for you?
[http://bandwidthd.sourceforge.net/](http://bandwidthd.sourceforge.net/)

---

### Post by Aeros84 on 2008-10-14
Almost, but not quite. With the routing setup the way I have it here, bandwidthD can't differentiate between LAN TCP traffic and WAN TCP traffic, no matter how I set the filters.

---

### Post by iponeverything on 2008-10-14
```

iptables -N outside
iptables -A INPUT -s 0/0 -j outside
iptables -A INPUT -d 0/0 -j outside
netstat -tn |awk '$5 {print $5}' |awk -F\: '{print $1}' | sort | uniq |grep -v Add |grep -v serv|awk '{print "iptables -A outside -s "$1" ; iptables -A outside -d "$1 }'  |sh

```

Then you see the numbers with:

iptables -L -v -n

I think that someone has made a template for cati..

---

### Post by Aeros84 on 2008-10-14
Hm, thanks, but theoretically what are those lines supposed to do, exactly?

---

### Post by iponeverything on 2008-10-14
> **Aeros84 said:**
> Hm, thanks, but theoretically what are those lines supposed to do, exactly?

It parses the output of netstat and then puts the uniq ip addresses that it finds into user defined iptables chain called outside just for the purpose keeping track of traffic for each connection. 

It might work better in your case to parse the the ip addresses in the arp table -- if all the traffic is at least passing through you squid box and all of the hosts are on the same segment as the internal interface.

Another way to do might be just feed the list of vaild internal ip address to iptables from a file and load the rules that way.. 

See these links for the basics of what is going on with accounting with iptables:

ref: [http://wiki.openvz.org/Traffic_accounting_with_iptables](http://wiki.openvz.org/Traffic_accounting_with_iptables)
ref: [http://www.catonmat.net/blog/traffic-accounting-with-iptables/](http://www.catonmat.net/blog/traffic-accounting-with-iptables/)

---

### Post by Aeros84 on 2008-10-16
Thanks :) Will have to figure this out over the course of a couple of weeks, iptables is a bit above me still :P

---

