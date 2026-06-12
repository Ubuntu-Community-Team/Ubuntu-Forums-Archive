---
title: "How is chkrootkit Rootkit Hunter Installed"
date: 2005-09-06
forum: Server Platforms
---

### Post by John.Michael.Kane on 2005-09-06
How is chkrootkit Rootkit Hunter Installed? 
What comands are used or needed to run them?
Can they be run automaticly? if so how? 

Also what kinds of wireless  routers do you all use? as im looking to get one? i know that some here use two routers so could one use say a Watchguard WG2500 Firewall conected to NETGEAR WGT624 or WRT54G.

Thanks

---

### Post by KingBahamut on 2005-09-06
apt-get install chkrootkit 

I believe. 

You probably set it as a cron job with an output file or something,to be examined later. 

I own the WRT54g , with accomanying APs that act as repeaters around my house. Not disappointed with that model in the slightest.

---

### Post by John.Michael.Kane on 2005-09-06
well it's installed. how can i use it to scan the machine?
Thanks

---

### Post by KingBahamut on 2005-09-06
chkrootkit 

hit enter 

[http://www.chkrootkit.org/](http://www.chkrootkit.org/) for more information. 

Alternately you could choose to do random scans with utils like nmap, tcpdump, iptraf, and etherape....as a way to determine traffic status on your network. 

Be sure however, that the machine your using these on has promiscuous mode enabled. 

Done via 

sudo ifconfig eth0 promisc

---

### Post by John.Michael.Kane on 2005-09-06
KingBahamut thanks for your help..

---

### Post by KingBahamut on 2005-09-06
Surely Snake, just do me a favor.....if they ask you to save the president because hes stuck in a prison in new york, dont do it. 

=)

---

### Post by John.Michael.Kane on 2005-09-06
You bet. Thanks angain for the help and advice..

one more question being that ubntu is based on debian the books that are publish for it the info in them holds true for this os as well?

---

