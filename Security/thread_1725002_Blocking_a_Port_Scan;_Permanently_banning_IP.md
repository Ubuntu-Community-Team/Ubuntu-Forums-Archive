---
title: "Blocking a Port Scan; Permanently banning IP"
date: 2011-04-09
forum: Security
---

### Post by drhiii on 2011-04-09
I've been rooting around trying to find anything that will do those two things...

When a port scan takes place, be able to block the offending in its tracks, and....

Block the offending IP permanently.   

There used to be a wonderful old tool called 'portscan' that did this.   When you defined a port in its configuration file, the instant that port was touched, wham, it would DENY the offending IP from any further access.   

This is all I am trying to do.   Define a known port, or ports, and if anything tries to touch that port, add the IP to a blacklist.  

Help anyone?  I have tried CSF and I thought I had very strong policies set up, then ran an Nmap scan from another system and it merrily did a port walk of the entire server and was never blocked, and never added to a ban list.   

Is there anything that will just stop a port scan in its tracks, and create a blacklist of offending IPs?

tx

---

### Post by brian_p on 2011-04-09
> **drhiii said:**
> I've been rooting around trying to find anything that will do those two things...

When a port scan takes place, be able to block the offending in its tracks, and....

Block the offending IP permanently.

You could look at and evaluate psad.

---

### Post by listerdl on 2011-04-10
> **brian_p said:**
> You could look at and evaluate psad.

i guess you want to block an IP like as in the .htaccess on a server?

Cant an IP be spoofed though? If this is to prevent a hacker or someone then they will likely work around the block.

My site was hacked into from a Russian IP so I simply blocked the entire country - possible for me since I get zero business from that part of the world....

Just my $0.02

---

### Post by bodhi.zazen on 2011-04-10
> **brian_p said:**
> You could look at and evaluate psad.

Another vote for psad =)

Just to play devils advocate, who cares about port scans ? What server(s) are you running ? Harden them and port scans are then insignificant.

---

### Post by HermanAB on 2011-04-10
Howdy,

In my experience, it is not necessary to be totally draconian.  It is sufficient to use iptables to rate limit connection attempts.  That causes miscreants to move on and go pester someone else and then you don't have the issue of accidentally locking yourself out with a block list.

The following one liner will stop pretty much all attempts at mischief and is the ONLY rule I use to protect my web and mail servers:

```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

---

### Post by bodhi.zazen on 2011-04-10
> **HermanAB said:**
> In my experience, it is not necessary to be totally draconian.

To add to that somewhat ...

Nothing like reading the logs to install paranoia =)

Banning an IP is of limited benefit as :

1. IP are easily spoofed.

2. IP are not unique identifiers, many (if no most/all) ISP use DHCP, so you are going to ban legitimate traffic as well.

3. A new IP is easily obtained (see #2 above).

4. Many scans come from compromised machines (it would be a sloppy cracker who used his or her actual IP address to scan you with).

5. Many IP are shared. For example a public IP may be shared by a large corporation or educational institution, and so again you are going to block legitimate traffic.

Blacklisting IP often hurts legitimate traffic more then would be crackers.

Probably several other reasons as well. It does vary, IMO, bu server. a public ftp or http is not the same as ssh or nfs or samba (which IMO should not be used over the internet anyways).

---

