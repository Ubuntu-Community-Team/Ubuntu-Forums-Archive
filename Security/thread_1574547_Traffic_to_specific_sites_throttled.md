---
title: "Traffic to specific sites throttled?"
date: 2010-09-14
forum: Security
---

### Post by spynappels on 2010-09-14
Hi guys,

I want to check if traffic to a specific URL is being throttled by a hospital acting as an ISP.

A client is having great trouble accessing a hosted web-app from inside the hospital, but access is fine from outside.

The hospital IT dept are not interested as the rest of the Internet is fine.

I need to trace where the latency is creeping in or where the throttling is happening, if I can do that, the hospital will remove it.

Traffic is standard http to a specific URL.

Any ideas?

---

### Post by endotherm on 2010-09-14
well if you think the issue is with throttleing to specific URLs, try configuring a proxy server. unless the proxy is on the throttling list, the problem should go away, if it is in fact being specifically throttled based on destination. 
my guess is that the network at the hospital is just overworked, undermaintained, and scaled well beyond it's capacity. hospitals don't spend a ton on switch meshes and well provisioned wans, when "the machine that goes ping" costs 8.6 million dollars.

---

### Post by perspectoff on 2010-09-14
> **spynappels said:**
> Hi guys,

I want to check if traffic to a specific URL is being throttled by a hospital acting as an ISP.

A client is having great trouble accessing a hosted web-app from inside the hospital, but access is fine from outside.

The hospital IT dept are not interested as the rest of the Internet is fine.

I need to trace where the latency is creeping in or where the throttling is happening, if I can do that, the hospital will remove it.

Traffic is standard http to a specific URL.

Any ideas?

Very common, and in fact throttling is recommended for all hospitals. I assume you are a patient using the hospital's Internet access.

I have worked as a hospital IT consultant and absolutely recommend every hospital to throttle usage (streaming, downloading, etc.), to filter many, many websites, and to use a host of network monitoring, and a wide range of other security precautions.

Nurse, employees, and patients tend to try to do all sorts of illegal or dangerous things on hospital computers (or any publicly available internet access).

Presumably you are not trying to do something similar?

On the flip side, some hospitals new to IT have overly strict filters, so that even legitimate medical sites get filtered (after all, the majority of the American public can't even discuss normal human anatomy and many medical issues properly). Those filters require a lot of tweaking, but it is better for a hospital (or other public venue) to err on the side of aggressive filters initially, loosening the filters slowly.

I have seen many hospitals (especially smaller ones) crippled by viruses and trojans for 1 day to 2 weeks for failing to implement proper filtering and security.

Further, and more commonly, I have seen hospitals internal Internet slow to a crawl when nurses, patients, or employees stream videos over their lunch break, or something.

BTW, this isn't a problem unique to hospitals. Many public ISPs, such as Comcast, do the same thing. 90% of bandwidth is monopolized by 5% of users, since large file trading is actually only done by a small percentage of Internet users.

In the days of Netflix and other online streaming, this is problematic for public ISPs, and I have switched ISPs (including Comcast) twice because they throttled so aggressively that I couldn't stream Netflix on them (which for Comcast was probably the whole idea).

But hospitals, with limited bandwidth to begin width, have to be even more aggressive with throttling, just to make sure their own internal systems run smoothly.

---

### Post by spynappels on 2010-09-14
Ok, I think I need to elaborate a little.

This is a private hospital, and I work for an Electronic Medical Record system vendor, supporting a web based EMR system. This system normally runs on a server based in a healthcare provider's suite of offices, but for a variety of reasons one particular provider needs his system hosted off-site, and connects to it through the supposedly unmetered and unfiltered broadband service provided to the suite of offices by the Private hospital.

Without unthrottled access to the web-app, the provider is finding it difficult to run clinics etc, and I have to find out why it is running so slowly inside the hospital infrastructure, but normally outside the hospital infrastructure.

So, no bit-torrents, no streaming etc, only legitimate http traffic to a required site.

I reckon it is probably a caching server like ISA which is limiting traffic from the URL in question, but I will need to find out definitively what is causing it before I can go back to the hospital and ask them to release a throttle which they are not admitting is there.

---

### Post by BkkBonanza on 2010-09-14
What tests have you already been able to do? 
Has traceroute provided anything useful? Or is ICMP blocked.
You might try -T option on traceroute to see if TCP packets can be traced.
Is access to other sites behaving similar, all or just some sites?
Can you test using a different port than 80 to see if filtering is port based?

SSH could be used to run a brief proxy test and see how traffic behaves when bounced off other servers, or using different ports/pathways. There is a lot of flexibilty in testing with ssh.

Are you able to use nmap to do some network mapping, or will this be too intrusive?

These are just questions that come to mind that may help shed light on the problem.

---

### Post by uRock on 2010-09-15
> **BkkBonaza said:**
> Are you able to use nmap to do some network mapping, or will this be too intrusive?
If they have a decent NIDS, then is it possible that his/her MAC might be blocked as a result of running a scan?

---

### Post by BkkBonanza on 2010-09-15
Anything is possible... it's easy to try a different MAC just in case it is an intentional block, and may be worth testing as a diagnostic.

---

### Post by perspectoff on 2010-09-15
> **spynappels said:**
> Ok, I think I need to elaborate a little.

This is a private hospital, and I work for an Electronic Medical Record system vendor, supporting a web based EMR system. This system normally runs on a server based in a healthcare provider's suite of offices, but for a variety of reasons one particular provider needs his system hosted off-site, and connects to it through the supposedly unmetered and unfiltered broadband service provided to the suite of offices by the Private hospital.

Without unthrottled access to the web-app, the provider is finding it difficult to run clinics etc, and I have to find out why it is running so slowly inside the hospital infrastructure, but normally outside the hospital infrastructure.

So, no bit-torrents, no streaming etc, only legitimate http traffic to a required site.

I reckon it is probably a caching server like ISA which is limiting traffic from the URL in question, but I will need to find out definitively what is causing it before I can go back to the hospital and ask them to release a throttle which they are not admitting is there.

Heh heh. Very common problem with web-based EMRs. Web based EMRs are pitched to rural hospitals which often have intermittent broadband throughput as it is. You definitely need a full network monitoring system -- the slowdowns are everywhere, I guarantee. Start with the switch and the DNS resolution and proxy severs, which are obvious bottlenecks.

---

### Post by spynappels on 2010-09-15
That is fair enough, except that this hospital is not rural, it is in a city centre and has (supposedly) state of the art connectivity.

I think their proxy servers are the place to start as the DNS shouldn't be an issue, the problem is getting them to look at their systems as being the issue. I don't have access to their infrastructure and a tracert ends at the default gateway for that suite's VLAN, and pings don't get through either.

I may have to show them that the system works faster if accessed through a 3G dongle than through the suite's internet connection.

The IT dept is understaffed though and is never interested if it means more work for them. Look like a fun day ahead.

---

### Post by endotherm on 2010-09-15
well, video is very convincing. I deployed a web app to some users with aircards in rural areas a few years ago, and when questions came up about the speed, I recorded a desktop session of myself using the app as fast as I could (it performed admirably) to present to management. after that, the supposed panacea that was aircards lost a bit of it's luster.

---

