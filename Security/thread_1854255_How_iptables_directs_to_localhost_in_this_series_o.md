---
title: "How iptables directs to localhost in this series of iptable rules"
date: 2011-10-04
forum: Security
---

### Post by narnie on 2011-10-04
Hello,

I have implimented a dansguardian system using dansguardian and privoxy. I borrowed a script from Ubuntu CE that makes it where a firewall program like firehol is not needed and it doesn't need a reconfigure of the proxy settings in browsers to be changed. I really like it that way. All is working well from that standpoint. I want to fully understand HOW it works on the iptables rules, though. I have most of it. Included is the code from my /etc/init.d/dansguardian_firewall init routine. Above this, I am going to make comments and ask questions. What I ask is for someone to help me understand fully how it works, esp the postrouting nat and output nat rules that are the business end of sending all web requests to localhost where it can be managed by Dansguardian.

The setup is on a single computer like so:

client browser -> iptables -> Dansguardian -> privoxy -> Linksys home router -> outside world internet

# I understand this flushes any -t filter rules

iptables -F

# This removes any user-created chains in -t filter

iptables -X

# This flushes any -t nat chain rules

iptables -t nat -F

# This removes and user-created -t nat chains

iptables -t nat -X

# This flushes -t mangle

iptables -t mangle -F

# This removes user-created -t mangle chains

iptables -t mangle -X

# This sets the firewall policies on FORWARD to accept, not sure what FORWARD does. Any explaination would be appreciated. 

iptables -P FORWARD ACCEPT

# This sets the firewall policy to accept all outbound traffic 

iptables -P OUTPUT ACCEPT

# Here is where I start having a lot of trouble. What is the postrouting mean verses prerouting, etc? What is the -t nat doing actually? Is -o because it is being directed to localhost (127.0.0.1). I understand -p tcp that this limits it to the tcp protocol (not UDP or both). --dport is short for -m tcp --dport 8080 to cause it to direct it to port 127.0.0.1:8080 where dansguardian is listening. What is -j SNAT --to 127.0.0.1 exactly doing? How is it directing to localhost in the first place? Why does it go on POSTROUTING instead of OUTPUT?

iptables -A POSTROUTING -t nat -o lo -p tcp --dport 8080 -j SNAT --to 127.0.0.1

# This is saying to make request not by root and not to 127.0.0.1 to route port 80 direct to localhost 8080 where dansguardian is listening, right? Further elaboration is appreciated. If this is so, it would make more sense to me to have this rule before the previous rule. Does it matter? If so, why? Why is it on OUTPUT and not POSTROUTING?

iptables -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -j REDIRECT --to-ports 8080

# Sets the policy on incoming connects to DROP (modified by the rules below)

iptables -P INPUT DROP

# This makes inbound request to localhost accepted. Why is this necessary? If this isn't included, then web sites won't load. I'm sure it has to do with dansguardian working over localhost, but please give me a more full understanding.

iptables -A INPUT -i lo -j ACCEPT

# Here is something I really don't undrstand. If this rule isn't included, allowed and blocked web sites won't load. I removed the RELATED, and it still loaded. I removed just the ESTABLISHED, and it wouldn't load. What is it that is established that it is accepting? Much elaboration needed here.

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

#I wrote many of these rules below and understand why they work. It is looking for new connect attempts to those ports that are needed for various services (I dn't run a web or mail server, so I don't leave those open).

## Open port for ssh server (22), web server (80), and mail server (25)
iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT
#iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
#iptables -A INPUT -p tcp --dport 25 -m state --state NEW -j ACCEPT

## Uncomment below to open NSF port, edit the port accoring actual setting
iptables -A INPUT -p tcp --dport 111 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 111 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 2049 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 2049 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 4045 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 4045 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 32771 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 32771 -m state --state NEW -j ACCEPT
## Open ports for NSF end

#Accept Ping request
iptables -A INPUT -p icmp -j ACCEPT

