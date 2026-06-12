---
title: "Firewall(iptables) problems..."
date: 2009-11-22
forum: Server Platforms
---

### Post by ChromoX on 2009-11-22
I have a problem with my iptables. I set them up to obviously drop everything coming in except for 22,80,8000, and allow everything going out. But the problem is that I can not get out at all from the box. I can come in through ssh, although it takes a very long time to give me the password prompt. I was wondering two things: 1, why can't I go out from the box?(DNS is setup correctly) 2, Why did the ssh prompt become so slow after I put this firewall in.

Thanks.


Output of iptables -L:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8000 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

---

### Post by hictio on 2009-11-23
Are you sure you have a rule like:

```

/sbin/iptables -A OUTPUT -j ACCEPT

```

It doesn't seem to be the case, given the output that you posted of the execution of 'iptables -L'.

Regarding the delay that you describe with the login over SSH, I'm pretty sure that's DNS related, try, just for the sake of the test, to add to the /etc/hosts file of the server yo are login into, the IP and hostname of the box you are connecting from.

---

### Post by ChromoX on 2009-11-23
Thats actually my problem... DNS is not resolving. If I flush the iptables DNS works perfectly, and if I turn my rules back up that were printed above DNS doesn't work, nor does trying to get to an IP.

Anyone have any ideas?

---

### Post by Lars Noodén on 2009-11-24
UDP is stateless, so there is no real way of knowing which returning UDP packets are related to the ones sent earlier by your machine.  So the catchall (RELATED,ESTABLISHED ) is probably not working.  You could log for a while and see what you are blocking.  

DNS uses UDP to connect to port 53. Sometimes it is also sent from port 53.

Allow UDP in on port 53 or else have the dns client use an unprivileged 
port.

---

### Post by hictio on 2009-11-24
But, I'm not clear with your response above.
Do you have a rule on your iptables that allow all outbound traffic?
If you do, and you have a correctly setup /etc/resolv.conf file (DNS servers that are reachable and that they are working), you'll have no problems with name resolution.

---

### Post by dragos_iliescu_2005 on 2009-11-24
In my case I have a line with the interface (eth0) in:

target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
eth0_in    all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
Drop       all  --  anywhere             anywhere            
DROP       all  --  anywhere   

I'm not seing this in your iptables -L output.

---

### Post by robert_pectol on 2009-11-24
> **hictio said:**
> ... Do you have a rule on your iptables that allow all outbound traffic?...

Seems that the default policy would be in affect in the absence of rules in the OUTPUT chain:

```

Chain OUTPUT (policy ACCEPT)

```

Right?

Also, your INPUT rules would all be rendered useless by the first rule:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
[COLOR="Red"]ACCEPT     all  --  anywhere             anywhere[/COLOR]            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8000 
DROP       all  --  anywhere             anywhere

