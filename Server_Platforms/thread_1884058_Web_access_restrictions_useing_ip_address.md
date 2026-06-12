---
title: "Web access restrictions useing ip address"
date: 2011-11-20
forum: Server Platforms
---

### Post by adtf01 on 2011-11-20
I would like to allow/restrict webm access on my netwrok based on ip address.
 
Firstly a range of address must have no web access at all
 
Secondly a range have limited access - ie no torrents
 
the third group has more access but still limited on torrents.
 
I have done some research and found that blocking torrents is very difficult.  One solution was to block high end ports 1024 - 65535.  I tried this but found it also blocked me from downloading hp printer drivers!

---

### Post by SeijiSensei on 2011-11-20
That might have been a [posting]("http://ubuntuforums.org/showpost.php?p=11321788&postcount=28") I made some weeks ago.

My client for whom we set up an identical blocking rule had the same experience with HP drivers.  (Why they can't just use port 80 escapes me.)  If there are certain services you need to access, just add an ACCEPT rule for those IPs/ports above the generic blocking rule.  In that posting I also suggested a method of logging blocked packets so you can determine what needs to be whitelisted.

Your first request is much easier to implement especially if you have some control over your network's topology.  You might try segregating users with different permission regimes into different subnets. 

```
iptables -A INPUT -p tcp -s 10.10.1.0/24 --dport 80 -j REJECT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
```

will block machines in the 10.10.1.0/24 subnet but no others.

Otherwise, you'll need rules for each machine you want to block like:

```
iptables -A INPUT -p tcp -s 10.10.10.10 --dport 80 -j REJECT
```

If you use DHCP, you can tell the DHCP server which IP address to assign a machine based on its MAC address.

---

### Post by adtf01 on 2011-11-22
Thank you SeijiSensei for you response.  I had actually seen your previous post and trie the suggestion - hence the blocking of hp drivers!
 
I have come into this situatin with the network already up but now we want to have more control!  Not a good way to set up a network I know!  I am also very new to linux so any help suggestions are much appreciated.
 
The current situation is ip range is 192.168.2.80 - 89 allowed full access, 90 - 120 (currently 120) no torrents, the rest no access to internet.  This will circumvent people hacking into the system - we have mac address filtering on the wireless so only those on wired segments will be able to fiddle.  The allowed addresses are all allocated to computers so any "fiddling" will result in address conflicts.
 
If I understand what you suggested I could first list those allowed full access, then the have the generic port reject.
 
After that list those addresses allowed with limited access and finally have a general ip reject.
 
One questioon is where do I put these rules - with the masquerade rules?  Before or after those rules?

---

### Post by adtf01 on 2011-11-22
Another question where is the log stored and what is it called?

---

### Post by SeijiSensei on 2011-11-22
> **adtf01 said:**
> One questioon is where do I put these rules - with the masquerade rules?  Before or after those rules?

I consolidate all the rules into a single script for convenience. I generally put the NAT rules at the end, but it doesn't really matter.  The masquerading rules are placed in the nat table; input and output rules are placed in the filter table.

Read [this](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Packet_Processing_In_iptables) to see how packets work their way through the various tables.

> **adtf01 said:**
> Another question where is the log stored and what is it called?

iptables logs to the "kernel" facility; by default it's logged to /var/log/kern.log.

---

