---
title: "Question about blocking access from countries..."
date: 2006-11-25
forum: Server Platforms
---

### Post by Kurt` on 2006-11-25
Hi,

My Edgy server has been getting hammered by port scans and SSH attacks from foreign countries that normally have no business visiting sites on my server (China, Taiwan, Brazil, etc.).

Is there a simple way to deny entire COUNTRIES from visiting my server? I don't mean just blocking them from Apache, I mean something for /etc/hosts.deny or the like.

I've tried Googling and searching the forums here, but I've only found ways to block access to specific daemons.

Any advice would be appreciated.

(If it matters, I have a BIND9 installation on the machine, so caching lookups is taken care of)

Thanks! :D

Edit:

I just remembered that a lot of these attacking IPs don't even have reverse lookups, am I better off just finding a list of IP ranges assigned to countries and blocking them?

---

### Post by stickboy2642 on 2006-11-26
Your best bet is to use iptables to block out unwanted traffic to your computer.  You can block out all ports on your server to the IP blocks in question if you so desire.  It is a good idea to set up a firewall with iptables anyway, and block everything that you do not want random people connecting to (for example, ssh should be open only to those who really need to ssh into the machine).

You can use the whois command to determine the IP range that a specific ISP or network uses so that you know what IPs to block. Doing a whois lookup on a specific IP address will return information about the network that contains that IP address.  Most importantly, it will return the range of ip addresses maintained by that organization in the NetRange field.  You can then use that range to block all traffic from that ISP or organization.  The whois.arin.net server is good about returning information based on the  IP address.  I don't think you will have a lot of luck blocking entire countries per se as the IP ranges are all over the map, but if you keep blocking IP ranges as you find them, you will likely notice that this type of traffic diminishes over time.  

```

root@laptop:/var/log/installer# whois -h whois.arin.net 204.115.2.65

OrgName:    Hughes Communications Inc. 
OrgID:      HUGHES-5
Address:    1990 East Grand Ave.
Address:    S67 / D454
City:       El Segundo
StateProv:  CA
PostalCode: 90245
Country:    US

NetRange:   204.115.0.0 - 204.115.5.255 
CIDR:       204.115.0.0/22, 204.115.4.0/23 
NetName:    HUGHES-2
NetHandle:  NET-204-115-0-0-1
Parent:     NET-204-0-0-0-0
NetType:    Direct Assignment
Comment:    
RegDate:    1994-09-19
Updated:    1994-09-19

RTechHandle: MW133-ARIN
RTechName:   Wittrock, Matthew 
RTechPhone:  +1-310-607-4660
RTechEmail:   

# ARIN WHOIS database, last updated 2006-11-25 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

```

Hope this helps!

---

### Post by Kurt` on 2006-11-26
Yeah, I already have iptables set up (only allowing incoming on 22, 25, 80, 443, etc.), everything else gets ICMP "port unreachable", which seems to mess with people trying to port scan (makes scans take forever :D).

I'm familiar with whois, nslookup, and all the domain-/ip-related command-line tools. I was just wondering if there was an elegant and simple way to say "All traffic from .<tld> is dropped".

---

### Post by MJN on 2006-11-26
> **Kurt` said:**
> "All traffic from .<tld> is dropped".

Ah, but now you're talking DNS. The DNS namespace bears little alignment to geographical IP distribution.... just think of all the .com's for a case in point (although not that relevent in this particular scenario).

I wouldn't worry about it if I were you - we're all getting it - just make sure you're secure and let 'em knock away... at least while they're spending time testing your server they're not testing the next one which might not be so locked down!

Mathew

---

