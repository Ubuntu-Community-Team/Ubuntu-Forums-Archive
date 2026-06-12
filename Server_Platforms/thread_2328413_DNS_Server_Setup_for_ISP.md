---
title: "DNS Server Setup for ISP"
date: 2016-06-20
forum: Server Platforms
---

### Post by soamz on 2016-06-20
Hi, we are a ISP and we currently use Google DNS IP, but we have to setup our own DNS server now, as google latency is very high in every 3-4 months. 

IS this the correct tutorial to this, 
[https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-an-authoritative-only-dns-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-an-authoritative-only-dns-server-on-ubuntu-14-04)

I have one Dell Server with with Xen, so one virtual instance of 8GB RAM and 50GB I have created. 
And kept 2 public IP free for this. 
Can I use this instance for DNS server and do as said in the above tutorial and setup both the IP as name servers, one for ns1 and ns2 and then setup reverse DNS records only ?

Please help!

---

### Post by Habitual on 2016-06-21
> **soamz said:**
> Can I use this instance for DNS server and do as said in the above tutorial and setup both the IP as name servers, one for ns1 and ns2 and then setup reverse DNS records only ?
I don't meant to be argumentative, but if you are an ISP, shouldn't you know this stuff?

If I understand correctly, you can.

ns1 = ip1
ns2 = ip2
Everything on one box? No slave-backup-secondary DNS?
Reverse is only important on mail hosts. </caffeine> # Never say 'never'...
Others may have something else to say about that statement.

Google's hiccup'y dns isn't the only game in town.

---

### Post by soamz on 2016-06-21
I went to my domain registrar and entered both the IP to ns1 of domain and the other Ip to ns2.

---

### Post by Habitual on 2016-06-21
Then you did so correctly.
Does the host called ns1 have bind, or similar installed?

---

### Post by soamz on 2016-06-21
> **Habitual said:**
> Then you did so correctly.
Does the host called ns1 have bind, or similar installed?

Yes BIND is installed. 
I just need to know, where I should check if the correct root DNS servers are set in its configuration. 

And then where to define in BIND that this IP is ns1 and this IP is ns2. 

And also, where to define the arpa format.

---

### Post by Habitual on 2016-06-21
> **soamz said:**
> And then where to define in BIND that this IP is ns1 and this IP is ns2. 
in the zone file of course.
How that's done manually, I shiver at the task. I usually rely on Webmin to do my initial bind setup.
There are many examples on the net for setting up bind with webmin.

GUI help utility or not,
You can  query your nameservers like so:
```
dig <record> @<ns1_ip> +short
``` or ```
dig <record> @<ns2_ip> +short
```

Actual example.
```
dig domain.com @xxx.yyy.zzz.aaa +short 
```
should return the A Record for the domain.com

Real live domain example:
```
host -t ns example.com
``` gives us the 2 nameservers for example.com
[PHP]example.com name server b.iana-servers.net.
example.com name server a.iana-servers.net.[/PHP]

host is a dns lookup utility
-t is "type of record"
-t ns is "show me nameservers"
example.com is the domain.tld

Let's see what a.iana-servers.net and b.iana-servers.net return for example.com
```
for i in a.iana-servers.net b.iana-servers.net ; do dig example.com @$i +short ; done
```
shows
93.184.216.34 for both. Good news :)

ns1.example.tld could be xxx.yyy.zzz.123 last year and xxx.yyy.zzz.234 next.
The ns1 indicator could change, it could be westcoast.domain.com 
It is very, very flexible.

I'm just not sure how this is setup without a GUI and that's sad, I've been at this for 
a number of years.

---

