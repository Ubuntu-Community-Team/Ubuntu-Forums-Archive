---
title: "iptables: MAC Filtering w/ a file?"
date: 2011-07-02
forum: Security
---

### Post by Tactical Fart on 2011-07-02
I'm wanting to use mac filtering to restrict access to certain machines. I already know that I can just add MACs line by line, but is there a way to specify a list of MACs? That way it would be much simpler to maintain a list of acceptable/unacceptable hosts.

I'm not going to rely only on this list because of spoofing, but it would be nice as another "layer" of protection.

---

### Post by HermanAB on 2011-07-03
Howdy,

No, I don't think you can directly do that with iptables.  You could create a Bash script to read a file of MACs and add a bunch of rules, or you can configure your DHCP server properly so that the machines are in a subnet group and then make a single IP Address rule for that subnet, instead of using MACs.

Probably the best way to control things on a LAN is with VLANs and a managed switch.

---

### Post by wacky_sung on 2011-07-03
Use [arptables]("http://manpages.ubuntu.com/manpages/hardy/man8/arptables.8.html")

---

### Post by The Cog on 2011-07-03
The only way I can think of is to use a script, a bit like this:
for m in $(cat maclist.txt) ; do iptables -A INPUT --mac-source $m -J DROP ; done

If you are using iptables-save and iptables-restore, you could write a small script that updates saved config.

---

### Post by Tactical Fart on 2011-07-04
I'm not too big on writing scripts. I've never looked into them except to do a series of command super fast.
```
Task 1
Task 2
Task 3
```
Is about all I can do right now. What The Cog put up is over my head, but that's a little off topic. 

I did find another solution though that generally gets the job done. When adding a rule, you use -j to "pass judgement" on the packets. You can use ACCEPT, DROP, or a user defined. Make the user defined chain look like this: 
```
iptables -A usersChain -m mac --mac-source (mac address here) -j ACCEPT
iptables -A usersChain -s 0.0.0.0/0 -j DROP
```

and the INPUT chain like this:
```
iptables -A INPUT (criteria you want to look for like a certain source network/host-address or protocol) -j usersChain
```

With this set-up, a packet that matches certain criteria will be put against a "list" of mac addresses, and can even block macs by using DROP instead of ACCEPT. The administrator can then manage a list of mac addresses (or ip addresses if so inclined) to simply everything instead of appending/inserting rules into the main chains.

I know that what I've just posted isn't original, but it's just in case someone else has a similar need. 

This guide showed me what to do, I hope it can help someone else out. 
[http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-7.html](http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-7.html) 

Thanks you for your help everyone. SOLVED

---

