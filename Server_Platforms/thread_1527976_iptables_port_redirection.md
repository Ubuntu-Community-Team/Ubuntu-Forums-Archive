---
title: "iptables port redirection"
date: 2010-07-10
forum: Server Platforms
---

### Post by carsten- on 2010-07-10
Hello.
I have two ip's on my server, I am trying to port forward from port 80 to 8080 on ip 69.164.206.62.. I am attempting to do this with an iptables command as follows: iptables -A PREROUTING -t nat -p tcp -d 69.164.206.62 --dport 80 -j REDIRECT --to-port 8080

I have had a couple of debian tell me this is quite correct, yet it is still not working. There are no webservers or anything else present on that IP..
What am I doing wrong here?

I forgot to mention, I have tried rebooting, to no avail.

---

### Post by HermanAB on 2010-07-10
Hmm, iptables is order dependent.  Think of it as having a long laundry list of rules and for each packet, it starts at the top and work its way to the bottom until a rule matches, then it returns to the top.

The '-A' will add a rule to the bottom of the list, while '-I' will stuff a rule in at the beginning of the list.  Depending on how much junk you already have in the list, a packet may never reach a rule that was added at the bottom. So, first flush all rules with 'iptables -F' before you start to experiment.

Note that a modern Linux distribution doesn't really need any iptables rules at all, since the network stack nowadays has a lot of error checks built in.  Complicated firewall rules are a habit from the good old bad old days.  Therefore, if you have a complex maze of rules thanks to UFW or Firestarter or gawd forbid Shorewall - get rid of it all and start over with only the two or three rules you really need.

Oh, remember to read the iptables man page about 5 times before you continue - it will eventually make sense.

---

### Post by carsten- on 2010-07-10
Hello Herman.
Thanks for your reply... I have read the man pages for iptables a tone of times, and what they are saying to me the rule I implemented should work.. I dont have any other rules in iptables other than that one... Nothing not a single one.

---

