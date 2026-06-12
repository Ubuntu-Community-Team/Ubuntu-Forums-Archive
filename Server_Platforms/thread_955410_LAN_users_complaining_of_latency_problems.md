---
title: "LAN users complaining of latency problems"
date: 2008-10-22
forum: Server Platforms
---

### Post by Aeros84 on 2008-10-22
Hi guys,

Some users on the LAN (Windows XP machines) behind the Ubuntu server/gateway/router/proxy here complains of latency issues and general lag issues. Some of the complains are that browsing has its "ups and downs" (to quote), sometimes being normal speed and at other times being slow as hell.

Another complaint is that latency-dependant services are experiencing spikes. One of our residential users even complained that he's getting latency spikes in World of Warcraft (the LAN covers the office as well as apartments above it). He explained that he usually had an average latency of 250, where it now occasionally spikes up to 3000 for a couple of minutes, before going back down to 250 again.

This seems to coincide with the setting up of the Ubuntu server on the network. At the moment, all the LAN users plug into a D-Link 24-port hub, which in turn uplinks to the Ubuntu server, which in turn is connected (on a seperate ethernet interface) to the ADSL router. I suppose the problem could lie with the hub (it's 100mbps but half-duplex), but still.. that big a difference?

So something must be going on on the server itself then. I've checked, and it's memory usage is absolutely fine. Squid runs without any problems (the server automatically forwards all incoming port 80 connections through squid first via iptables, the rest is forwarded directly to the WAN interface, thus, acting as a router/gateway).

Is there any way I can check where the bottleneck lies? I can't connect everyone directly to the ADSL router, for obvious reasons - so that, as a test, isn't possible. Any other ideas?

---

### Post by jonabyte on 2008-10-22
since you mention that the network serves apartments, I would check into those users and see what they are doing with the network/internet.
also, are you actually using a hub or switch, switches will increase speeds over hubs.
finally, check what services are running on the server since you think it may be related to the install of it.

---

### Post by Robstarusa on 2008-10-22
My first guess is that the residential users are sucking bandwidth with torrents or other crap.

Cap them (or setup QoS) and I think you will be OK.

---

### Post by mschutte on 2008-10-22
You mention that you run squid. Have you had a look at the squid logs? It might be worth a looksee. Secondly you mention that the server is a gateway, a proxy and a router. I obviously do not know the layout, but are you routing just to the ADSL link or are you doing any other routing between different subnets?

It might be worth the touble to set up a seperate router if a lot of subnets are involved.

---

### Post by Aeros84 on 2008-10-22
Thanks for the replies so far, guys!

No, not routing to any other subnets, just routing between eth1 (LAN) and eth0 (WAN/ADSL). And, as mentioned, forwarding port 80 traffic to port 3128 for it to go through the (transparent) squid cache-proxy. Squid's logs don't display any apparent anomalies, so I reckon squid itself is okay.

I checked, when the WoW-player complained, only his computer and one of the workstations down in the office was connected. The workstation did nothing (was suspended), and he said that he didn't run anything other than WoW. Now obviously, I'll have to take him at his word for it, but he IS the database administrator, so he probably won't lie while trying to resolve his bandwidth issues :P

The problem MAY have been with the half-duplex Hub though. I replaced it with a full-duplex switch this evening, and asked everyone to test during the night (for the residential users) and during the day tomorrow (for the office users) and report back. So will let you guys know tomorrow afternoon.

Thanks again,

---

### Post by Robstarusa on 2008-10-22
PLEASE use a switch.  This may well resolve it.

I've also "killed" (until hard power reset) cheap switches with heavy nfs, smb, etc...

---

### Post by Aeros84 on 2008-10-22
While I'm waiting for the reports tomorrow, there's one thing I've noticed that I'm a little bit confused about:

The Ubuntu server's got 1GB of RAM. At the moment it reports around 820MB of this as free (buffers/cache calculation included, without those calculations it only reports about 50MB as free), but it still uses about 14MB of swap space. Is this normal? I thought swap space is only used when the RAM is close to being filled completely.

This is what my "free" command says:

```
             total       used       free     shared    buffers     cached
Mem:       1035524     984556      50968          0     260300     517920
-/+ buffers/cache:     206336     829188
Swap:      2000084      13332    1986752

```

So why is the swap space being used at all?

---

### Post by Aeros84 on 2008-10-23
(The users reported no real improvement in latencies after the switch has been installed. So must be something on the Ubuntu server itself then?)

---

### Post by tunggul on 2008-10-23
Is this lagging problem happens only after you use ubuntu machine as router/proxy gateway?
 Observe the traffic (with iptraf, or tcpdump) when your user experience lag, also check the throughput usage (w/ ifstat or some other tools capable showing current/realtime throughput usage). Check whether there're other traffic activity high enough beside the WoW traffic.

---

### Post by Aeros84 on 2008-10-24
These problems persist even if I bypass the Ubuntu server completely and just plug the switch straight into the ADSL router (and obviously, set the ADSL router to have the same IP that the Ubuntu server had).

I did check the traffic activity during these "lag spikes", and everytime the traffic seemed fine. Just as much bandwidth used as needed, and nothing else interfering with the WoW traffic (or browsing traffic).

Which led me to suspect that maybe it's not a connectivity-related problem, but maybe a software problem on the Ubuntu server? Something "getting stuck" as they said in the 90's? :P

---

### Post by Kolipoki on 2008-10-24
> **Aeros84 said:**
> 
...
Another complaint is that latency-dependant services are experiencing spikes. One of our residential users even complained that he's getting latency spikes in World of Warcraft (the LAN covers the office as well as apartments above it). He explained that he usually had an average latency of 250, where it now occasionally spikes up to 3000 for a couple of minutes, before going back down to 250 again.
...


Well, about all the symptoms in general I can't say much, but about the WOW issue, I can say, the game alone has been having serious latency issues after the last patch release (3.0.2). At the moment, this is a well known issue in the playing community. The spikes are insanely large (you can be d/ced and uncapable of logging in again for 10-15 minutes, several times a day), compared to what WOW has had the players used to, meaning a former overall good connectivity before that patch. 

This has been the worst scenario I've encountered in WOW since I started the game, over 1 year ago. Nonetheless Blizzard have been working on it, and some servers are reporting an acceptable improvement, specially in the current week.

Well, that was only regarding the game... *winks

---

### Post by Aeros84 on 2008-10-24
Heheh, I play WoW myself, but from home, where none of this is an issue. The thing is though, my latencies at home are fine. I use the same ISP for my ADSL at home than the office uses. Granted, sometimes the servers are wonky - but in general my latency is about 350 (the joys of living in South Africa, sigh), whereas this guy complains of latencies ranging from 700 to 3000.

---

### Post by Aeros84 on 2008-10-26
Anyone have any answer on the swap space usage at least?

---

### Post by steve_d on 2008-10-26
> **Aeros84 said:**
> These problems persist even if I bypass the Ubuntu server completely and just plug the switch straight into the ADSL router (and obviously, set the ADSL router to have the same IP that the Ubuntu server had).

You already have your answer, the problem is not with the server, but with some other bottleneck along the line. If you've removed the server from the equation and still have the same results, it can't be the server.

As others have suggested I would think it has more to do with the WOW servers. If your adsl connection is pinging at 350 at home, and hes getting near the same at work you've verified there is a WOW server latency problem.

What kind of latency do you get from other servers? Like [www.google.com](www.google.com) or a large SA server.

I would like to hear what latency your adsl connection is normally getting. Here in Canada I'd drop a provider that had any more than a 50ms ping, so it would be interesting to hear the averages from SA.

EDIT: as far as the swap goes, I wouldn't be too concerned about it. I can't give you the technical reason why the swap would be used, but at home I have 2GB of ram and any network transfers across my lan tend to use up a bit of the swap even when I'm using ~350/2000MB ram

-Steve

---

### Post by Aeros84 on 2008-10-26
> **steve_d said:**
> You already have your answer, the problem is not with the server, but with some other bottleneck along the line. If you've removed the server from the equation and still have the same results, it can't be the server.


Ah sorry, I meant to say "These problems desist if I...". Mixed up my words there. I have to admit, however, replacing the hub with a switch did improve things a little bit at least.

I think a better solution in the long run would be some traffic shaping, to limit each IP to a certain bandwidth rate (like 20kbps, for example). Not really sure how to implement it though, but will do some research.

As for the latency question, Steve: To local servers I get an average ping of about 30. But international is 250+, usually an average of 300. This isn't the ISP's fault, but rather our telecomms operator, which in all its wisdom shapes everything except FTP and HTTP. No way to bypass it, apart from going to another telecomms operator (and there is only one other operator, still in its starting phases now).

---

