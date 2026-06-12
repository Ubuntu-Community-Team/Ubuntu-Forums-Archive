---
title: "iptables misbehaving?"
date: 2014-11-18
forum: Security
---

### Post by greg_s2 on 2014-11-18
Hi all... I've been using iptables for ages and have never seen this particular oddity. Here's what I have.

VM running Ubuntu Server 14.04.

I'm running a set of processes that listen to netflow and sflow data exports from a dozen or so routers. The processes are from the nfdump package, and are nfcapd and sfcapd running in daemon mode. Each one of these processes is meant to capture from a single router. Since it is easiest to have the same config on each router, I am using iptables to map the same destination port on the my server to the actual port the process is running on. For example:

```
iptables -t nat -A PREROUTING -s <router 1 IP> -p udp -m udp --dport 2055 -j REDIRECT --to-port 2001
iptables -t nat -A PREROUTING -s <router 2 IP> -p udp -m udp --dport 2055 -j REDIRECT --to-port 2002

```
... and so on. I also have matching INPUT rules to allow this as follows:

```
iptables -A INPUT -i eth1 -s <router 1 IP> -p udp --dport 2000:2999 -j ACCEPT

```
The source router IPs are substituted as you might expect.

The problem I'm having is, at times, this just doesn't work. Also, I only see one or two matches in the nat counters (-v) even when it is working.  On the last reboot of the server, all but two of the entries were working, no counters incrementing as you'd expect. No amount of prodding it got the two problem entries to work - not rebooting, not flushing iptables, nothing. After throwing my hands up in disgust and going for a cocktail, I returned to find that it just started working for no reason about 15 minutes after I left. I'm certain that if I reboot it the problem will start again.

Anyone have a clue?

---

### Post by Doug S on 2014-11-19
> **greg_s2 said:**
> Also, I only see one or two matches in the nat counters (-v) even when it is working.That is correct. The nat PREROUTING table/chain is only consulted for "NEW" connections, and thereafter the connection tracking table knows what to do with the packets. (Important note: The comment is only about the nat PREROUTING table.)

[Reference.]("https://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#PREROUTINGCHAIN")

The other issues, I don't know. (It's late in my time zone, maybe tomorrow I'll think of something.)

Edit: I wonder if, when you re-boot your server, streams from some of your routers are ahead of the iptables setup, such that they are not considered "NEW". Eventually they are seen as "NEW" and things start to work.

---

### Post by greg_s2 on 2014-11-19
> **Doug S said:**
> That is correct. The nat PREROUTING table/chain is only consulted for "NEW" connections, and thereafter the connection tracking table knows what to do with the packets. (Important note: The comment is only about the nat PREROUTING table.)

[Reference.]("https://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#PREROUTINGCHAIN")

The other issues, I don't know. (It's late in my time zone, maybe tomorrow I'll think of something.)

Edit: I wonder if, when you re-boot your server, streams from some of your routers are ahead of the iptables setup, such that they are not considered "NEW". Eventually they are seen as "NEW" and things start to work.

Ah, got it. Interesting, I never noticed before, possibly because I didn't have to look - things just worked.

The routers do constantly bombard the server with packets, probably at least 1 pps. So, it is highly possible that packets are hitting prior to iptables kicking in during boot. Since this is all UDP, there is no connection set up. Maybe there is something with how UDP is tracked "session-wise" such that all packets are accepted? I did try putting the necessary allows at the top of the FORWARD table but that did not help.

---

### Post by Doug S on 2014-11-19
> **greg_s2 said:**
> Since this is all UDP, there is no connection set up. Maybe there is something with how UDP is tracked "session-wise" such that all packets are accepted?I don't know UDP very well. I do observe that connection tracking table entries have a 30 second life.```
doug@doug-64:~$ [COLOR=#ff0000]sudo cat /proc/net/ip_conntrack | grep udp[/COLOR]
udp      17 [COLOR=#ff0000]29[/COLOR] src=127.0.0.1 dst=127.0.0.1 sport=52092 dport=53 src=127.0.0.1 dst=127.0.0.1 sport=53 dport=52092 mark=0 use=2
udp      17 [COLOR=#ff0000]29[/COLOR] src=173.180.45.4 dst=216.239.32.10 sport=60042 dport=53 src=216.239.32.10 dst=173.180.45.4 sport=53 dport=60042 mark=0 use=2
```The above was done as quick as possible after "nslookup google.com" in another window. So, and I am really really guessing at this point, you would need a 30 second gap for the next packet to be perceived as "NEW".

Edit: The counters can be used to know how many times the packet from a given router has been perceived as "NEW".

---

