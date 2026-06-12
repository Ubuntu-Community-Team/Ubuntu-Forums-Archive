---
title: "Free &amp; secure DNS service review"
date: 2010-08-12
forum: Security
---

### Post by wacky_sung on 2010-08-12
I have browsed through the net search for a free fast and secure dns service.Below is my conclusion.

Test carried out : [GRC DNS Nameserver Spoofability Test]("https://www.grc.com/dns/dns.htm")
Alternative Test : [DNS - OARC]("https://www.dns-oarc.net/oarc/services/dnsentropy")
Method of using each DNS : Input the ip address into router

**_[Google Public DNS]("http://code.google.com/speed/public-dns/")_**
Review : This is fastest & least secure dns available.

_**[Comodo Secure DNS]("http://www.comodo.com/secure-dns/")**_
Review : Moderate speed and security.
       : Unable to block malicious website.

**_[Norton DNS]("http://www.nortondns.com/")_**
Review : Moderate speed and security.
       : Able to block some malicious website.

**_[Sunbelt ClearCloud DNS]("http://clearclouddns.com/")_**
Review : Moderate speed and best security.
       : Reliability is reasonable and availability is acceptable    
         due to it has down for maintenance several times. 

**_[OpenDNS]("http://www.opendns.com/")_**
Review : Moderate speed and security.
       : Good filter of site and phishtank incorporated if you 
         sign up.
       : Require to use additional software if you are on dynamic 
         ip.

**_Short Youtube review done by a guy using window OS_**
[http://www.youtube.com/watch?v=5846w2a4oio](http://www.youtube.com/watch?v=5846w2a4oio)

What do you think is the best dns for you?The reason why i choose to use an external dns service is because my ISP DNS service having inconsistent speed during the peak hourof usage.

---

### Post by wacky_sung on 2010-08-13
Ah,hard to believe nobody actually use 3rd party dns service.Probably you guys only trust your ISP.:D

---

### Post by Lovett1991 on 2012-05-08
I run ubuntu as my router.

I have
internet -> modem -> ubuntu(Hyper-v VM) -> Server 2008R2 hyper-v network -> network

I run bind9 on the ubuntu machine itself although I'm not sure where this then obtains its dns requests. The dhcp server tells the network it can either get dns from the router or 8.8.8.8

For google; The most common sites (facebook, google) are normally very quick as history & cache. However if I try to access random websites, its not that impressive. I can't say I've tried any other DNS servers.

If you know a way of determining where bind9 sends its requests to I'd really like to know. I want to know as, like you, I don't want to use my ISP's DNS servers.

---

### Post by Soul-Sing on 2012-05-09
1) - 87.118.109.2 (Swiss Privacy Foundation)
2) - 87.118.104.203 (Swiss Privacy Foundation)
3) - 87.118.100.175 (German Privacy Foundation e.V.)
4) - 213.73.91.35 (Chaos Computer Club Berlin)

out of europe? don't use them.

---

