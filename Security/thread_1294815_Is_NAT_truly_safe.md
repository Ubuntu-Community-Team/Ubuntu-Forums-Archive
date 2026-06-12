---
title: "Is NAT truly safe?"
date: 2009-10-18
forum: Security
---

### Post by virtuoosi on 2009-10-18
Hello,

Call me paranoid, but since I started to run my own home server I have been worried about it's security. There are no local threats, we have couple of Windows machines here and I don't think my family members have any real reasons to mess around with my server box. 

I opened my server to the outside world some months ago by forwarding couple of ports to it. I opened an port for http (80), ventrilo (3784) and an custom port for ssh (not the default 22). So basically Shields Up! or Open port checking tool doesn't show anything but those ports open. That's cool. Obviously, when I scan the box with my laptop within the LAN, it shows that many ports are open since I run many services on the server which are ment to be used from within the LAN.

So the question is: can I trust on the NAT only? Or should I run some kind of a firewall on my server box? So far I've been thinking that the NAT is enough, as long as I only keep those ports open which I need.

---

### Post by falconindy on 2009-10-18
NAT alone isn't enough. Suppose you open port 25 for unsecure telnet and allow anonymous connections with no password? NAT isn't going to do a whole lot of good in this case.

In theory, you should be sandboxing any program that requests or receives requests from the outside world. AppArmor can be used to this effect.

---

### Post by virtuoosi on 2009-10-18
Thanks for the fast response, I am looking into AppArmor. 

So I've got a port open for ssh. This is only safe if the sshd waiting in the port is safe? So it is just a matter of configuring my sshd to not allow login as root or to not allow empty passwords etc?

---

### Post by cariboo on 2009-10-18
I would suggest you not allow password access to ssh at all. Setup key based ssh logins. There is a howto [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

---

### Post by Lars Noodén on 2009-10-19
> **virtuoosi said:**
> Thanks for the fast response, I am looking into AppArmor. 

So I've got a port open for ssh. This is only safe if the sshd waiting in the port is safe? So it is just a matter of configuring my sshd to not allow login as root or to not allow empty passwords etc?

That helps.  NAT is just a means of addressing and unrelated to security.  

You can use iptables to throttle the rate at which the port is probed, using --limit and --match

```

# for entertainment only: 

   ip6tables -N SSH;    # create chain
   iptables  -N SSH;    # create chain

   # send all incoming SSH trafficc to SSH chain
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 22 -j SSH;
   iptables  -I INPUT -i eth0 -p tcp --destination-port 22 -j SSH;

   # accept incoming connections, in moderation
   ip6tables -I SSH -i eth0 -p tcp --destination-port 22 \
      -m limit --limit 1/minute --limit-burst 2 -j ACCEPT
   iptables  -I SSH -i eth0 -p tcp --destination-port 22 \
      -m limit --limit 1/minute --limit-burst 2 -j ACCEPT

   # allow finite new connections per timelimit
   ip6tables -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT
   iptables  -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT

   ip6tables -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --set
   iptables  -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --set


```

However, most attacks pace themselves better nowadays, so the above is not as effective.  It also only counts connections and not failed logins.  

You might try white listing good addresses and blocking everyone else using tcpd, also known as tcpwrappers.

Or as @cariboo907 wrote, disable password authentication for ssh and rely on keys.  The keys obviously should have their own passphrases.  

It depends on how you plan to use the connection.

---

### Post by koenn on 2009-10-19
I agree with this : NAT is just a means of addressing and unrelated to security. 

Although it does have the interesting side effect of blocking incoming connections towards your LAN (behind the NAT router).

The thing that is most often overlooked is this side effect does not apply to the router itself, which remains publicly accessible. And if someone manages to compromise it, it's easy for the intruder to reconfigure the router so that it does allow routing into the LAN (eg by setting up portforwarding / DNAT)

So no, NAT alone is not truly safe.

---

### Post by The Cog on 2009-10-19
The reason that NAT is often considered safe is that it prevents incoming connections to the PC, thus acting like a firewall. But in this case, you have forwarded some ports to your PC which is running services that accept incoming connections - effectively opening holes in your NAT "firewall". Now, obviously if you had a firewall installed, you would have to open the ports in that to allow the connections in, so adding a firewall won't help. You have chosen to allow connections to these services from the internet, so they are exposed to all the bad guys out there. You need to ensure those services themselves are secure, by making using strong login passwords or encryption keys etc. AppArmour will help if one of the services does get compromised. 

But for services that have to be exposed to the internet, NAT and firewalls don't really help because they prevent the incoming connections that you need. You have to look at the services themselves to see if they're secure.

---

### Post by update_manager on 2009-10-19
> **virtuoosi said:**
> 
So the question is: can I trust on the NAT only? Or should I run some kind of a firewall on my server box? So far I've been thinking that the NAT is enough, as long as I only keep those ports open which I need.

Things that a NAT would let through:
* invalid combinations of TCP flags ([https://bugs.launchpad.net/ufw/+bug/323950](https://bugs.launchpad.net/ufw/+bug/323950))
* connections from hosts known to be attackers
* exploits that target upper layer protocols ([http://www.cipherdyne.org/fwsnort/](http://www.cipherdyne.org/fwsnort/))
* anything outbound (misconfigured programs)

If you'd like to stop these things, don't rely on NAT. Using UFW + fwsnort would be a good start, the launchpad bug link should be enough for you to customize it some.

---

### Post by virtuoosi on 2009-10-20
> **The Cog said:**
> You need to ensure those services themselves are secure, by making using strong login passwords or encryption keys etc. AppArmour will help if one of the services does get compromised.

Okay this made things a bit clearer! I have now set up RSA keys for ssh, and disabled password logins. 

I am looking into apache2 security, and this thread has given me plenty of ideas how to proceed. Thanks alot for the help! :)

---

### Post by QLee on 2009-10-20
[QUOTE=virtuoosi]
Call me paranoid, but since I started to run my own home server I have been worried about it's security. There are no local threats, we have couple of Windows machines here and I don't think my family members have any real reasons to mess around with my server box.[/QUOTE]

You haven't mentioned it but don't fail to consider what happens if one of those Windows boxes is compromised, it may not be an actual family member who now has trusted access inside your LAN.

---

### Post by virtuoosi on 2009-10-20
> **QLee said:**
> You haven't mentioned it but don't fail to consider what happens if one of those Windows boxes is compromised, it may not be an actual family member who now has trusted access inside your LAN.

Excellent point there. I am trying my best to keep them secure.

---

