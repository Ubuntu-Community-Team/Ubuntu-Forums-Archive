---
title: "Internet providers and download speed"
date: 2015-01-21
forum: The Cafe
---

### Post by mikodo on 2015-01-21
I decided to change to a different and faster internet provider, yestersday. It is less expensive with no supposed bandwidth usage limitations. For fun, I downloaded an Ubuntu 14.10 64 bit .iso, from the main server and consistently only got about 975 Kbs speed. Then I tried with Transmission, and the speed was marginally faster with 60 peers connected, (about 1 Mps). Supposedly the service I purchased, provides 5Mbs download. I know it still rated quite low, but I don't stream video, so I haven't needed a faster one, but this is reputable provider, with less cost, that uses fibre optics. It's priciest home plan, offers 260 Mbs downloads ... well, so it says. They have a website, that one can check, the download speed, but one must give them an email address for this, and I don't want to do that with them. At least not yet!

Oh and, I don't use Wi-Fi. 

I called and was able to talk with a real IT person, (not a service rep). Response ... Oh! Linux ... It has to do with the site's servers you are downloading from ... your firewall ... your browser ... yada yada yada but, nothing to do with their service.

So people, what do you usually get for download speeds, when downloading Ubuntu .iso's?

---

### Post by TheFu on 2015-01-21
It depends on where the ISO is coming from and whether the remote server has bandwidth limits for downloads.
When getting large files, like a linux ISO, it is common for the distribution network to limit downloads to about 1Mbps.  

You might get better throughput if you get the ISO from a local university.

Another way to test is to get 2 or 3 or 4 ISO downloads from different source servers. If each of them limit to 1Mbps, then 3 should let you see 3x1Mbps or so.

Does **speedtest.net** require an email address? I didn't think it did. Try that for estimates. It is well known.

---

### Post by mastablasta on 2015-01-21
you can try speed test. you will see that the advertised speed is actually only to their servers. ;-)
sometimes you will get close to that speed on same continent or to close by countries. but the farther you go the slower the speed. also if you connect to island with low main cable bandwidth it will also be slow.

e.g. I have 20 Mbit/s up & down. and I get this in my country, also some neighbouring countries have very close to that. if I go to UK it get's a bit slower. it is even slower if I test with over Atlantic (e.g. USA) server.

---

### Post by ajgreeny on 2015-01-21
I am in the UK with a 38Mb/s plan using fibre broadband and my speeds are as shown in the attachment.  I regularly get those sort of d/l speeds when using transmission for .iso files, so this is not just some theoretical figure, but an actual speed for me.

Transmission is great; it is fast, simple, and it does exactly what it is supposed to do very well, in my experience.

---

### Post by mastablasta on 2015-01-21
I use CLI transmission controlled via web interface. if I load more than one torrent to download it knock off the connection. not sure why since the transfer speed is capped at 2mbit and also peers and such. quite interesting. 

oh I think I have 100Mbit/s down and 50 Mbit up until end of this month (promotional for 3 months). I am not sure I would be upgrading to that since I doubt it would make much of a difference in my everyday use. sure it was fun to download large files at such speed, but in my everyday use the current plan is more than enough. if they offered for same price or a really small increase only then maybe I would take it.

---

### Post by SeijiSensei on 2015-01-21
> **mastablasta said:**
> you can try speed test. you will see that the advertised speed is actually only to their servers. ;-)
I'm not sure what you're getting at.  I believe most of their servers are housed at ISP datacenters.  If you mean connections to other servers can be slower than the Speedtest results, well sure.  It's going to depend on the speed of connection at both ends, of course.

I have Verizon FiOS Quantum, which is a 50/50 service.  Speedtest.net just now reported speeds in the 60 Mbit range in both directions.  Downloading a DVD ISO from cdimage.ubuntu.com with Firefox pushed 7 Mbyte/sec, consistent with the figures from Speedtest.net.

---

### Post by TheFu on 2015-01-21
I know that GA-Tech throttles outside their campus to 1Mbps for their Linux software library and believe they are the fastest connection nearby.

---

### Post by AllenGG on 2015-01-21
Speedtest.net is a good indicator.  See worldwide speeds here>  [http://www.netindex.com/download/map](http://www.netindex.com/download/map)

From what I can see, there is very little consistency.  Japan wins with 70 mpbs download.
On my 20 mpbs , with 3 computers and 3 cel phones on, very little latency.  Not cheap.  Approx 80USD per month, includes unused landlline.
Allen

---

### Post by mikodo on 2015-01-21
Thanks everyone, including the adm/mod, that gave the thread a more appropriate title.> **TheFu said:**
> It depends on where the ISO is coming from and whether the remote server has bandwidth limits for downloads.
When getting large files, like a linux ISO, it is common for the distribution network to limit downloads to about 1Mbps.  

You might get better throughput if you get the ISO from a local university.

Another way to test is to get 2 or 3 or 4 ISO downloads from different source servers. If each of them limit to 1Mbps, then 3 should let you see 3x1Mbps or so.

Does **speedtest.net** require an email address? I didn't think it did. Try that for estimates. It is well known.

I tried speedtest.net, and with it connecting/testing it with 2 close by servers, the results, were ~8Mbs download, and ~2Mbs upload. This is higher than advertised with the plan.

So, I think that it does have to do with the source servers. A friend of mine used to use 4 different geo-servers, when torrenting. I don't know how to that, but I can learn if I want to. I am assuming this is not possible when downloading directly from an Ubuntu server that it uses, but I don't know.

Again, thanks for the education, everyone.

---

### Post by mastablasta on 2015-01-22
> **SeijiSensei said:**
> I'm not sure what you're getting at.  I believe most of their servers are housed at ISP datacenters.  If you mean connections to other servers can be slower than the Speedtest results, well sure.  It's going to depend on the speed of connection at both ends, of course.
.
exactly. but often people do not understand this. so here they would complain on ISP forums that while downloading something speed was not as advertised. well if they were downloading from US server of course they can not have the same speed as from a server inside the country, but many do not understand this.

---

### Post by leclerc65 on 2015-01-22
For a 'fresh' distro torrent is usually faster than direct download because the swarm is large.

---

### Post by Ko_Char on 2015-01-22
I get about 200-650 KB/sec for direct download from Ubuntu server (not mirror), and 1.2 MB/sec for torrent. 
I get about 300 KB/sec - 1.2 MB/sec for most websites. 
For Google & Microsoft, I sometimes get up to 1-4 MB/sec download speed.

---

### Post by linuxyogi on 2015-01-25
My original line speed is 512kbps but my ISP supports local peering and caching for torrents and some http sites. On peered torrents I get download speeds upto 10MB/s and in case of cached http sites I get 480kB/s.

---

### Post by shantiq on 2015-01-26
i too in UK used to have Virgin 50Mb connection     downgraded to 30Mb as was skint;     and now that i am not any longer see no reason to go back up to 50
a film down in 10 mns is fast enough; i am not quite that desperate! ::]]

faster than Speedtest.net i find and command line is this >>>>

```
[I]wget -O speedtest-cli https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py
[/I]c*hmod +x speedtest-cli*
./speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Virgin Media (82.20.25.138)...
Selecting best server based on latency...
Hosted by Virgin Media (Basildon) [129.16 km]: 30.682 ms
Testing download speed........................................
Download: 27.27 Mbits/s
Testing upload speed..................................................
Upload: 1.72 Mbits/s
```

---

