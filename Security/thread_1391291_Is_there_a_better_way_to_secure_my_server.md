---
title: "Is there a better way to secure my server?"
date: 2010-01-26
forum: Security
---

### Post by syslord on 2010-01-26
Hi all,

i set up my ubuntu server with iptables that only allows ssh in the input chain (and of course established connections) with only the mac adress of my laptop allowed to connect, set up a key with a long passphrase and installed pam_abl plugin. ICMP echo is blocked by default.

The only problem is i log all other attempts to connect to the server and i see a lot of traffic going to ports 445 and 5900.

My question is: Is there a possibility that these attempts could succeed and is there any way to further ensure this server?

Thanks in advance for the answers

Best regards

michael

---

### Post by cdenley on 2010-01-26
If you have no services listening for that traffic, then it will be rejected. Also, it sounds like it will be filtered anyway. These "attacks", or connection attempts, cannot succeed unless you stop filtering it and install a service to handle the connection attempts.

---

### Post by bodhi.zazen on 2010-01-26
Nothing like reading the logs to instill a little paranoia.

---

### Post by syslord on 2010-01-26
that's what i wanted to hear, in fact i was able to trace a lot of the attempts back to china so because i am new to linux (coming from windows server) i was kinda afraid that they might be able to get around with some crude kind of exploit or somethin :)

---

### Post by bodhi.zazen on 2010-01-26
If you really wish to monitor your server , take a look at NIDS and HIDS.

Snort is the "gold standard" and can generate 'alerts", or network traffic that is more concerning.

The problem with reading the logs, they are very long and you need to somehow filter out the normal activity.

You can also look at something like denyhosts or fail2ban if you wish, but if you are not running a VNC server and have a good set of rules for iptables, you have to ask yourself if snort , denyhosts, or fail2ban are worth it.

Of course you can always look at hardening apache, such as mod_security :lolflag:

---

### Post by syslord on 2010-01-27
i don't think that's worth it, the server is just a relay to enter the network in my office so it's only ssh that is needed and even if someone succeeds in breaching in he still needs another private key to connect to the actual fileserver.

---

### Post by Lars Noodén on 2010-01-27
Just be sure to let at least some ICMP in so that you are able to diagnose your network connection should there be a problem later. ping and traceroute are the bare minimum.

---

### Post by syslord on 2010-01-27
hmm that might be an issue for external servers but this one is located in my office so if it doesn't respond i can go and check or at least when i'm not at the place i can send someone.

---

### Post by Lars Noodén on 2010-01-27
> **syslord said:**
> hmm that might be an issue for external servers but this one is located in my office so if it doesn't respond i can go and check or at least when i'm not at the place i can send someone.

1) ICMP is there for a purpose and needed for correct operation. Your network is *broken* without ICMP

2) ICMP will save you unnecessary trips and wasted time. You will recover your time investment in the first network or connectivity problem.

corollary) It's not just the products or distro but the way of thought and problem solving (or not).  Not doing things correctly is the Microsoft way and will eventually bite you.

---

### Post by alvarojavier on 2010-01-27
Thanks, good appreciation.

---

### Post by Lars Noodén on 2010-01-27
Here's one of the ways I have to allow ping, but discourage flooding:

```

   # allow the courtesy of at least a ping
   iptables -A INPUT -p icmp --icmp-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

   ip6tables -A INPUT -p icmpv6 --icmpv6-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

```

The idea is to be able to see if the server is connected to the net without having to go over to it.

---

### Post by syslord on 2010-01-27
> **Lars Noodén said:**
> 1) ICMP is there for a purpose and needed for correct operation. Your network is *broken* without ICMP

2) ICMP will save you unnecessary trips and wasted time. You will recover your time investment in the first network or connectivity problem.

corollary) It's not just the products or distro but the way of thought and problem solving (or not).  Not doing things correctly is the Microsoft way and will eventually bite you.

Spose u got a point there

[QUOTE=Lars Noodén]Here's one of the ways I have to allow ping, but discourage flooding:

```

   # allow the courtesy of at least a ping
   iptables -A INPUT -p icmp --icmp-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

   ip6tables -A INPUT -p icmpv6 --icmpv6-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT
```
The idea is to be able to see if the server is connected to the net without having to go over to it.[/QUOTE]

Ok i'll do that

---

