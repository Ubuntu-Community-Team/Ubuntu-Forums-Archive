---
title: "ATT and traceroute"
date: 2008-04-29
forum: Security
---

### Post by jmore9 on 2008-04-29
Hello!

Well here is a new one for me.  I have never seen a bunch of trace routes from ATT like this before :

Time:Apr 29 06:35:56 Direction: Unknown In:eth0 Out: Port:33439 Source:64.94.45.26 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Apr 29 06:36:02 Direction: Unknown In:eth0 Out: Port:33442 Source:64.94.45.30 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Apr 29 06:36:07 Direction: Unknown In:eth0 Out: Port:33436 Source:64.94.45.18 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Apr 29 06:36:12 Direction: Unknown In:eth0 Out: Port:33442 Source:64.94.45.30 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Apr 29 06:36:12 Direction: Unknown In:eth0 Out: Port:33436 Source:64.94.45.18 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Apr 29 06:36:17 Direction: Unknown In:eth0 Out: Port:33442 Source:64.94.45.30 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Apr 29 06:36:17 Direction: Unknown In:eth0 Out: Port:33436 Source:64.94.45.18 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Apr 29 06:36:20 Direction: Unknown In:eth0 Out: Port:27358 Source:121.210.32.165 Destination:71.205.135.55 Length:59 TOS:0x00 Protocol:UDP Service:Unknown
Time:Apr 29 06:36:22 Direction: Unknown In:eth0 Out: Port:33442 Source:64.94.45.30 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Apr 29 06:36:22 Direction: Unknown In:eth0 Out: Port:33436 Source:64.94.45.18 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Apr 29 06:36:27 Direction: Unknown In:eth0 Out: Port:33442 Source:64.94.45.30 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute
Time:Apr 29 06:36:27 Direction: Unknown In:eth0 Out: Port:33436 Source:64.94.45.18 Destination:71.205.135.55 Length:32 TOS:0x00 Protocol:UDP Service:Traceroute

I cannot figure out why that would be happening.  Earlier in the day someone or something was searching for windows files on the ubuntu box without getting past the firewall --  enbd-cstatd -- was the name.  I have been using ubuntu all night so no windows stuff here funny huh

---

### Post by Monicker on 2008-04-29
The ip addresses 64.94.45.30 and 64.94.45.18 belong to Internap; they are a backbone provider for the internet.  They may be experiencing some type of routing issue within their network.

---

### Post by jmore9 on 2008-04-29
Well that is just one little piece of my firewall log and my high speed internet slowd to a stop for about 15 minutes.  I tried asking comcast about this and guess what they told me to do to correct the problem ?  Power cycle my modem and reboot my computer.  If that did not fix my connection problems then my modem or my computer must be broken !!  This is from the comcast support people.  I guess they either did not read the stuff i posted in my email or they just did not know what to do , any way i know it is not my machine or the modem.  Kind of funny in a way

---

### Post by lemming465 on 2008-04-29
Last estimate I saw suggested that the internet traffic was runnig about 2% spam, 5% ddos, and I'd guess 30% copyright violations (minimum).  You may have run into some of the 5%.

---

### Post by jmore9 on 2008-04-29
Well i know that the firestarter works pretty good because all that happened was the internet slowed down and stopped nothing got inside. Which seems to me to speak pretty good of linux as a whole.

---

