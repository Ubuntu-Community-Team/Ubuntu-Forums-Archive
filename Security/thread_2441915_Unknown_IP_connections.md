---
title: "Unknown IP connections"
date: 2020-04-27
forum: Security
---

### Post by justtom2 on 2020-04-27
Hey,

Sorry if this is completely expected behaviour. 

Upon a fresh install of transmission-daemon from Ubuntu repository, transmission will establish numerous (60+) outgoing connections to servers across the world. 

No torrents have been added and I cannot understand why on earth that many servers are needed for telemetry. 

A sample of the connections are as such:


udp	ubuntu	51413	Redacted-destination	32992	
udp	ubuntu	51413	Redacted-destination	51413	
udp	ubuntu	51413	Redacted-destination	6881	
udp	ubuntu	51413	Redacted-destination	44558	
udp	ubuntu	51413	Redacted-destination	32205	
udp	ubuntu	51413	Redacted-destination	40952	
udp	ubuntu	51413	Redacted-destination	6881	
udp	ubuntu	51413	Redacted-destination	6881	
udp	ubuntu	51413	Redacted-destination	59777	
udp	ubuntu	51413	Redacted-destination	49643	
udp	ubuntu	51413	Redacted-destination	32992	
udp	ubuntu	51413	Redacted-destination	61098

I'm sure this is most likely legitimate behaviour but thought I would check. The other alternative is pretty crazy to think of. 

Kind regards,
Tom

---

### Post by EuclideanCoffee on 2020-04-28
These IPs don't appear to belong to Canonical, so I don't think this is telemetry... though it's completely possible and don't have an argument that it cannot be telemetry on the application's side, which I would find surprising.

I checked the ports. Some are definitely BitTorrent, but others are random.

Are you positive this behavior only begins after you finish installing the application? I would expect you'd only see this behavior after running the daemon. But only after you install the application, I'm a bit confused... If you were just pulling data, I would expect 443 or 80 not such a strange assortment, especially from apt.

If you're on a torrent website, service, or client, you'd see traffic like this as well, as the client needs to find possible torrents. And in order to do this, I'm sure there's an outgoing connection to some server... whether that is the IP of the peer seeding the data, not sure.

I typically only see 443 data on websites, but depending on their services, I've seen other protocols. Maybe try closing your browser, re-install, and see if the behavior reoccurs.

---

### Post by justtom2 on 2020-04-28
Hey cheers for the reply,

Upon installation of transmission-daemon it is enable automatically (this is the norm).

This traffic has nothing to do with the installation of transmission from the repo, that would indeed link to canonical servers. The data transfer from the repo has already taken place and I have not included it in these logs. 

This traffic is coming directly from transmission Daemon on its default port immediately after first time startup (on install) - when I refer to telemetry I mean telemetry to transmission servers not canonical. You can see it leaving transmissions default port (51413) and connecting to those servers and their different ports.  

I just cannot fathom why there should be over 70 servers it connects to. - no torrents etc added, fresh install. (purged and repeated with same result)

---

### Post by EuclideanCoffee on 2020-04-28
And I don't think those IPs are owned by Transmission. I would hide the IPs. They may be residential and belong to actual people who may have a legitimate use.

---

### Post by justtom2 on 2020-04-28
It is impossible they are residential IPs. 

My firewall blocks all incoming ports by default and I had not yet added a rule to allow incoming connections. 

These are all outgoing connections which transmission is initiating by itself. Just to reiterate this is a fresh install on a fresh Ubuntu server. No torrents had been added and no default  configurations have been changed. 

However, out of an abundance of caution I will remove the destination ips but leave the destination port numbers so people can get a jist of what is happening. 

Would be great if someone else can see if this happens on their end too?

---

### Post by EuclideanCoffee on 2020-04-29
Thanks for removing the addresses, as it protects users' privacy.

> 
It is impossible they are residential IPs.


If the residential address is a transmission server, it is not impossible. But the user may not be aware that your host can see them while you are blocking them (from incoming, meaning from peer to localhost). And from my understanding, BitTorrent does not need port forwarding to work. This is why we see them on university campuses, etc. The same happens on Puppet using web protocols. You don't need port forwarding to tell a computer to run a task from the Puppet server, even if you're on separate networks.

I do not use torrents because regardless of my router configuration, I can still seed.

---

### Post by SeijiSensei on 2020-04-29
One way to see how busy these connections are is to add some iptables rules like this:
```

sudo /sbin/iptables -A OUTPUT -p udp -d redacted-IP1 -j LOG
sudo /sbin/iptables -A OUTPUT -p udp -d redacted-IP2 -j LOG
[...]

```
The command "sudo iptables -L -nv" will display totals for each IP address.  Also the traffic itself will be logged to /var/log/kern.log  

If there's a lot of traffic, the log may fill up quickly. If so, you may want to stop logging and just use
```

sudo /sbin/iptables -A OUTPUT -p udp -d redacted-IP1 -j ACCEPT
sudo /sbin/iptables -A OUTPUT -p udp -d redacted-IP2 -j ACCEPT
[...]

```
The "sudo iptables -L -nv" command will still show totals.

I presume you've already run reverse-IP lookups for these hosts with 
```
host -t ptr redacted-IP1
```
etc.

---

### Post by justtom2 on 2020-04-29
Cheers. I've found out it could possibly be transmission-daemon connecting to the distributed hash table. 

I just didn't expect this to happen right away after a clean install before torrents added.

I know P2P doesn't need port forwarding to work (although it can hinder seeding without), my point was that these connections were being established by the program itself without any torrents added which was extremely confusing. 

However now I know that transmission will connect to the DHT network even if no torrents are added this makes sense

---

### Post by EuclideanCoffee on 2020-04-29
So those were residential IP addresses associated with a distributed hash table, which I surmise is a pool of users?

Please mark as solved for archival purposes, Tom. Thanks.

---

### Post by justtom2 on 2020-04-30
Will do. Thanks for the help :)

---