## Drop other packets, Logging, and closing firewall.

#What is this rule actually doing?

iptables -A INPUT -d 255.255.255.255/0.0.0.255 -j DROP

#What is this rule actually doing?

iptables -A INPUT -d 224.0.0.1 -j DROP

#What is this rule actually doing?

iptables -A INPUT -j LOG

#What is this rule actually doing?

iptables -A INPUT -j REJECT

Further explaination is much appreciated.

Kind Regards,
Narnie

```

#!/bin/bash
### BEGIN INIT INFO
# Provides: dansguardian_firewall
# Required-Start: $remote_fs $syslog
# Required-Stop: $remote_fs $syslog
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: firewall
# Description: Start, stop or reload firewall.
### END INIT INFO
#cat /etc/init.d/dansguardian_firewall

set -e

case "$1" in
start)
echo -e "\nStarting Ubuntu CE firewall .....\n"
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -A POSTROUTING -t nat -o lo -p tcp --dport 8080 -j SNAT --to 127.0.0.1
iptables -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -j REDIRECT --to-ports 8080
iptables -P INPUT DROP
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

## Open port for ssh server (22), web server (80), and mail server (25)
iptables -A INPUT -p tcp --dport 50505 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 25 -m state --state NEW -j ACCEPT

## Uncomment below to open NSF port, edit the port accoring actual setting
iptables -A INPUT -p tcp --dport 111 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 111 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 2049 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 2049 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 4045 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 4045 -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 32771 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 32771 -m state --state NEW -j ACCEPT
## Open ports for NSF end

#Accept Ping request
iptables -A INPUT -p icmp -j ACCEPT

## Drop other packets, Logging, and closing firewall.
iptables -A INPUT -d 255.255.255.255/0.0.0.255 -j DROP
iptables -A INPUT -d 224.0.0.1 -j DROP
iptables -A INPUT -j LOG
iptables -A INPUT -j REJECT
;;

stop)
echo -e "\nFlushing firewall and setting default policies to ACCEPT\n"
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
;;

status)
echo "FILTER POLICY"
iptables -L
echo ; echo "NAT POLICY"
iptables -t nat -L
;;

restart|force-reload)
$0 stop
$0 start
;;
*)
echo "Usage: /etc/init.d/ubuntu_ce_firewall {start|stop|restart|force-reload|status}"
exit 1
;;
esac


```

---

### Post by Dangertux on 2011-10-04
That's a lot of questions. I suggest you read this it will help you. [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

I also subscribed to this thread and when I am at a computer (instead of a phone) I will come back and answer as many of them as I can directly if nobody else has. However that link should give you the info you need to understand your rules better.

Basically this bit here is where the redirect occurs 

```

iptables -A POSTROUTING -t nat -o lo -p tcp --dport 8080 -j SNAT --to 127.0.0.1
iptables -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -j REDIRECT --to-ports 8080

```

The first line is taking from the nat table in the POSTROUTING(packets from other systems on the network)chain being sent on loopback interface (localhost) of type tcp to port 8080 and changing Their source ip to localhost. 

The second rule is anything in the nat table not from localhost of typ tcp bound for port 80 owned by root will be redirected to port 8080. 

Hope this helps will give more concise answer later hard to type on iPhone at 230 am :-p

---

### Post by narnie on 2011-10-04
> **Dangertux said:**
> That's a lot of questions. I suggest you read this it will help you. [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

I also subscribed to this thread and when I am at a computer (instead of a phone) I will come back and answer as many of them as I can directly if nobody else has. However that link should give you the info you need to understand your rules better.

Great! Thanks for the tutorial tip. I'll head there now as I was going to be looking for tutorials, too. Understanding firewalls has always been on my list, just now ready to hunker down and put my learning cap on. Thanks for any additional info you might provide later.

Kind Regards,
Narnie

---

### Post by Dangertux on 2011-10-04
Ok now I will try to answer the questions you originally posted more in depth. Sorry for the delay it's been hectic at work for me :-/

