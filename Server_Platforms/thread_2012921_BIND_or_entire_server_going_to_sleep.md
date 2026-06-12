---
title: "BIND or entire server going to sleep?"
date: 2012-06-30
forum: Server Platforms
---

### Post by cryptotheslow on 2012-06-30
Hi,

Simple setup here.

10.04 Server running BIND to provide DNS (no forwarders in the config, so querying root servers) to usually one 12.04 Desktop client. The 12.04 client has had dnsmasq removed so all DNS lookups go to the BIND server.

I'm seeing long DNS lookup delays in applications on the 12.04 client when querying DNS after a period of inactivity on the client.  e.g. Firefox will sit for upto 5 seconds with a status of "Looking up host xxxxxxxxx" before getting the response then displaying the page.

Initially I thought it was to do with TTLs and caching so turned to dig using a domain that has a low TTL...  first is right after I accessed the site, the second after the TTL expired - so 3msec and 138msec are not unreasonable for a cached and non-cached response respectively.

```

crypto@ubulaptop1204:~$ date && dig roguevampires.net
Sat Jun 30 05:54:10 BST 2012

; <<>> DiG 9.8.1-P1 <<>> roguevampires.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 13650
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;roguevampires.net.        IN    A

;; ANSWER SECTION:
roguevampires.net.    542    IN    A    213.175.213.194

;; AUTHORITY SECTION:
roguevampires.net.    542    IN    NS    ns1.impulsiveimagination.com.
roguevampires.net.    542    IN    NS    ns2.impulsiveimagination.com.

;; ADDITIONAL SECTION:
ns1.impulsiveimagination.com. 542 IN    A    213.175.213.194
ns2.impulsiveimagination.com. 542 IN    A    213.175.213.195

;; Query time: 3 msec
;; SERVER: 192.168.1.67#53(192.168.1.67)
;; WHEN: Sat Jun 30 05:54:10 2012
;; MSG SIZE  rcvd: 143

crypto@ubulaptop1204:~$ date && dig roguevampires.net
Sat Jun 30 06:17:57 BST 2012

; <<>> DiG 9.8.1-P1 <<>> roguevampires.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24277
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;roguevampires.net.        IN    A

;; ANSWER SECTION:
roguevampires.net.    600    IN    A    213.175.213.194

;; AUTHORITY SECTION:
roguevampires.net.    600    IN    NS    ns2.impulsiveimagination.com.
roguevampires.net.    600    IN    NS    ns1.impulsiveimagination.com.

;; ADDITIONAL SECTION:
ns1.impulsiveimagination.com. 600 IN    A    213.175.213.194
ns2.impulsiveimagination.com. 600 IN    A    213.175.213.195

;; Query time: 138 msec
;; SERVER: 192.168.1.67#53(192.168.1.67)
;; WHEN: Sat Jun 30 06:17:57 2012
;; MSG SIZE  rcvd: 143

```

So - not really the time the lookup takes that is delaying things.

If I leave the client idle for an hour or so and do a dig from a terminal there is a 5 - 10 second delay and then the response comes back saying the lookup took ~150msec.

I'm at a loss as to whether this is BIND on the server going to sleep or the server as a whole is dozing off.

What can I check for either sleepy settings on the server or BIND specifically?

Thanks for reading my rambling :lolflag:

---

### Post by cryptotheslow on 2012-07-04
OK I think I solved this thanks to this wiki: [http://wiki.kartbuilding.net/index.php/DNS_-_Bind9#Slow_DNS_lookup_issues_with_bind9](http://wiki.kartbuilding.net/index.php/DNS_-_Bind9#Slow_DNS_lookup_issues_with_bind9)

That suggests BIND9 will attempt to use IPv6 lookups before moving on to use IPv4 when the IPv6 request times out (no IPv6 on my LAN or my ISP).

So looking at /var/log/syslog I see stacks of entries like this from named:
```

Jul  5 02:41:09 ubuserver named[3752]: error (network unreachable) resolving 'www-bytemark-v4v6.gentoo.org/A/IN': 2001:7f8:23:323::1e#53
Jul  5 02:41:09 ubuserver named[3752]: error (network unreachable) resolving 'ns10.az.pl/AAAA/IN': 2001:500:1::803f:235#53
Jul  5 02:41:10 ubuserver named[3752]: error (network unreachable) resolving 'unix.org.ua/A/IN': 2a03:6300:1:102::3#53
Jul  5 02:41:26 ubuserver named[3752]: error (network unreachable) resolving 'del.icio.us/A/IN': 2001:500:3682::11#53
Jul  5 02:41:26 ubuserver named[3752]: error (network unreachable) resolving 'ns1.p27.dynect.net/AAAA/IN': 2001:500:94::100#53
Jul  5 02:41:26 ubuserver named[3752]: error (network unreachable) resolving 'ns1.p08.dynect.net/A/IN': 2001:500:90::100#53
Jul  5 02:41:26 ubuserver named[3752]: error (network unreachable) resolving 'ns1.p08.dynect.net/AAAA/IN': 2001:500:90::100#53
Jul  5 02:41:26 ubuserver named[3752]: error (network unreachable) resolving 'ns2.p08.dynect.net/A/IN': 2001:500:90::100#53
Jul  5 02:41:26 ubuserver named[3752]: error (network unreachable) resolving 'reddit.com/A/IN': 2001:503:a83e::2:30#53
Jul  5 02:41:27 ubuserver named[3752]: error (network unreachable) resolving 'ns1.isc-sns.net/AAAA/IN': 2001:470:1a::1#53
Jul  5 02:41:27 ubuserver named[3752]: error (network unreachable) resolving 'red.freebsd.org/A/IN': 2001:5a0:10::1#53
Jul  5 02:41:27 ubuserver named[3752]: error (network unreachable) resolving 'www.netbsd.org/A/IN': 2607:f140:ffff:fffe::3#53

```

Presumably the root servers return both IPv6 and IPv4 nameserver records for a domain where set, BIND then tries to make an IPv6 DNS request to the domain's nameserver even though the server has no active IPv6 connection which delays things while it times out.

So I changed two things.

```
sudo nano named.conf.options
```
And changed:
listen-on-v6 { any; }
to
listen-on-v6 { none; }

```
sudo nano /etc/default/bind9
```
And changed:
# startup options for the server
OPTIONS="-u bind"
to
# startup options for the server
OPTIONS="-4 -u bind"

That has stopped all the syslog messages and so far appears to have resolved the resolution delays I was seeing.

---

### Post by cryptotheslow on 2012-07-09
OK, well the above helped somewhat but didn't resolve the problem.

I finally tracked it down to a "feature" of the Western Digital Caviar Green hard drive that is in the server. In order to save a little power it unloads the heads after just a few seconds of idle time. This causes slight delays when the heads need to be loaded back up.

More worryingly it has a nasty side-effect when using an ext4 filesystem in that no sooner has the drive parked the heads then the journalling process comes along and makes them load up again - over and over and over again.

Looking at the SMART data on the drive this issue leads to this:
```

9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3438
193 Load_Cycle_Count        0x0032   047   047   000    Old_age   Always       -       460814

```

So in just 5 months of uptime the drive has already far exceeded it's quoted serviceable limit of 300,000 load cycles.

Western Digital do have a DOS based utility that allows this idle behaviour to be stopped. Thankfully someone has created a *nix port of it's functionality called idle3-tools.

[http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/)

So if you have a WD EADS or EARS drive in a server or NAS device with a journalling filesystem I strongly recommend you check it's not going bananas on the load cycle count!

---

