---
title: "Port Scan Bypassing Router??"
date: 2011-03-25
forum: Security
---

### Post by themanfromdelmonte on 2011-03-25
This is the typical log extract from firestarter.

I'vehad a number of tcp probes to select ports a number of times in a very short time. I had to restart my modem and router with new mac/ip to stop it happening. 

[I know its just a sacn and it was blocked but how did it get passed my router with SPI and no port forwarding, DMZ etc??. When i test it with nmap from another computer every port is hidden and its not known if host is up.
Also any idea what they were looking for on those ports?

---

### Post by CharlesA on 2011-03-25
Logs can make you paranoid. If a packet was dropped, it was dropped. 

If the packets aren't being dropped, just block that IP.

---

### Post by bodhi.zazen on 2011-03-25
You will need to capture some of those packets to know what they are.

Use tcpdump or wireshark (you really can not tell much from those logs, or at least the picture is cut off). Capturing packets will allow you to do the necessary analysis.

Also do a whois on that ip address.

My guess is you have some kind of a problem your your network, it does not look like a typical scan.

Google search how to tcpdump for information on how to sort this out.

---

