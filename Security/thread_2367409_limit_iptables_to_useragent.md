---
title: "limit iptables to useragent"
date: 2017-07-29
forum: Security
---

### Post by rickr0ll on 2017-07-29
I have a asterisk server that runs in the background of my computer and i would like to secure it a bit better and i have been playing with the tcpdump

```
tcpdump -i eth0 port sip -l -A | egrep -i 'User-Agent' 
```

I can see my voip provider and my different sip devices get the User-Agent spitting out if I leave this command running I run on my network. now it would be nice to drop all other User-Agent unless its the 4-5 I have.  is it possible to write a command like this is anyone fluent enough in iptables that could help me?

i already block some common  scripts that seem to hit me up all the time and that works good but would be nice to drop just everything but a few. some devices let you manipulate your user-agent so it could be sort of a key plus the login credentials and all the othere security.. 

using

```
-A INPUT -p udp -m hashlimit --hashlimit-upto 6/sec --hashlimit-burst 5 --hashlimit-mode srcip,dstport --hashlimit-name tunnel_limit -m udp --dport 5060 -j ACCEPT
-A INPUT -p udp -m udp --dport 5060 -m string --string "INVITE sip:" --algo bm --to 65535 -m recent --update --seconds 60 --hitcount 12 --rttl --name VOIPINV --rsource -j DROP
-A INPUT -p udp -m udp --dport 5060 -m string --string "INVITE sip:" --algo bm --to 65535 -m recent --set --name VOIPINV --rsource
-A INPUT -p udp -m udp --dport 5060 -m string --string "REGISTER sip:" --algo bm --to 65535 -m recent --update --seconds 60 --hitcount 12 --rttl --name VOIP --rsource -j DROP
-A INPUT -p udp -m udp --dport 5060 -m string --string "REGISTER sip:" --algo bm --to 65535 -m recent --set --name VOIP --rsource
-A INPUT -p udp -m udp --dport 5060 -m string --string "sipvicious" --algo bm --to 65535 -j REJECT --reject-with icmp-port-unreachable
-A INPUT -p udp -m udp --dport 5060 -m string --string "VaxSIPUserAgent/3.1" --algo bm --to 65535 -j REJECT --reject-with icmp-port-unreachable
-A INPUT -p udp -m udp --dport 5060 -m string --string "sipcli/v1.8" --algo bm --to 65535 -j REJECT --reject-with icmp-port-unreachable
```

---

### Post by Habitual on 2017-07-30
fail2ban?

---

### Post by rickr0ll on 2017-07-30
unfortunately fail2ban is limited to logs .  Yes it does make iptables on the failed login attempts.  But No this is not the answer.

i am looking for someone who can help me  drop all trafic that shows a user-agent in the packets with the string search user-agent and I know you can not do wild cards in iptables.

But I am hoping one can just block all but not traffic that does not have these user-agent in the string. 

I run fail2ban and I am at its limits .. 

> **Habitual said:**
> fail2ban?

the problem is the more sophisticated scanning that is going on fail2ban just does not even  see.  I have always dumped the packets and figured out what I could do iptables wise to block using strings and its been effective.. but now I am getting user-agents like ahgsfghfghads ...  clearly they are getting smarter.. so I want to custom my sip devices user agents and only allow those user-agents .

---

