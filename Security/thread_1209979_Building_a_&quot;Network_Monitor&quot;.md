---
title: "Building a &quot;Network Monitor&quot;"
date: 2009-07-10
forum: Security
---

### Post by Piro24 on 2009-07-10
Theres a long, lengthy story behind this, but I'll spare the boring details. Basically, what I'm looking to do is convert one of the oldest, relatively useless PC's we own into a Linux Box that would monitor our Wlan, extensively log it, and report on suspicious activity on all machines.

I'm probably not going to be using Ubuntu on this, most likely a really lightweight distro, I'm looking at Arch currently. However, I'd like some tips as for what programs to use. I have a few in mind, but would like your input and suggestions out of the blue. Thanks!

```

1: Program to log all network traffic. For example
#192.168.2.3 outgoing request to *IP Address** Port:67845 Service: Utorrent

2: Program to prevent ARP Spoofing, and especially password sniffing.

3: Program to detect suspicious network activity and possibly log it.

4: Anything else you can think of.

```

Please keep in mind this computer is there to log and monitor. Not to anonymize traffic or block connections, however, any network security tools (that do not really effect speed) that you can recommend will be useful. 

Thanks guys.

---

### Post by andrewc6l on 2009-07-12
You might want to look into Argus - Audit Record Generation and Utilization System. [http://www.qosient.com/argus/](http://www.qosient.com/argus/)

---

### Post by 22x on 2009-07-12
Arp spoofing, is that not when someone has got into your router and redirected everything you do online to just about any place they want it to go ? some people write code to your router and do man in the middle attacks these can be dangerous.

---

### Post by wirelessmonkey on 2009-07-12
snort + nagios + cacti + wireshark

---