> 
# Here is where I start having a lot of trouble. What is the postrouting  mean verses prerouting, etc? What is the -t nat doing actually? Is -o  because it is being directed to localhost (127.0.0.1). I understand -p  tcp that this limits it to the tcp protocol (not UDP or both). --dport  is short for -m tcp --dport 8080 to cause it to direct it to port  127.0.0.1:8080 where dansguardian is  listening. What is -j SNAT --to 127.0.0.1 exactly doing? How is it  directing to localhost in the first place? Why does it go on POSTROUTING  instead of OUTPUT?

iptables -A POSTROUTING -t nat -o lo -p tcp --dport 8080 -j SNAT --to 127.0.0.1
This rule would be read as append to chain POSTROUTING table nat, output interface localhost bound to port 8080 type tcp change the source ip address to 127.0.0.1. The difference between POSTROUTING and PREROUTING is the origin of the packets essentially PREROUTING is from outside the network. POSTROUTING is from inside the network. It goes on POSTROUTING because it is likely from one of the system's behind the router.

> 
# This is saying to make request not by root and not to 127.0.0.1 to route port 80 direct to localhost 8080 where dansguardian  is listening, right? Further elaboration is appreciated. If this is so,  it would make more sense to me to have this rule before the previous  rule. Does it matter? If so, why? Why is it on OUTPUT and not  POSTROUTING?

iptables -A OUTPUT -t nat ! -d 127.0.0.1 -p tcp --dport 80 -m owner ! --uid-owner root -j REDIRECT --to-ports 8080
This is appending to chain OUTPUT table nat any packet that is NOT bound for localhost but bound to port 80 of type tcp NOT owned by root, should be redirected to port 8080 where dansguardian listens. This matters because the previous rule matched only packets output on the localhost interface, this is also why it is in the OUTPUT chain because we want to match packets outbound from other interfaces too, such as eth1 etc.

> 
# Here is something I really don't undrstand. If this rule isn't  included, allowed and blocked web sites won't load. I removed the  RELATED, and it still loaded. I removed just the ESTABLISHED, and it  wouldn't load. What is it that is established that it is accepting? Much  elaboration needed here.

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
This is quite simply just saying keep connections that are currently open and connections associated to them alive. Nothing more, it's blocking probably has more to do with how you were refreshing the pages to see if they loaded than the rule itself.

> 
#What is this rule actually doing?
iptables -A INPUT -d 255.255.255.255/0.0.0.255 -j DROP


Drops broadcast packets.

> 
#What is this rule actually doing?

iptables -A INPUT -d 224.0.0.1 -j DROP
Dropping multicast  group packets.

> 

#What is this rule actually doing?
iptables -A INPUT -j LOG
Logging all traffic on the INPUT chain.

> 
#What is this rule actually doing?
iptables -A INPUT -j REJECT
Rejecting (TCP RST) all traffic on the INPUT chain.

I think that answers them all , if I missed something or you're still unclear feel free to ask.

---

### Post by narnie on 2011-10-04
> **Dangertux said:**
> Ok now I will try to answer the questions you originally posted more in depth. Sorry for the delay it's been hectic at work for me :-/

Dangertux,

Thanks so much for taking your time and putting the effort into helping me on this. This isn't what I would call a delay at all. You are so kind to take me under your wing.

> 
This rule would be read as append to chain POSTROUTING table nat, output interface localhost bound to port 8080 type tcp change the source ip address to 127.0.0.1. The difference between POSTROUTING and PREROUTING is the origin of the packets essentially PREROUTING is from outside the network. POSTROUTING is from inside the network. It goes on POSTROUTING because it is likely from one of the system's behind the router.

Oh, I think I get why this is important. If you don't do it, someone could change their browser proxy to point to local host and bypass this way if they pointed to 8080. On second thought, I don't get it. If it is already outbound to lo, isn't it's IP already 127.0.0.1? And dansguardian is already listening on lo:8080? As you can see, I have a long way to go on understand NAT.

