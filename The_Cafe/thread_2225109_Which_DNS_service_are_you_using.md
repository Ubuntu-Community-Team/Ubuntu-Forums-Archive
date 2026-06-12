---
title: "Which DNS service are you using ?"
date: 2014-05-19
forum: The Cafe
---

### Post by linuxyogi on 2014-05-19
Hi,

I am using [Google DNS]("https://developers.google.com/speed/public-dns/") atm but some times I use openDNS also. In the past I have tried the 4.2.2.1 ranges and UltraDNS.

So do you prefer your ISP's DNS ? If not which one do you use ?

---

### Post by pretty_whistle on 2014-05-19
Interesting.  I didn't know Google had that.

I'm using my ISPs DNS.  In the past I used openDNS on a Windows machine but decided to stop because a few times it couldn't find some web addresses.

---

### Post by sammiev on 2014-05-19
For local stuff my providers ISP is much faster and over all they seem to be as fast as GoogleDNS/OpenDNS.

---

### Post by pqwoerituytrueiwoq on 2014-05-20
4.2.2.[2-6] are supposed to be really fast (faster than google)
i am using google's combined with DNSMasq caching

---

### Post by The Spectre on 2014-05-20
I would recommend running a DNS Benchmark to see which DNS Service would be the best for you...

[https://code.google.com/p/namebench/](https://code.google.com/p/namebench/)

[IMG]http://baudlabs.com/wp-content/uploads/namebench_screenshot2.png[/IMG]

---

### Post by pqwoerituytrueiwoq on 2014-05-20
speaking of benchmarks, ever wonder how much faster caching makes DNS lookups?
[ATTACH]253311[/ATTACH]

---

### Post by Habitual on 2014-05-20
```
host 8.8.8.8
8.8.8.8.in-addr.arpa domain name pointer google-public-dns-a.google.com.
host 4.2.2.2
2.2.2.4.in-addr.arpa domain name pointer b.resolvers.Level3.net.
```

---

### Post by estamets on 2014-05-20
Unblock Us. 

The reason being, I can watch blacked out NBC Sports coverage of the Hockey playoffs online.

---

### Post by CharlesA on 2014-05-20
I use some DNS servers from here:

[http://opennicproject.org/](http://opennicproject.org/)

I got sick of my ISP hijacking search results and directing me to pages filled with ads.

---

### Post by vasa1 on 2014-05-21
My ISP's. No problems that I know of.

---

### Post by linuxyogi on 2014-05-21
> **CharlesA said:**
> I use some DNS servers from here:

[http://opennicproject.org/](http://opennicproject.org/)

I got sick of my ISP hijacking search results and directing me to pages filled with ads.

After reading that they respect privacy. I just switched. I sometimes use Tor. I guess this change will enhance my anonymity. :grin:

> **vasa1 said:**
> My ISP's. No problems that I know of.

I am using a government owned ISP. Not only their DNS but the entire service is a peice of s***. I am leaving this DSL including the phone too. I will be Airtel mobile broadband from the beginning of next month.

---

### Post by vasa1 on 2014-05-21
> **linuxyogi said:**
> ...
I am using a government owned ISP. Not only their DNS but the entire service is a peice of s***. I am leaving this DSL including the phone too. I will be Airtel mobile broadband from the beginning of next month.
When I was on BSNL ADSL I had changed to Google's but now my connection is via cable broadband: unlimited scheme but not that fast ... that's too costly but I'm okay with what I have (Rs. 2697 for six months). To keep my Android updated, I use WiFi.

---

### Post by LastDino on 2014-05-21
I live in Greater Bombay too and I use local ISP, he has no real problems like the big names in internet industry here. It costs me and my buddies 3k/year plus initial charges of router since  we are sharing single connection. It is not fast but it is unlimited and there are no hijacking from ISP as far as I know. Before this I used to use Hathway, and while connectivity was good, it was costing too much .-.

---

### Post by vasa1 on 2014-05-21
> **LastDino said:**
> .. no hijacking from ISP as far as I know. ...
Same here.

---

### Post by linuxyogi on 2014-05-21
I have become a big fan of Hathway even when they dont operate in Kolkata. I mean you have to agree they introduced 50 Mbps speeds to India. ATM 50Mbps is available in Bombay and Bangalore only.

[This plan ]("http://www.hathway.com/Broadband/broadband_home.aspx")is not that costly.  50Mbps Rs 1799 for 3 Months

---

### Post by The Spectre on 2014-05-21
OpenDNS is a popular DNS service worth checking out...
[http://www.opendns.com/](http://www.opendns.com/)

When I ran the namebench DNS Benchmark last year OpenDNS scored the best for me followed Google Public DNS.

---

### Post by HiImTye on 2014-05-21
I use the 4 OpenDNS servers and then the 2 GoogleDNS servers

---

### Post by linuxyogi on 2014-05-21
> **HiImTye said:**
> I use the 4 OpenDNS servers and then the 2 GoogleDNS servers

I didnt know openDNS maintains 4 servers. I thought they offer only two

 

[LIST]
[*]208.67.222.222 
[*]208.67.220.220 
[/LIST]

What are the addresses of the other 2 ?

---

### Post by HiImTye on 2014-05-21
> **linuxyogi said:**
> I didnt know openDNS maintains 4 servers. I thought they offer only two

 

[LIST]
[*]208.67.222.222 
[*]208.67.220.220 
[/LIST]

What are the addresses of the other 2 ?

```
[ tye@t: ~ ]$ cat /etc/resolv.conf | grep -v '^#'
nameserver 208.67.220.222
nameserver 208.67.222.220
nameserver 208.67.220.220
nameserver 208.67.222.222
nameserver 8.8.4.4
nameserver 8.8.8.8
nameserver 2620:0:ccc::2
nameserver 2620:0:ccd::2
```
the last 2 are OpenDNS's IPv6 servers

---

### Post by linuxyogi on 2014-05-25
Anyone using [DNSCrypt ? ]("http://dnscrypt.org/")

Please help me with the installation and configuration.

---

### Post by Niets on 2014-06-13
> **The Spectre said:**
> OpenDNS is a popular DNS service worth checking out...
[http://www.opendns.com/](http://www.opendns.com/)

When I ran the namebench DNS Benchmark last year OpenDNS scored the best for me followed Google Public DNS.


+1

---

### Post by quantal on 2014-06-13
My ISP, what are the differences and what makes people change dns? apart from censorship reasons

---

### Post by linuxyogi on 2014-06-14
> **quantal said:**
> My ISP, what are the differences and what makes people change dns? apart from censorship reasons

Some ISPs provide slow DNS in comparison to others. 

You can test which DNS is best for you using namebench.

```
sudo apt-get install namebench
```

Choosing a faster DNS will only make the forward lookup faster and therefore page loading but it wont increase your download speed.

---

### Post by black veils on 2014-06-14
i use Comodo Secure DNS, i've had no problems with it, and have been using for a year or more.

[http://www.comodo.com/secure-dns/](http://www.comodo.com/secure-dns/)

---

### Post by quantal on 2014-06-15
Thank you for replying
I will try different dns's

---

### Post by quantal on 2014-06-15
Ok, my isp's dns is the fastest for me, but in the notes in namebench it says that google appears hijacked and both google and twitter appear incorrect

---

### Post by linuxyogi on 2014-06-16
> **quantal said:**
> Ok, my isp's dns is the fastest for me, but in the notes in namebench it says that google appears hijacked and both google and twitter appear incorrect

I am also curious about what "hijacked" means here.

I have used namebench only once and I remember that when the test finishes namebench suggests 3 DNS servers, starting from the fastest.

Just use those servers in the same order as suggested by namebench.

---

### Post by LastDino on 2014-06-16
> **linuxyogi said:**
> I am also curious about what "hijacked" means here.

I have used namebench only once and I remember that when the test finishes namebench suggests 3 DNS servers, starting from the fastest.

Just use those servers in the same order as suggested by namebench.

Out of curiosity, how do you achieve this? I've only used commodo secure DNS as well, which is as easy as putting tick mark in front of that box while installing, but that was in my windows days.

---

### Post by linuxyogi on 2014-06-16
> **LastDino said:**
> Out of curiosity, how do you achieve this? I've only used commodo secure DNS as well, which is as easy as putting tick mark in front of that box while installing, but that was in my windows days.

Right click on Network Manager > Edit Connections > Select interface (Wired in my case) > Click Edit > IPv4 Settings >

Automatic (DHCP) address only > Enter DNS servers (max 3) like this

8.8.8.8, 8.8.4.4, 4.2.2.1

Note : After each comma there is a space.

---

### Post by linuxyogi on 2014-06-16
> **quantal said:**
> Ok, my isp's dns is the fastest for me, but in the notes in namebench it says that google appears hijacked and both google and twitter appear incorrect

[Source]("https://code.google.com/p/namebench/wiki/FAQ#What_does_%22NXDOMAIN_hijacking%22_mean?")

What does "NXDOMAIN hijacking" mean?

It means that the DNS  server falsifies the result when a non-existent host is requested. This  is usually used so that the DNS provider can place advertising when you  make a typo when typing in a URL.  

What does "Incorrect result for..." mean?


This  means that the DNS server may be falsifying the result for a well known  service, and redirecting you to another website. This is usually a very  bad thing. This alert may also result in false positives when a website  changes to a new network or CNAME.

---

### Post by quantal on 2014-06-16
> **linuxyogi said:**
> [Source]("https://code.google.com/p/namebench/wiki/FAQ#What_does_%22NXDOMAIN_hijacking%22_mean?")

What does "NXDOMAIN hijacking" mean?

It means that the DNS  server falsifies the result when a non-existent host is requested. This  is usually used so that the DNS provider can place advertising when you  make a typo when typing in a URL.  

What does "Incorrect result for..." mean?


This  means that the DNS server may be falsifying the result for a well known  service, and redirecting you to another website. This is usually a very  bad thing. This alert may also result in false positives when a website  changes to a new network or CNAME.

It seems that I have no alternative because in the log after I run namebench it says that all dns servers are hijacking google and both twitter and google appear incorrect. This happens in my ISP's dns, cogent dns (66.28.0.45), other isps of my country dns, google public dns (8.8.8.8), open dns dns (208.67.222.222), ultradns dns (156.154.70.1). All of them hijack google and twitter and google appear incorrect. I don't know what to do

---

### Post by linuxyogi on 2014-06-16
> **quantal said:**
> It seems that I have no alternative because in the log after I run namebench it says that all dns servers are hijacking google and both twitter and google appear incorrect. This happens in my ISP's dns, cogent dns (66.28.0.45), other isps of my country dns, google public dns (8.8.8.8), open dns dns (208.67.222.222), ultradns dns (156.154.70.1). All of them hijack google and twitter and google appear incorrect. I don't know what to do

IMO that hijacking part is not that important.

Namebench shows "incorrect" when the ip of say Google doesn't match with the ip which is in namebench's database.

But since "incorrect" is showing up using so many DNS servers these are most probably false positives. In other words Twitter and Google have changed their IP addresses.

---

### Post by linuxyogi on 2014-06-16
@[**[COLOR=#000000]quantal[/COLOR]**]("http://ubuntuforums.org/member.php?u=1808322") 

This may help you relax ... [https://www.grc.com/dns/dns.htm](https://www.grc.com/dns/dns.htm)

---

### Post by LastDino on 2014-06-16
Hmm fastest I get is 127.0.1.1

Because I'm using router?

---

### Post by linuxyogi on 2014-06-16
> **LastDino said:**
> Hmm fastest I get is 127.0.1.1

Because I'm using router?

If thats the ip of your router then yes coz your router is configured to use your ISP's DNS which is nearest to you.

I never used a router for cable broadband so the address 127.0.1.1 is new to me.

---

### Post by LastDino on 2014-06-16
Yes, and it is not even the main router. :P

You see, we are sharing single connection into multiple houses. 

I read few comments on that namebench site, and it looks like for configuration like mine it is best to stick with default.Tsk tsk

---