### Post by CannibalZerg on 2010-07-12
**carsten**, are you trying to configure transparent proxy? 
Here is the solution: [http://tldp.org/HOWTO/TransparentProxy-6.html](http://tldp.org/HOWTO/TransparentProxy-6.html)

---

### Post by Sporkman on 2010-07-12
> **HermanAB said:**
> 
Note that a modern Linux distribution doesn't really need any iptables rules at all, since the network stack nowadays has a lot of error checks built in.  Complicated firewall rules are a habit from the good old bad old days.

Do we still need stuff like this (found on the internet):

```
# block spoofing
iptables -A INPUT -s 127.0.0.0/8 -i ! lo -j DROP

# stop bad packets
iptables -A INPUT -m state --state INVALID -j DROP

# NMAP FIN/URG/PSH
iptables -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j DROP
# stop Xmas Tree type scanning
iptables -A INPUT -p tcp --tcp-flags ALL ALL -j DROP
iptables -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j DROP
# stop null scanning
iptables -A INPUT -p tcp --tcp-flags ALL NONE -j DROP
# SYN/RST
iptables -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j DROP
# SYN/FIN
iptables -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP
# stop sync flood
iptables -N SYNFLOOD
iptables -A SYNFLOOD -p tcp --syn -m limit --limit 1/s -j RETURN
iptables -A SYNFLOOD -p tcp -j REJECT --reject-with tcp-reset
iptables -A INPUT -p tcp -m state --state NEW -j SYNFLOOD
# stop ping flood attack
iptables -N PING
iptables -A PING -p icmp --icmp-type echo-request -m limit --limit 1/second -j RETURN
iptables -A PING -p icmp -j REJECT
iptables -I INPUT -p icmp --icmp-type echo-request -m state --state NEW -j PING

```

---

### Post by koenn on 2010-07-12
> **carsten- said:**
> Hello.
I have two ip's on my server, I am trying to port forward from port 80 to 8080 on ip 69.164.206.62.. I am attempting to do this with an iptables command as follows: iptables -A PREROUTING -t nat -p tcp -d 69.164.206.62 --dport 80 -j REDIRECT --to-port 8080

I have had a couple of debian tell me this is quite correct, yet it is still not working. There are no webservers or anything else present on that IP..
.
How do you know it's not working ? How are you testing this ?
Note the dst address in the iptables statement, and the fact that you say this server has 2 addresses ...

---

### Post by WinstonChurchill on 2010-07-13
> **carsten- said:**
> Hello.
I have two ip's on my server, I am trying to port forward from port 80 to 8080 on ip 69.164.206.62.. I am attempting to do this with an iptables command as follows: iptables -A PREROUTING -t nat -p tcp -d 69.164.206.62 --dport 80 -j REDIRECT --to-port 8080

I have had a couple of debian tell me this is quite correct, yet it is still not working. There are no webservers or anything else present on that IP..
What am I doing wrong here?

I forgot to mention, I have tried rebooting, to no avail.The REDIRECT target simply redirects packets to a different port on the same IP, or the primary IP of the interface if the interface it is received on has multiple addresses - what the rule you have written actually says is "If we see a TCP packet to port 80 with the destination address 69.164.206.62, redirect it to port 8080 on the interface's primary IP". Is 69.164.206.62 the first address in your /etc/network/interfaces file? If it is, that could be why this isn't working... and REDIRECT probably isn't the optimal solution to what you're trying to do anyway.

A better solution might be to use the TPROXY target (recently added to Ubuntu's iptables I think...) if you're setting up a transparent proxy - pay attention to the warning in the manpage about inadvertantly forwarding packets. Or you could use the DNAT target, although I'm not sure that that's necessary - if you're not trying to transparently proxy, you should just edit the config for whatever service is listening on 8080, and have it  listen on 80 on the other IP as well.

---

### Post by MidSpeck on 2010-07-14
> **carsten- said:**
> iptables -A PREROUTING -t nat -p tcp -d 69.164.206.62 --dport 80 -j REDIRECT --to-port 8080
I've thought about this for a little while.  Your port 8080 does seem to respond to me, but port 80 is giving me a reject.  Your rule above does indeed look correct, so I couldn't figure out why.
I looked at the man page for iptables and the REDIRECT target.  It looks like REDIRECT changes the destination address to 127.0.0.1.  Is your application (whatever you are running on port 8080) set up to listen on 127.0.0.1, or is it only set up to listen on your external IP address?

---

### Post by WinstonChurchill on 2010-07-15
> **MidSpeck said:**
> I've thought about this for a little while.  Your port 8080 does seem to respond to me, but port 80 is giving me a reject.  Your rule above does indeed look correct, so I couldn't figure out why.
I looked at the man page for iptables and the REDIRECT target.  It looks like REDIRECT changes the destination address to 127.0.0.1.  Is your application (whatever you are running on port 8080) set up to listen on 127.0.0.1, or is it only set up to listen on your external IP address?
Only locally generated packets are redirected to 127.0.0.1 - his aren't:
> 
   REDIRECT
       This  target is only valid in the nat table, in the PREROUTING and OUTPUT chains, and user-defined chains which are only called from those chains.  It redirects the packet to the machine itself by changing the destination IP to the primary address of the incoming interface (locally-generated packets are mapped to the 127.0.0.1 address).

       --to-ports port[-port]
              This specifies a destination port or range of ports to use: without this, the destination port is never altered.  This is only valid if the rule also specifies -p tcp or -p udp.

       --random
              If option --random is used then port mapping will be randomized (kernel >= 2.6.22).


---

### Post by MidSpeck on 2010-07-15
> **WinstonChurchill said:**
> Only locally generated packets are redirected to 127.0.0.1 - his aren't:

Ah, you are right.  So I guess then the only question might be if the OP has multiple IP addresses per interface.  Which now that I'm re-reading your original response, you've basically already asked that question.

---

