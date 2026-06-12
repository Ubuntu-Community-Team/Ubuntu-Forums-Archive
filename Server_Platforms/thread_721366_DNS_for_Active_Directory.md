---
title: "DNS for Active Directory?"
date: 2008-03-11
forum: Server Platforms
---

### Post by cwhitmore on 2008-03-11
I  would like to replace the two Active Diretory DNS servers with Ubuntu DNS. I have DNS setup on a Ubuntu server, but it doesn't resolve the internal DNS names. How can I setup Ubuntu DNS to pickup the internal names?

---

### Post by ctyc on 2008-03-12
since you use MS software why not contact MS support for some of their wonderful help.

---

### Post by Petersonz on 2008-03-13
A couple of things to consider.

1) Microsoft DNS servers that have Active Directory integrated zones replicate through multimaster Active Directory replication. BIND (Linux DNS servers) will need to have primary/slaves setup with "notify" so that if a Windows box registers DNS with a slave, it notifies the master which re-propogates just the incremental change through "notify" to the other slaves. Im not sure about 100% accuracy of this as I am a bit rusty on BIND. I think BIND may support a multimaster replication scheme as well but it will probably need to be configured through the named.conf and other files.

2) Microsoft DNS servers use Unicode rules which allow underscores and non ASCII characters in the records. I think BIND doesnt allow this by default and has to be told to allow it in the named.conf file.

3) Microsoft clients and servers use Dynamic DNS to register their records. To say that the DNS server does or doesnt "pick up" internal DNS names is a bit of a misnomer. Instead, they, (the Microsoft operating system based machines) register their DNS entry with the DNS server. BIND supports this in Linux so long as Dynamic DNS and the aformentioned notification system is set up.

There may be other caveats to your endeavor, but I hate to admit my own BIND rustiness because in the end, the Microsoft DNS servers are simply quite easy to use.

The format of BIND zone files can appear to be daunting to a DNS novice. Mistakes like formatting the SOA record improperly are not easy to find/fix for the faint hearted.

Also, the default TTL for the records in a Microsoft DNS server is 3600 seconds or 1 hour for a reason. (As opposed to BIND's default of 86400 seconds or 24 hours I think). On the internet, where websites and email servers dont change their address often, 86400 TTL is ok and promotes longer caching of DNS records. On an internal network with dynamic addressing though, a much shorter TTL is needed.

This reason for this is because, in a Microsoft network, DHCP clients register their name/address pairs in WINS and DNS with the Microsoft DHCP server set to an 8 hour lease by default. Which means that every 8 hours, they "could" have a new IP address to register. Therefore the DNS zone needs to expire the cache (Time To Live value) quicker than the DHCP lease time in order to maintain reliable name to address resolution throughout the cycle of address allocation/release/renewal.

A couple of other things, either 

a. Dont use WINS and disable netbios on the servers and clients to use DNS only. 
Without WINS, B-NODES (Broadcast nodes) broadcast to find the netbios names of the other machines. This is ok in a flat single network, but doesnt work too well in routed multi segment network. 

or

b. Use WINS service, (and the nodes have WINS addresses), they are H-Nodes by default and use WINS first, then fall back to broadcast if WINS fails. This gives the appearance of slow drive mapping, slow printing, etc.

I believe the Ubuntu package samba-server has the Netbios name daemon (nmbd as opposed to smbd) which can act as WINS server for you. Again, its been a while so I am a little rusty on these details.

Good luck with your efforts :)

---

### Post by cwhitmore on 2008-03-13
Petersonz,
Thanks for the valuable information. I think you're right, the easiest way to resolve this is to setup NetBIOS on the Ubuntu side.

---

### Post by HermanAB on 2008-03-13
Hmm, there are also a zoo of little entries with leading underscore names that are undocumented and required.  I think the easiest way is to copy the rule set from the Windows DNS server.  The Windows DNS is an old version of BIND and the rules are somewhere on the disk.

---

### Post by koenn on 2008-03-13
> **ctyc said:**
> since you use MS software why not contact MS support for some of their wonderful help.

contact MS support for help with the configuration of (opensource) BIND. Right, very sound advice. You must have really thought this through.

---

### Post by koenn on 2008-03-13
I've hard that BIND can actually support AD and its DNS requirements, but that it's hairy. I guess Petersonz post covers most of the issues.

If it's just a matter of having dhcp-asdsigned addresses registered in DNS, Bind doesn't allow this by default because having any random workstation writing to a DNS zone file is a breach of security and a possible attack vector, as it can lead to all sorts of hijacking, redirection, spoofing, ... etc. 

An alternative is to let the dhcp server (who knows the hostname/ipaddress combinations as it hands out the addresses) write to DNS. This may require the dhcp and dns server to authenticate to each other (using a key)
I don't know whether DNS Updates by clients (workstations) also requires authentication. 


What HermanAB is talking about are all sorts of additional records (and possible even some subdomains) which are required for AD to work, eg SRV records to tell the workstations the names/ipaddresses of Domain Controllers that they can log on to - that sort of stuff. It does indeed look very messy. 


Since you have to set up domain controllers anyway, I think you might as well just run DNS on them as well. If you have additional DNS needs, you can run BIND besides thos and work out some forwarding scheme.

---

### Post by cwhitmore on 2008-03-13
Koenn and HermanAB,
Thanks for the information. Looks like this might not work as well as I thought without making the DNS server a secondary domain controller. I'll play with it somemore.




> **koenn said:**
> I've hard that BIND can actually support AD and its DNS requirements, but that it's hairy. I guess Petersonz post covers most of the issues.

If it's just a matter of having dhcp-asdsigned addresses registered in DNS, Bind doesn't allow this by default because having any random workstation writing to a DNS zone file is a breach of security and a possible attack vector, as it can lead to all sorts of hijacking, redirection, spoofing, ... etc. 

An alternative is to let the dhcp server (who knows the hostname/ipaddress combinations as it hands out the addresses) write to DNS. This may require the dhcp and dns server to authenticate to each other (using a key)
I don't know whether DNS Updates by clients (workstations) also requires authentication. 


What HermanAB is talking about are all sorts of additional records (and possible even some subdomains) which are required for AD to work, eg SRV records to tell the workstations the names/ipaddresses of Domain Controllers that they can log on to - that sort of stuff. It does indeed look very messy. 


Since you have to set up domain controllers anyway, I think you might as well just run DNS on them as well. If you have additional DNS needs, you can run BIND besides thos and work out some forwarding scheme.

---

