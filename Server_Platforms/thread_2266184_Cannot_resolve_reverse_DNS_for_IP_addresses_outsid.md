---
title: "Cannot resolve reverse DNS for IP addresses outside our domain"
date: 2015-02-20
forum: Server Platforms
---

### Post by Chad_Carson on 2015-02-20
Hello, all,

I'm just wanting to see if this is a problem or something that is "by design".

On Ubuntu Server 14.04, I have a split DNS set up (handing out public IP addresses to
for our domain to the outside world, 10.x.x.x to my internal customers).

If I use the "host" or "nslookup" either one to resolve my OWN host names or IP addresses, it works,
both forward and reverse. 

If I do host on an external domain it works, but if I do "host" on an external IP address to get the
reverse DNS lookup PTR address, I get SERVFAIL.

I thought it may have something to do with my split DNS, but I installed a brand new 14.04 server,
installed BIND, added nothing, and the same thing happens on it, too.

However, if I redirect my host command at Google DNS 8.8.8.8 it works as I expect, and gives me the reverse lookup right away.

Sample session below so you can see what I mean...NOTE: this is on a new install of 14.04, new install of BIND9, right out of the box,
no config changes whatsoever from the defaults.


[FONT=courier new]me@Ubuntu:~$ host ubuntuforums.org
ubuntuforums.org has address 91.189.94.12

me@Ubuntu:~$ host 91.189.94.12
Host 12.94.189.91.in-addr.arpa not found: 2(SERVFAIL)

me@Ubuntu:~$ host 91.189.94.12 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 

12.94.189.91.in-addr.arpa domain name pointer feijoa.canonical.com.[/FONT]



So, my question is "is this normal behavior for Bind9 on Ubuntu?"
If not, what do you think the problem could be especially if this is doing this on
a brand new, unaltered installation?   My first thought is something firewall related,
but I would think if that was the case I would not be able to do ANY lookups
at all, forward OR reverse, not just reverse lookups.

Thanks for any input you can give me.

---

### Post by darkod on 2015-02-20
That is a PTR but the real question is is it your PTR? You own canonical.com?

The problem with reverse DNS (PTR) is that hosting/ISP providers buy and own the IP blocks. So usually you need their help for a properly working public PTR. I had similar issues helping a friend set up a PTR for his hosted mailserver. We tried various combinations in his DNS but only after he contacted the hosting provider to do it, it worked right away.

I think the PTR control by the owner/provider makes sense otherwise anyone can set a "wrong" PTR about some domain and release it in the internet space. You can't allow that. Having a config in BIND should not be enough, right? You can set what ever you want in there...

So, from my (limited) experience, you will need the help of where ever you have the IP from... I might be wrong though. :)

---

### Post by Doug S on 2015-02-20
works fine for me (I run an internal DNS using bind9):```
doug@doug-64:~/config/apache2$ host ubuntuforums.org
ubuntuforums.org has address 91.189.94.12
doug@doug-64:~/config/apache2$ host 91.189.94.12
12.94.189.91.in-addr.arpa domain name pointer feijoa.canonical.com.
doug@doug-64:~/config/apache2$ host s15
s15.smythies.com has address 192.168.111.112
doug@doug-64:~/config/apache2$ host 192.168.111.112
112.111.168.192.in-addr.arpa domain name pointer s15.smythies.com.
```Note that bind9 is one package that doesn't work properly "right out of the box", it needs to be configured.
It is not clear to me what is wrong. Perhaps monitor port 53 traffic with a packet sniffer.```
sudo tcpdump -n -nn -tttt -i eth1 port 53
```change eth1 to whatever interface is your external one. I cannot give an example from my computer because the answer is now cached.

---

### Post by Chad_Carson on 2015-02-23
Well, maybe this is all because I am just letting queries to go the root servers.
A TCPDUMP when I do a HOST 91.189.94.12 shows that my server is trying to 
contacting these three servers, c.in-addr-servers.arpa, fc.in-addr-servers.arpa, anysec.apnic.net,
but no response is coming back from them.

If I instead point to Google Public DNS or OpenDNS servers, I get the
expected result instantly.  I cannot find anything online about it,
but are PTR queries directly to the in-addr-servers.arpa prohibited?
If I use the HOST command directly to these servers I get no results,
so maybe this is by design, and I need to point instead to Google
or OpenDNS or an upstream ISP DNS server.


