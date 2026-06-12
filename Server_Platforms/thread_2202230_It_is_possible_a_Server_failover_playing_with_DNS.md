---
title: "It is possible a Server failover playing with DNS ?"
date: 2014-01-28
forum: Server Platforms
---

### Post by nilla78ro on 2014-01-28
Hello, I'm using virtual private servers(VPS) for hosting, the main problem is the uptime, those VPS's are not managed and also very cheap so the uptime is an issue.

To solve this issue I'm thinking if i can go to uptime almost 100% playing with DNS server and use two cheap VPS?

At registrar I'm thinking to set ns1 to vps1 and ns2 to vps2 , both vps's will have a DNS server and will resolve the www.<domain> to the server ip , and setting TTL to 5 minutes to prevent the case when a vps will go down .
 so in this solution I'm seeing vps1 as master and vps2 as backup and as active failover server when the first server is down.

Any one are using something like this?
I'm missing something ?
What may not be OK ?
Thanks.

---

### Post by TheFu on 2014-01-28
DNS has redundancy built into the protocol. Why not just use that?

I'd setup 2 DNS slaves available to everyone in the world and 1 DNS master that cannot be reached on the internet, but pushes any changes to the slaves immediately.  Might as well try to be secure when playing with DNS - the 2nd most likely internet service to be hacked - following the best practices.  Don't forget to run bind in a chroot too.

---

### Post by nilla78ro on 2014-01-28
Maybe i was not clear, i'm trying to explain with more details
vps 1 (with ip z.z.z.z) on this server i'll have in dns something like : z.z.z.z A www.<the domain>
vps 2 (with ip q.q.q.q) on this server i'll have in dns something like : q.q.q.q A www.<the domain>
at registrar i'll have ns1 pointing to z.z.z.z and ns2 pointing to q.q.q.q
so, it the vps1 who will be the 1st server will go down then all dns request will be handled by vps 2 and the domain will be resolved as been on vps2. when vps1 will be back again it will takeover the domain. 
I want to create something like is a dynamic dns .

---

### Post by sandyd on 2014-01-28
> **nilla78ro said:**
> Maybe i was not clear, i'm trying to explain with more details
vps 1 (with ip z.z.z.z) on this server i'll have in dns something like : z.z.z.z A www.<the domain>
vps 2 (with ip q.q.q.q) on this server i'll have in dns something like : q.q.q.q A www.<the domain>
at registrar i'll have ns1 pointing to z.z.z.z and ns2 pointing to q.q.q.q
so, it the vps1 who will be the 1st server will go down then all dns request will be handled by vps 2 and the domain will be resolved as been on vps2. when vps1 will be back again it will takeover the domain. 
I want to create something like is a dynamic dns .
example: (adjust to make script swap the zones when ping happens and zone was swapped). Also make sure that this wont cause bind9 to flap between the zones
Where server 1 = 192.168.0.101 and 2 = 192.168.0.2

On Server 2
```

#!/bin/bash

FAILS=0
SERVER="192.168.0.101"
SLEEP=60
FAILED=0

while true; do
    ping -c 1 $SERVER >/dev/null 2>&1
    if [ $? -ne 0 ] ; then #if ping exits nonzero...
        FAILS=$[FAILS + 1]
    else
        FAILS=0
    fi
    if [ $FAILS -gt 4 ]; then
        FAILS=0
        #swap zone and apply
        cp /var/lib/bind/server2 /var/lib/bind/default
        service bind9 restart
        FAILED=1
    fi
    sleep $SLEEP #check again in SLEEP seconds
done

if [ $FAILED -eq 1 ]; then
 #check if it is accessable again so that you can move the bind zones back
fi

```

---

### Post by TheFu on 2014-01-28
There are a few issues with using DNS as a failover - clients determine how long any DNS record is retained - so that "failover" might take a reboot of the client device to work or 30 minutes to a day. Is that a failover?

I believe DNS is best used for load balancing or complete failover that lasts a while. Pre-connected clients will be stuck on the wrong IP for awhile, but eventually make a fresh DNS request. [http://www.zytrax.com/books/dns/ch9/rr.html](http://www.zytrax.com/books/dns/ch9/rr.html) discusses some of the methods and issues.

Something like HAProxy (run redundant instances) or using nginx as a reverse proxy might be smarted. Not certain that I understand your end-goal.
Is DNS the only service you are trying to setup? No email, no web, no SIP, nothing else except DNS?

From a design standpoint, it is critical to understand how "network-near" the DNS and domain servers are to each other. Solutions for LAN-near are different from those for WAN-far. There are liabilities if each are on the same ISP link.

Not really certain I understand the last line.  If you want to make a DynDNS clone, then the slave, slave, master setup is best.

Or I could be completely misunderstanding the problem?

---

### Post by nilla78ro on 2014-01-30
The goal is to have the web server uptime almost 100% with low quality hosting :), this solution may work with wordpress or not intensive db changes applications
@sabdyd : thanks for sugessting to change dns setup on 2nd server ... without this the visitors was balanced between servers

---

### Post by TheFu on 2014-01-30
Ahhhhh I get it.  Don't think "failover", instead think "load balanced" for the websites. This way any box running your website can be available. This is a very common solution pattern. [http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster](http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster)

Is there a DB involved?  Then just work out the 2-way "master-master" replication. [http://www.howtoforge.com/mysql_master_master_replication](http://www.howtoforge.com/mysql_master_master_replication) other DBs do this too, like postgress.
The php and static files really aren't much concern, just the data.

How close are these VPS boxes?  If they are in the same building, then use dual reverse proxies in a cluster to direct traffic. A reverse proxy will know if one of the "back-ends" is unavailable. That is built-in.  You can use an outside machine to poll the reverse proxy - if it is down, either restart it or bring it up on another VPS with the replicated DB.

I've been running an nginx reverse proxy for a few years this way  it has never crashed. Not once.

If the servers are far apart, you can still use the dual reverse proxies, but some more smarts will be needed - those should be easily scriptable. A delayed answer means the remote location is down.  Again, this is a very common solution pattern.

No need to do anything funky with DNSes. Just standard RR resolution.  BTW, I outsource my DNS needs to reputable DNS providers. If you have less than 20 domains, this makes sense and is highly cost effective - less than $20/yr.  You can still run DNS internally for LAN users.

[https://serverfault.com/questions/189290/how-use-dns-server-to-create-simple-ha-high-availability-of-my-website](https://serverfault.com/questions/189290/how-use-dns-server-to-create-simple-ha-high-availability-of-my-website) and [https://serverfault.com/questions/69870/multiple-data-centers-and-http-traffic-dns-round-robin-is-the-only-way-to-assur](https://serverfault.com/questions/69870/multiple-data-centers-and-http-traffic-dns-round-robin-is-the-only-way-to-assur) might help too.

---