```

Seems that your ruleset should be no different than a box with *no* ruleset.

---

### Post by ChromoX on 2009-11-27
Sorry I should have printed the verbose iptables. The first rule is for anything coming from localhost.

Second I am going to try allowing port 53 in, or maybe reconfigure dns to use a different port.

Also is this assumption correct?... Even though my default for OUTPUT is allow that doesn't mean that whatever I request will come back through the firewall because of my restrictive rules on INPUT right?

---

### Post by iponeverything on 2009-11-27
> **ChromoX said:**
> Sorry I should have printed the verbose iptables. The first rule is for anything coming from localhost.

Second I am going to try allowing port 53 in, or maybe reconfigure dns to use a different port.

Your DNS requests are not leaving on port 53. Unless you control the upstream namesever, you have no choice but to send those queries to port 53 on the listener. Also note that some replies that return multiple records are too big for a UDP packet, so the request will be resent over TCP. 
> 
Also is this assumption correct?... Even though my default for OUTPUT is allow that doesn't mean that whatever I request will come back through the firewall because of my restrictive rules on INPUT right? 

Your assumption is somewhat correct. I use a rule for established connections.

---

### Post by ChromoX on 2009-11-28
> Your assumption is somewhat correct. I use a rule for established connections. 	
I have that same rule, but for some reason DNS requests are not coming back to the server.

---

### Post by iponeverything on 2009-11-28
> **ChromoX said:**
> I have that same rule, but for some reason DNS requests are not coming back to the server.

because UDP is stateless there is no way for the server to know if the packet was solicited.

The best way to address that is to setup a rule to allow DNS packets only from nameservers you are using in your resolv.conf

---

### Post by ChromoX on 2009-11-28
> **iponeverything said:**
> because UDP is stateless there is no way for the server to know if the packet was solicited.

The best way to address that is to setup a rule to allow DNS packets only from nameservers you are using in your resolv.conf

Wow... Thats simple enough. Should I allow all traffic from the nameservers, or just on port 53 or something along those lines?

Thanks again for your help.

---

### Post by iponeverything on 2009-11-28
> **ChromoX said:**
> Wow... Thats simple enough. Should I allow all traffic from the nameservers, or just on port 53 or something along those lines?

Thanks again for your help.

I would specify just port 53. The namesevers have no other business talking to your machine from any other ports. When I do vulnerability testing on networks, I look for machines that might be "trusted" by the network that I am checking to run scans from. You have no reason to totally trust you nameservers.  

If you setup something just for port 53 -- make sure that you setup a rule for TCP and a rule for UDP.

---

### Post by hictio on 2009-11-28
> **iponeverything said:**
> 
~snip~
If you setup something just for port 53 -- make sure that you setup a rule for TCP and a rule for UDP.

You don't need TCP open for the DNS servers, unless your own box is a DNS server and it is a slave (or master) for the domains that the DNS you are connecting to is serving (again, either as Master or Slave).

That is, to resolve IPs onto hosts from a DNS server, you need to communicate via UDP, the only TCP you need involves zone transfers, and that involves that you run a DNS server.

For a regular client, that only needs DNS, this iptables line should work.
```

iptables -A OUTPUT -d DNS.server.IP -p udp --sport 1024:65535 --dport 53 -j ACCEPT

```

---

### Post by iponeverything on 2009-11-28
> **hictio said:**
> You don't need TCP open for the DNS servers, unless your own box is a DNS server and it is a slave (or master) for the domains that the DNS you are connecting to is serving (again, either as Master or Slave).

That is, to resolve IPs onto hosts from a DNS server, you need to communicate via UDP, the only TCP you need involves zone transfers, and that involves that you run a DNS server.

For a regular client, that only needs DNS, this iptables line should work.
```

iptables -A OUTPUT -d DNS.server.IP -p udp --sport 1024:65535 --dport 53 -j ACCEPT

```

I have gotten bitten by this before.

[http://www.spamstopshere.com/blog/2008/06/12/dns-also-uses-tcp/](http://www.spamstopshere.com/blog/2008/06/12/dns-also-uses-tcp/)

---

### Post by hictio on 2009-11-29
> **iponeverything said:**
> I have gotten bitten by this before.

[http://www.spamstopshere.com/blog/2008/06/12/dns-also-uses-tcp/](http://www.spamstopshere.com/blog/2008/06/12/dns-also-uses-tcp/)

Interesting, thanks a lot.
I didn't bite, or at least, it wasn't my intention.

---

### Post by ChromoX on 2009-11-30
iptables -A OUTPUT -d DNS.server.IP -p udp --sport 1024:65535 --dport 53 -j ACCEPT 
Is appended to the OUTPUT chain... My default policy is to allow all communication out therefore this line is redundant correct?

---

### Post by iponeverything on 2009-11-30
The rules are eval'ed from the top down.

If you don't have have a DENY or DROP in the chain that matches a packet before it hits the end of the chain, it will pass thought with your default policy of ACCEPT.

---

### Post by spynappels on 2010-03-04
Thanks for the pointers on adding a rule to enable DNS rules Inbound.
I was setting up Firewall rules through Webmin and couldn't understand why it was taking so long for PuTTY to log in, and HTTPS pages to update in Webmin.

Opening DNS ports helped.

Thank you very much.

---