```
root@Ubuntu# host 91.189.94.12 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 

12.94.189.91.in-addr.arpa domain name pointer feijoa.canonical.com.

root@Ubuntu:# host 91.189.94.12 f.in-addr-servers.arpa
Using domain server:
Name: f.in-addr-servers.arpa
Address: 193.0.9.1#53
Aliases: 

12.94.189.91.in-addr.arpa has no PTR record

root@Ubuntu:# host 91.189.94.12 c.in-addr-servers.arpa
Using domain server:
Name: c.in-addr-servers.arpa
Address: 196.216.169.10#53
Aliases: 

12.94.189.91.in-addr.arpa has no PTR record

root@Ubuntu:# host 91.189.94.12 anysec.apnic.net
Using domain server:
Name: anysec.apnic.net
Address: 203.119.86.101#53
Aliases: 

12.94.189.91.in-addr.arpa has no PTR record


```

---

### Post by Doug S on 2015-02-23
I no longer specify any forwarder. Here is my file:```
doug@doug-64:~/config/bind$ [COLOR=#ff0000]cat named.conf.options[/COLOR]
options {
        directory "/var/cache/bind";

        recursion yes;
        allow-recursion {any;};
        allow-query {any;}; // this is needed to override the default
        allow-transfer {"none"; }; // transfer will be allowed per zone below.

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

//      forwarders {
//              75.153.176.9;
//              75.153.176.1;
//      };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { none; };

        sortlist {
                {// preference block start
                        0.0.0.0/0;  // For any client IP
                        {192.168.111.222/32;   // return this response as 1st preference
                        };
                }; // end first block (only block, in this case)
        }; // end sortlist
};
```

---

### Post by Chad_Carson on 2015-02-23
Thank you for confirming that for me.

I am working with my upstream provider as a next step...I suspect they have some kind of 
network policy or firewall block (either intentional or maybe by accident) that is killing these 
responses back from the root servers.

Thank you!

---

### Post by Doug S on 2015-02-23
But my DNS isn't limited to only root name servers. It goes to many, I suspect as learned over time. I get the same response as you if I force it. ```
doug@doug-64:~/config/bind$ host 91.189.94.12 f.in-addr-servers.arpa
Using domain server:
Name: f.in-addr-servers.arpa
Address: 193.0.9.1#53
Aliases:

12.94.189.91.in-addr.arpa has no PTR record
```Later today I might be able to try a test after a fresh re-boot. see also [this older thread]("http://ubuntuforums.org/showthread.php?t=2253128&highlight=forwarder").

---

### Post by SeijiSensei on 2015-02-23
> **Doug S said:**
> But my DNS isn't limited to only root name servers. It goes to many, I suspect as learned over time. I get the same response as you if I force it. ```
doug@doug-64:~/config/bind$ host 91.189.94.12 f.in-addr-servers.arpa
Using domain server:
Name: f.in-addr-servers.arpa
Address: 193.0.9.1#53
Aliases:

12.94.189.91.in-addr.arpa has no PTR record
```Later today I might be able to try a test after a fresh re-boot. see also [this older thread]("http://ubuntuforums.org/showthread.php?t=2253128&highlight=forwarder").
That's because f.in-addr-servers.arpa isn't authoritative for 94.189.91.in-addr.arpa:
```

$ host -t ns 94.189.91.in-addr.arpa
94.189.91.in-addr.arpa name server ns1.canonical.com.
94.189.91.in-addr.arpa name server ns3.canonical.com.
94.189.91.in-addr.arpa name server ns2.canonical.com.

$ host -t ptr 12.94.189.91.in-addr.arpa
12.94.189.91.in-addr.arpa domain name pointer feijoa.canonical.com.

$ host -t ptr 12.94.189.91.in-addr.arpa ns1.canonical.com
Using domain server:
Name: ns1.canonical.com
Address: 91.189.94.173#53
Aliases: 

12.94.189.91.in-addr.arpa domain name pointer feijoa.canonical.com.

