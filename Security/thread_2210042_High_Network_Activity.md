---
title: "High Network Activity"
date: 2014-03-08
forum: Security
---

### Post by CosmicFlux on 2014-03-08
Hi,

System Monitor is showing my system downloading between 700KiB and 1.3MiB constantly and I'm not downloading anything. I disconnected and then reconnected and within 5 minutes it was showing that 3.9GB had been recieved. 

Is this normal or should I be worried?


Flux

---

### Post by bashiergui on 2014-03-09
Entirely depends on what the traffic is. Use ```
netstat -napt
```to see what IP addresses you're communicating with and over what ports. If you're familiar with wireshark or tcpdump, capture the packets and see what's getting transmitted.

---

### Post by tgalati4 on 2014-03-09
Install *etherape* and see where the packets are coming from.  If it is from a country that you have no desire to visit, then you might install some IP blocking.

---

### Post by untrustytahr on 2014-03-09
Usually, when I see unexpected activity on my computer, i'ts downloading a podcast or torrent in the background that I've forgotten about.  Sometimes, I also mute my volume when streaming and forgot too.  The tools above work well in identifing connectons.  Another super-easy one is Nethogs.  It's a cli tool that will just give the user/application that's consuming bandwidth on an interface.

---

### Post by matt_symes on 2014-03-09
Hi

For another couple of suggestions, i use nethogs and iftop to check when i have high traffic.

```
sudo apt-get install nethogs
```

```
sudo apt-get install iftop
```

They may or may not be useful for you.

Kind regards

---

### Post by raja.genupula on 2014-03-11
Hi Matt

install nethogs as suggested by matt. Its very good tool , I have used it. It will display the data transmission from every connection your PC had. 

just launch it as

> sudo nethogs <your_device>

ex:
> 
sudo nethogs eth0

---