I added another rule to prevent changing the proxy on a browser to jump over dansguardian so it drops all packets not sent by dansguardian itself:

```
iptables -A OUTPUT -d 127.0.0.1 -p tcp --dport 8118 -m owner ! --uid-owner dansguardian -j DROP
```

> This is appending to chain OUTPUT table nat any packet that is NOT bound for localhost but bound to port 80 of type tcp NOT owned by root, should be redirected to port 8080 where dansguardian listens. This matters because the previous rule matched only packets output on the localhost interface, this is also why it is in the OUTPUT chain because we want to match packets outbound from other interfaces too, such as eth1 etc.


So this is capturing anything not going to localhost, like a request to open google.com's IP. It will redirect that request to localhost on the port where dansguardian is listening (lo:8080). Does the order of the last two rules really matter? How does it "remember" on the other side of dansguardian to go the the original requested IP number so privoxy can go fetch it?

> This is quite simply just saying keep connections that are currently open and connections associated to them alive. Nothing more, it's blocking probably has more to do with how you were refreshing the pages to see if they loaded than the rule itself.

Ic, some caching or something was going on? I thought I had understood it, but the behaviour made me wonder. I guess it was just dodgy how I was reloading it.

> Drops broadcast packets.

Can you help me understand what a broadcast packet is and why it is important to drop them?

> Dropping multicast  group packets.

Same for multicast packets

> Logging all traffic on the INPUT chain.

Makes complete sense

> Rejecting (TCP RST) all traffic on the INPUT chain.
What is TCP RST and why reject (and send a message back) instead of drop?

> I think that answers them all , if I missed something or you're still unclear feel free to ask.

You did hit them all, and thank you for your patience. I'm am absorbing the site you sent and it is very helpful. I'm eagerly lapping it up. I appreciate its links to more detail info. I think I'm just wanting to learn too much too soon and I'm on the shallow end of the learning curve where I don't have the knowledge base to get it all and it is hard to know then where to start. You have been MOST helpful. Please let me know if my understandings were wrong.

Kindly,
Narnie

---

### Post by Dangertux on 2011-10-04
Thank you, your words are very flattering. :-)

Now on to the questions ;-)

> 
Oh, I think I get why this is important. If you don't do it, someone  could change their browser proxy to point to local host and bypass this  way if they pointed to 8080. On second thought, I don't get it. If it is  already outbound to lo, isn't it's IP already 127.0.0.1? And  dansguardian is already listening on lo:8080? As you can see, I have a  long way to go on understand NAT.
This is a catch all , because of the way certain services listen. IE : 0.0.0.0:8080 is ALL interfaces on 8080, so it COULD be bound for localhost but originated from 192.168.1.1 if that makes sense. If your service listened on 127.0.0.1:8080 this wouldn't matter so much, but it's designed to make up for misconfigured services. 

> 
So this is capturing anything not going to localhost, like a request to  open google.com's IP. It will redirect that request to localhost on the  port where dansguardian is listening (lo:8080). Does the order of the  last two rules really matter? How does it "remember" on the other side  of dansguardian to go the the original requested IP number so privoxy  can go fetch it?
As far as I can tell the order doesn't really matter since it is unlikely a packet will match BOTH rules. That being said it could be some anomalous situation (I've also never run the set up you're trying to do so can't speak from experience) my only advice is to experiment and see if it makes a difference. It doesn't have to remember the original IP because that is never changed, that is changed with DNAT not SNAT, SNAT changes the source IP so that it can get back to privoxy, if that makes sense.

> 
Ic, some caching or something was going on? I thought I had understood  it, but the behaviour made me wonder. I guess it was just dodgy how I  was reloading it.
Because of the way the rule was written ESTABLISHED,RELATED. If you simply reloaded the page by refreshing the connection was likely still in an established state, thus is matched the ACCEPT rule and was allowed. Now if you closed your browser and waited a moment the connection would reset and no longer be in an ESTABLISHED state and would not match the rule, thus would have gone through your firewall rules normally.

