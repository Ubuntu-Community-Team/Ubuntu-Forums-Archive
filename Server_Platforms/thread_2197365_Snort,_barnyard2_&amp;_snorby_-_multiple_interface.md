---
title: "Snort, barnyard2 &amp; snorby - multiple interface configuration"
date: 2014-01-03
forum: Server Platforms
---

### Post by paul68 on 2014-01-03
Hi,

Ii've installed snort, barnyard2 and snorby on Ubuntu Server 13.04 monitoring my VPN connection (tun0) and default ethernet connection (p1p1). I've tested it by creating a rule to catch all tcp packets and then alert. Logging into snorby I can see the alerts logged. However, the exact number of alerts are logged for both the p1p1 and tun0 interfaces which leads me to think that the unified logs barnyard2 is reading from is not distinguishing between the two interfaces. 

I'm running two instances of barnyard2 and each is configured with a specific interface (config interface: tun0 and config interface: p1p1 in each conf). I've configured snort to use unified logging and where I think it may be failing is that snort is producing only one set of unified logs and either barnyard2 is not filtering correctly or the snort logs do not include the interface or other information needed to allow barnyard2 to filter.

I've seen from googling that a common solution is to pass a different log directory to snort when starting up but as Ubuntu's snort is configured with one snort.conf I don't see how this can be achieved without hacking the init.d script? 

Any ideas on what I can possibly try?

Thanks

---

