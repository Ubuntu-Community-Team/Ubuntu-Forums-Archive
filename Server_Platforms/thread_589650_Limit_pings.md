---
title: "Limit pings"
date: 2007-10-24
forum: Server Platforms
---

### Post by btaylor101 on 2007-10-24
I have read through some of the information on limiting pings and have a couple questions. I want to be able to ping my box, but reduce the damage of a DOS attack.  

Currently in iptables I have this rule:
> sudo iptables -I INPUT 3 -p icmp --icmp-type echo-reply -m limit --limit 1/sec --limit-burst 3 -j DROP

I am able to ping my box repeatedly without any packets being dropped. So  I was wondering if this rule limits the connections or packets?

---

### Post by HermanAB on 2007-10-24
Where is the rule?  If the rule is at the end of the list (after a spot where the packet is accepted) then it won't have any effect.

Check with 'iptables -L'.

Cheers,

Herman

---

### Post by btaylor101 on 2007-10-24
I have moved the rule to second in the list.
> Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts   bytes     target     prot opt in       out     source               destination         
 4617 1126K     ACCEPT     0    --  lo       any     anywhere             anywhere            
    0     0            DROP       icmp --  any    any     anywhere             anywhere            icmp echo-reply limit: avg 1/sec burst 3

Still able to repeatedly ping my box.

---

### Post by codmate on 2007-10-24
> **btaylor101 said:**
> I have moved the rule to second in the list.


Still able to repeatedly ping my box.

For a start, I think you're looking to restrict echo-request on the INPUT chain rather than echo-reply.

Secondly, you will still be able to ping the box once per second once the limit burst of 3 has been reached.

In real-world terms, this means that somebody pings your box three times as fast as they like, and then can only ping once per second.

Maybe what you really want is:
```
sudo iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/min --limit-burst 3 -j ACCEPT
```
...with a policy of dropping all other INPUT: ```

sudo iptables --policy INPUT DROP
```
Don't forget to open up all the other ports you need on the INPUT chain.
You can find out what programs you what ports at:
[http://www.grc.com/port_22.htm](http://www.grc.com/port_22.htm)

You can often also find this info in the conf files for whatever software you are using.

Otherwise try echo-response, as you had before, but on the OUTPUT chain:
```
sudo iptables -A OUTPUT -p icmp --icmp-type echo-reply -m limit --limit 1/min --limit-burst 3 -j DROP
```
This will allow only one ping response per minute once the box has been pinged 3 times.

AFAIK the limit burst resets itself after the time specified in --limit.

---

### Post by btaylor101 on 2007-10-24
I appreciate the quick response. After your explanation the reading I had done earlier made sense. I added your proposed rule and was still able to ping my box repeatedly. Taking a deeper look into my rule set I realized that I had allowed pings into the network:
> 203 12253 ACCEPT     icmp --  any    any     anywhere             anywhere

Once I removed this rule it is behaving as it should. Thank you for the explanation and information.

---