> 
Can you help me understand what a broadcast packet is and why it is important to drop them?
Broadcast is actually an address as you can see above, basically if you ping that address ; any machine in the group running the broadcast service will respond. This is a security thing, it can help an attacker in determining the layout of the network. It can also be used to troubleshoot network failure on large networks. It's a personal preference for the administrator, it was likely added as it is considered best practices to disable it. It can also be used by a malicious attacker to carry out some types of denial of service attacks.

> 
Same for multicast packets


Same concept as above, IGMP multicast is used in discovery of multicast capable routers.

> 
What is TCP RST and why reject (and send a message back) instead of drop?
TCP RST stands for reset, it basically tells the machine requesting a connection that no connection will be accepted. Reject is used instead of dropping on many proxy and router implementations because you want traffic to flow smoothly. If you DROP the packet the machine sending it may try many more times, causing a delay. Since it is not really a security concern to reject instead of drop it is used for performance sake.

That should be all of them for now, feel free to ask if you have any others. I'm glad you're enjoying your endeavors with firewalls/routing. Thanks again for the kind words.

Regards
Adam

---

### Post by narnie on 2011-10-05
> **Dangertux said:**
> Thank you, your words are very flattering. :-)

Now on to the questions ;-)

This is a catch all , because of the way certain services listen. IE : 0.0.0.0:8080 is ALL interfaces on 8080, so it COULD be bound for localhost but originated from 192.168.1.1 if that makes sense. If your service listened on 127.0.0.1:8080 this wouldn't matter so much, but it's designed to make up for misconfigured services. 

As far as I can tell the order doesn't really matter since it is unlikely a packet will match BOTH rules. That being said it could be some anomalous situation (I've also never run the set up you're trying to do so can't speak from experience) my only advice is to experiment and see if it makes a difference. It doesn't have to remember the original IP because that is never changed, that is changed with DNAT not SNAT, SNAT changes the source IP so that it can get back to privoxy, if that makes sense.

Because of the way the rule was written ESTABLISHED,RELATED. If you simply reloaded the page by refreshing the connection was likely still in an established state, thus is matched the ACCEPT rule and was allowed. Now if you closed your browser and waited a moment the connection would reset and no longer be in an ESTABLISHED state and would not match the rule, thus would have gone through your firewall rules normally.

Broadcast is actually an address as you can see above, basically if you ping that address ; any machine in the group running the broadcast service will respond. This is a security thing, it can help an attacker in determining the layout of the network. It can also be used to troubleshoot network failure on large networks. It's a personal preference for the administrator, it was likely added as it is considered best practices to disable it. It can also be used by a malicious attacker to carry out some types of denial of service attacks.



Same concept as above, IGMP multicast is used in discovery of multicast capable routers.

TCP RST stands for reset, it basically tells the machine requesting a connection that no connection will be accepted. Reject is used instead of dropping on many proxy and router implementations because you want traffic to flow smoothly. If you DROP the packet the machine sending it may try many more times, causing a delay. Since it is not really a security concern to reject instead of drop it is used for performance sake.

That should be all of them for now, feel free to ask if you have any others. I'm glad you're enjoying your endeavors with firewalls/routing. Thanks again for the kind words.

Regards
Adam

Adam,

Once again, a great help. This is starting to congeal somewhat and make sense. It also give me some light at the end of the tunnel, as I trust that as I'm reading more I'll find these best practices and hope to understand them even more fully. I am eager to delve into the nat tables to understand better what is going on there and why this works. Your help has been of inestimable value. Thank you for taking the time to help me and also point me in the right directions.

Kind Regards,
Narnie

---

### Post by Dangertux on 2011-10-05
Once again thank you for the kind words, I'm glad this was helpful. 

Best regards,
Adam

---

