---
title: "iptables dos rules"
date: 2013-04-19
forum: Security
---

### Post by Leo Matheus on 2013-04-19
im having a problem with some iptables DOS rules: 


iptables -A INPUT -p tcp --dport 80 -m state --state NEW -m limit --limit 100/minute --limit-burst 50 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -m state --state NEW -m limit --limit 100/minute --limit-burst 50 -j ACCEPT
iptables -A INPUT -p tcp --dport 1812 -m state --state NEW -m limit --limit 50/minute --limit-burst 50 -j ACCEPT
iptables -A INPUT -m state --state RELATED,ESTABLISHED -m limit --limit 100/sec --limit-burst 50 -j ACCEPT
iptables -A INPUT -j DROP

when i run them they are dropping all the trafic, include the exceptions.

what im doing wrong?

---

### Post by Doug S on 2013-04-19
try removing this line:```
iptables -A INPUT -m state --state RELATED,ESTABLISHED -m limit --limit 100/sec --limit-burst 50 -j ACCEPT
```Or just remove the rate limiting part. You do not want to limit the established sessions.

---

### Post by Leo Matheus on 2013-04-19
i have removed, but it didn't work.:(

---

### Post by Doug S on 2013-04-19
Without the bigger context of the entire iptables rules set, it is hard to know for sure what is wrong. And I don't know if that bigger context includes the rule set of the other thread from a couple of days ago.
You might want to add some direction and interface specific stuff, and you probably do need some by-pass (RELATED, ESTABLISHED) rule. For example if eth0 is your external I/F, eth1 (if you have it) is your internal I/F, your WAN ip address is XXX.YYY.ZZZ.AAA and your internal network (if you have it) is 192.168.1.0, maybe something like:```
iptables -A INPUT -i lo -s 0.0.0.0/0 -d 0.0.0.0/0 -j ACCEPT
iptables -A INPUT -i eth1 -s 192.168.1.0/24 -d 0.0.0.0/0 -j ACCEPT
iptables -A INPUT -i eth0 -s 0.0.0.0/0 -d XXX.YYY.ZZZ.AAA -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -s 0.0.0.0/0 -d XXX.YYY.ZZZ.AAA -p tcp --dport 80 -m state --state NEW -m limit --limit 100/minute --limit-burst 50 -j ACCEPT
iptables -A INPUT -i eth0 -s 0.0.0.0/0 -d XXX.YYY.ZZZ.AAA -p tcp --dport 443 -m state --state NEW -m limit --limit 100/minute --limit-burst 50 -j ACCEPT
iptables -A INPUT -i eth0 -s 0.0.0.0/0 -d XXX.YYY.ZZZ.AAA -p tcp --dport 1812 -m state --state NEW -m limit --limit 50/minute --limit-burst 50 -j ACCEPT
iptables -A INPUT -j DROP

```

---

### Post by Leo Matheus on 2013-04-19
yes, i think it was that. By the way, i have put the lest drop rule like this:

code:

> iptables -A INPUT -i eth0 -j DROP

Thanks for the help Doug

---

### Post by CharlesA on 2013-04-19
Not really on topic, but how would a limit rule apply when you use a rule to block a connection after a certain number of access attempts?

My current rules are as follows:

```

-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# Set general rate limiting
-A INPUT -p tcp -m state --state NEW -m limit --limit 30/min --limit-burst 5 -j ACCEPT
# Accept ICMP packets
-A INPUT -p icmp -j ACCEPT
# Slow down log clutter from bruteforce attacks
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j REJECT
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -j ACCEPT
# Allow HTTP
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
# Allow HTTPS
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
# Allow loopback
-A INPUT -i lo -j ACCEPT
# Reject everything else
-A INPUT -j REJECT

```

It gets kinda weird when I tested it with these rules, but if I took out the general rate limiting rule, the ssh block rule worked as expected. Puzzling.

---

### Post by Doug S on 2013-04-19
@ Charles: What I would suggest for your case it to put the SSH rule outside of the rate limiting general rule:```
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# Slow down log clutter from bruteforce attacks
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j REJECT
-A INPUT -p tcp -m tcp --dport 22 -m state --state NEW -j ACCEPT
# Set general rate limiting
-A INPUT -p tcp -m state --state NEW -m limit --limit 30/min --limit-burst 5 -j ACCEPT
# Accept ICMP packets
-A INPUT -p icmp -j ACCEPT
# Allow HTTP
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
# Allow HTTPS
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
# Allow loopback
-A INPUT -i lo -j ACCEPT
# Reject everything else
-A INPUT -j REJECT
```By the way (mostly for other readers, as I think Charles has seen this before), here are my rules for ssh:```
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP [COLOR=#ff0000]all packets [/COLOR]from them.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT

```Notice that I drop all packets, not just port 22 packets, once they get on my "list".While very rare, I have had attacks over many many ports at once. The other thing I do is have a very long timeout, as I have seen many of these password bots come back after a short time. Notice also, the logging rule aside, this method uses 1 less rule.

Also, Myself I have had difficulties with rate limiting for incoming port 80 on my web site. I seem to keep hitting the limits for real accesses, or backing off so far, that it is of little use. Rate limiting has been useful for port 25 (e-mail) though.

@Leo: Glad you got it working.

---

### Post by CharlesA on 2013-04-19
Thanks, that helps. I wasn't too sure how two rate limiting rules work with each other. That really helps.\

EDIT: What is this rule supposed to do? It looks different from my accept rule.

```
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
```

---

### Post by matt_symes on 2013-04-19
Hi

Some good rules there Doug. I like the idea of dropping all traffic from an offending IP.

I may pinch that idea from you ;)

Kind regards

---

### Post by Doug S on 2013-04-19
Charles: Our SSH rule sets both do the same thing. Mine checks for hit count first, and acts. The next rule either creates the list entry or increments the hits and accepts. It will not get there, if the previous rule has already intervened. In your case the list is created or incremented. The next rule does the checking and acts. The third rule, if it gets there accepts.

I don't specify --update, but based on my experiments (years ago, now), a hit does reset the timer anyhow.

I also do not use the --rttl. I have seen attackers vary the ttl. It might not be the way for others with important sites, but for my server, I really do not care if it has collateral damage (I.E. if someone gets on the bad guy list in error. (I got myself on it one time when I was far away on a business trip, and I didn't wait quite long enough before tyring again...)).

---

### Post by CharlesA on 2013-04-20
Thanks for explaining it. I've added those rules to my firewall script. :)

---