```

---

### Post by Doug S on 2015-02-23
Seiji: Yes, of course. I was trying to show that is doesn't work that way for me either.

Because I am behind on updates, I did them on my main server and re-booted. Thus I didn't have anything cached anymore. This is what I got for "host host 91.189.94.12":```
doug@doug-64:~$ sudo tcpdump -n -nn -tttt -i eth1 port 53
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
2015-02-23 13:33:36.898922 IP 173.180.XXX.YYY.60922 > 128.63.2.53.53: 61242 [1au] PTR? [COLOR=#ff0000]12.94.189.91.in-addr.arpa[/COLOR]. (54)
2015-02-23 13:33:36.898951 IP 173.180.XXX.YYY.61737 > 128.63.2.53.53: 30424 [1au] NS? . (28)
2015-02-23 13:33:37.037495 IP 128.63.2.53.53 > 173.180.XXX.YYY.60922: 61242- 0/8/13 (642)
2015-02-23 13:33:37.038108 IP 173.180.XXX.YYY.41822 > 193.0.9.1.53: 11765 [1au] PTR? [COLOR=#ff0000]12.94.189.91.in-addr.arpa[/COLOR]. (54)
2015-02-23 13:33:37.040292 IP 128.63.2.53.53 > 173.180.XXX.YYY.61737: 30424*- 14/0/25 NS a.root-servers.net., NS b.root-servers.net., NS c.root-servers.net., NS d.root-servers.net., NS e.root-servers.net., NS f.root-servers.net., NS g.root-servers.net., NS h.root-servers.net., NS i.root-servers.net., NS j.root-servers.net., NS k.root-servers.net., NS l.root-servers.net., NS m.root-servers.net., RRSIG (913)
2015-02-23 13:33:37.193689 IP 193.0.9.1.53 > 173.180.XXX.YYY.41822: 11765- 0/9/1 (466)
2015-02-23 13:33:37.194350 IP 173.180.XXX.YYY.37709 > 192.112.36.4.53: 2875% [1au] A? ns3.nic.fr. (39)
2015-02-23 13:33:37.194587 IP 173.180.XXX.YYY.24837 > 192.112.36.4.53: 21021 [1au] NS? . (28)
2015-02-23 13:33:37.194961 IP 173.180.XXX.YYY.27027 > 192.41.162.30.53: 44810% [1au] A? tinnie.arin.net. (44)
2015-02-23 13:33:37.194992 IP 173.180.XXX.YYY.3345 > 192.41.162.30.53: 24500% [1au] A? pri.authdns.ripe.net. (49)
2015-02-23 13:33:37.195131 IP 173.180.XXX.YYY.29557 > 192.41.162.30.53: 24704% [1au] A? sec1.apnic.net. (43)
2015-02-23 13:33:37.195295 IP 173.180.XXX.YYY.49608 > 192.41.162.30.53: 61189% [1au] A? sec3.apnic.net. (43)
2015-02-23 13:33:37.195452 IP 173.180.XXX.YYY.39052 > 192.112.36.4.53: 44838% [1au] A? sns-pb.isc.org. (43)
2015-02-23 13:33:37.250883 IP 192.41.162.30.53 > 173.180.XXX.YYY.27027: 44810- 0/7/9 (535)
2015-02-23 13:33:37.251317 IP 173.180.XXX.YYY.3474 > 199.71.0.108.53: 14073% [1au] A? tinnie.arin.net. (44)
2015-02-23 13:33:37.253324 IP 192.41.162.30.53 > 173.180.XXX.YYY.29557: 24704- 0/11/14 (732)
2015-02-23 13:33:37.254051 IP 173.180.XXX.YYY.60116 > 202.12.29.59.53: 57227% [1au] A? sec1.apnic.net. (43)
2015-02-23 13:33:37.254278 IP 173.180.XXX.YYY.41344 > 192.48.79.30.53: 14542% [1au] A? ns4.apnic.com. (42)
2015-02-23 13:33:37.255015 IP 192.41.162.30.53 > 173.180.XXX.YYY.3345: 24500- 0/9/9 (608)
2015-02-23 13:33:37.255392 IP 173.180.XXX.YYY.51110 > 202.12.29.59.53: 49943% [1au] A? pri.authdns.ripe.net. (49)
2015-02-23 13:33:37.257076 IP 192.41.162.30.53 > 173.180.XXX.YYY.49608: 61189- 0/11/14 (737)
2015-02-23 13:33:37.257456 IP 173.180.XXX.YYY.17647 > 202.12.29.59.53: 38592% [1au] A? sec3.apnic.net. (43)
2015-02-23 13:33:37.290839 IP 192.112.36.4.53 > 173.180.XXX.YYY.24837: 21021*- 14/0/25 NS m.root-servers.net., NS e.root-servers.net., NS a.root-servers.net., NS i.root-servers.net., NS c.root-servers.net., NS l.root-servers.net., NS d.root-servers.net., NS b.root-servers.net., NS j.root-servers.net., NS h.root-servers.net., NS f.root-servers.net., NS k.root-servers.net., NS g.root-servers.net., RRSIG (913)
2015-02-23 13:33:37.292474 IP 192.112.36.4.53 > 173.180.XXX.YYY.37709: 2875- 0/8/11 (598)
2015-02-23 13:33:37.292862 IP 173.180.XXX.YYY.50988 > 194.146.106.46.53: 14549% [1au] A? ns3.nic.fr. (39)
2015-02-23 13:33:37.297913 IP 192.112.36.4.53 > 173.180.XXX.YYY.39052: 44838- 0/9/13 (688)
2015-02-23 13:33:37.298322 IP 173.180.XXX.YYY.14976 > 199.249.120.1.53: 61997% [1au] A? sns-pb.isc.org. (43)
2015-02-23 13:33:37.307366 IP 199.71.0.108.53 > 173.180.XXX.YYY.3474: 14073*- 2/5/17 A 199.212.0.53, RRSIG (1248)
2015-02-23 13:33:37.309903 IP 173.180.XXX.YYY.43346 > 202.12.29.59.53: 32089 [1au] PTR? [COLOR=#ff0000]12.94.189.91.in-addr.arpa[/COLOR]. (54)
2015-02-23 13:33:37.357531 IP 199.249.120.1.53 > 173.180.XXX.YYY.14976: 61997- 0/7/7 (514)
2015-02-23 13:33:37.358183 IP 173.180.XXX.YYY.15821 > 149.20.64.3.53: 6390% [1au] A? sns-pb.isc.org. (43)
2015-02-23 13:33:37.358313 IP 173.180.XXX.YYY.2593 > 199.7.83.42.53: 57738% [1au] A? ns.isc.afilias-nst.info. (52)
2015-02-23 13:33:37.397205 IP 194.146.106.46.53 > 173.180.XXX.YYY.50988: 14549- 0/8/12 (593)
2015-02-23 13:33:37.397591 IP 173.180.XXX.YYY.49670 > 193.0.9.4.53: 59550% [1au] A? ns3.nic.fr. (39)
2015-02-23 13:33:37.413114 IP 149.20.64.3.53 > 173.180.XXX.YYY.15821: 6390*- 2/5/13 A 192.5.4.1, RRSIG (1472)
2015-02-23 13:33:37.461767 IP 192.48.79.30.53 > 173.180.XXX.YYY.41344: 14542- 0/10/13 (693)
2015-02-23 13:33:37.462182 IP 173.180.XXX.YYY.42027 > 202.12.29.59.53: 2063% [1au] A? ns4.apnic.com. (42)
2015-02-23 13:33:37.475741 IP 202.12.29.59.53 > 173.180.XXX.YYY.60116: 57227*- 2/0/1 A 202.12.29.59, RRSIG (228)
2015-02-23 13:33:37.479910 IP 202.12.29.59.53 > 173.180.XXX.YYY.51110: 49943*- 2/0/1 A 193.0.9.5, RRSIG (233)
2015-02-23 13:33:37.482381 IP 202.12.29.59.53 > 173.180.XXX.YYY.17647: 38592*- 2/0/1 A 202.12.28.140, RRSIG (228)
2015-02-23 13:33:37.536102 IP 202.12.29.59.53 > 173.180.XXX.YYY.43346: 32089- 0/5/1 (340)
2015-02-23 13:33:37.536421 IP 173.180.XXX.YYY.16667 > 91.189.95.3.53: 4081 [1au] PTR? 12.94.189.91.in-addr.arpa. (54)
2015-02-23 13:33:37.545541 IP 199.7.83.42.53 > 173.180.XXX.YYY.2593: 57738- 0/9/13 (686)
2015-02-23 13:33:37.545967 IP 173.180.XXX.YYY.23164 > 199.254.49.1.53: 55571% [1au] A? ns.isc.afilias-nst.info. (52)
2015-02-23 13:33:37.556509 IP 193.0.9.4.53 > 173.180.XXX.YYY.49670: 59550*- 2/7/21 A 192.134.0.49, RRSIG (1472)
2015-02-23 13:33:37.656907 IP 199.254.49.1.53 > 173.180.XXX.YYY.23164: 55571- 0/6/9 (542)
2015-02-23 13:33:37.657282 IP 173.180.XXX.YYY.31591 > 65.22.6.1.53: 30987% [1au] A? ns.isc.afilias-nst.info. (52)
2015-02-23 13:33:37.689348 IP 202.12.29.59.53 > 173.180.XXX.YYY.42027: 2063*- 2/0/1 A 202.12.31.140, RRSIG (227)
2015-02-23 13:33:37.718418 IP 91.189.95.3.53 > 173.180.XXX.YYY.16667: 4081*- 1/3/4 [COLOR=#ff0000]PTR feijoa.canonical.com[/COLOR]. (190)
2015-02-23 13:33:37.768723 IP 65.22.6.1.53 > 173.180.XXX.YYY.31591: 30987*- 1/4/9 A 199.254.63.254 (316)
```

---

